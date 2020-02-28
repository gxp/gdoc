# start

包含头文件：
```
 #include <boost/dll.hpp>
```

链接： boost_filesystem and boost_system libraries.


## 加载库

boost::dll::shared_library lib("/test/boost/application/libtest_library.so");

## 导入符号

```
int plugin_constant = lib.get<const int>("integer_variable");
boost::function<int()> f = lib.get<int()>("function_returning_int");
int& i = lib.get_alias<int>("alias_to_int_variable");
```

注意：加载的符号只能在boost::dll::shared_library析构前使用。

Query libraries using boost::dll::library_info and get symbol infos using boost::dll::symbol_location, boost::dll::this_line_location and boost::dll::program_location.

### 导入单个函数或变量

```
using namespace boost;

// `extern "C"` - specifies C linkage: forces the compiler to export function/variable by a pretty (unmangled) C name.
#define API extern "C" BOOST_SYMBOL_EXPORT

//Import (code that uses DLL/DSL):
// Importing function.
auto cpp11_func = dll::import<int(std::string&&)>(
        path_to_shared_library, "i_am_a_cpp11_function"
    );

// Importing  variable.
shared_ptr<std::string> cpp_var = dll::import<std::string>(
        path_to_shared_library, "cpp_variable_name"
    );

// Importing function by alias name
auto cpp_func = dll::import_alias<std::string(const std::string&)>(
        path_to_shared_library, "pretty_name"
    );

//Export (DLL/DSL sources):
namespace some_namespace {
    API int i_am_a_cpp11_function(std::string&& param) noexcept;
//          ^--------------------  function name to use in dll::import<>
}

namespace your_project_namespace {
    API std::string cpp_variable_name;
}

namespace some_namespace {
    std::string i_am_function_with_ugly_name(const std::string& param) noexcept;
}

// When you have no control over function sources or wish to specify another name.
BOOST_DLL_ALIAS(some_namespace::i_am_function_with_ugly_name, pretty_name)

```

# Plugin

## basics

* 创建一个接口

```
#include <boost/config.hpp>
#include <string>

class BOOST_SYMBOL_VISIBLE my_plugin_api {
public:
   virtual std::string name() const = 0;
   virtual float calculate(float x, float y) = 0;

   virtual ~my_plugin_api() {}
};
```

* 实现接口

```
#include <boost/config.hpp> // for BOOST_SYMBOL_EXPORT
#include "../tutorial_common/my_plugin_api.hpp"

namespace my_namespace {

class my_plugin_sum : public my_plugin_api {
public:
    my_plugin_sum() {
        std::cout << "Constructing my_plugin_sum" << std::endl;
    }

    std::string name() const {
        return "sum";
    }

    float calculate(float x, float y) {
        return x + y;
    }

    ~my_plugin_sum() {
        std::cout << "Destructing my_plugin_sum ;o)" << std::endl;
    }
};

// Exporting `my_namespace::plugin` variable with alias name `plugin`
// (Has the same effect as `BOOST_DLL_ALIAS(my_namespace::plugin, plugin)`)
extern "C" BOOST_SYMBOL_EXPORT my_plugin_sum plugin;
my_plugin_sum plugin;

} // namespace my_namespace

```

* 使用插件

```
#include <boost/dll/import.hpp> // for import_alias
#include <iostream>
#include "../tutorial_common/my_plugin_api.hpp"

namespace dll = boost::dll;

int main(int argc, char* argv[]) {

    boost::dll::fs::path lib_path(argv[1]);             // argv[1] contains path to directory with our plugin library
    boost::shared_ptr<my_plugin_api> plugin;            // variable to hold a pointer to plugin variable
    std::cout << "Loading the plugin" << std::endl;

    plugin = dll::import<my_plugin_api>(          // type of imported symbol is located between `<` and `>`
        lib_path / "my_plugin_sum",                     // path to the library and library name
        "plugin",                                       // name of the symbol to import
        dll::load_mode::append_decorations              // makes `libmy_plugin_sum.so` or `my_plugin_sum.dll` from `my_plugin_sum`
    );

    std::cout << "plugin->calculate(1.5, 1.5) call:  " << plugin->calculate(1.5, 1.5) << std::endl;
}
```

* 输出结果

```
Loading the plugin
Constructing my_plugin_sum
plugin->calculate(1.5, 1.5) call:  3
Destructing my_plugin_sum ;o)
```

## 插件工厂

```
#include <boost/dll/alias.hpp> // for BOOST_DLL_ALIAS
#include "../tutorial_common/my_plugin_api.hpp"

namespace my_namespace {

class my_plugin_aggregator : public my_plugin_api {
    float aggr_;
    my_plugin_aggregator() : aggr_(0) {}

public:
    std::string name() const {
        return "aggregator";
    }

    float calculate(float x, float y) {
        aggr_ += x + y;
        return aggr_;
    }

    // Factory method
    static boost::shared_ptr<my_plugin_aggregator> create() {
        return boost::shared_ptr<my_plugin_aggregator>(
            new my_plugin_aggregator()
        );
    }
};


BOOST_DLL_ALIAS(
    my_namespace::my_plugin_aggregator::create, // <-- this function is exported with...
    create_plugin                               // <-- ...this alias name
)

} // namespace my_namespace
```

```
#include <boost/dll/import.hpp> // for import_alias
#include <boost/function.hpp>
#include <iostream>
#include "../tutorial_common/my_plugin_api.hpp"

namespace dll = boost::dll;

int main(int argc, char* argv[]) {

    boost::dll::fs::path shared_library_path(argv[1]);                  // argv[1] contains path to directory with our plugin library
    shared_library_path /= "my_plugin_aggregator";
    typedef boost::shared_ptr<my_plugin_api> (pluginapi_create_t)();
    boost::function<pluginapi_create_t> creator;

    creator = boost::dll::import_alias<pluginapi_create_t>(             // type of imported symbol must be explicitly specified
        shared_library_path,                                            // path to library
        "create_plugin",                                                // symbol to import
        dll::load_mode::append_decorations                              // do append extensions and prefixes
    );

    boost::shared_ptr<my_plugin_api> plugin = creator();
    std::cout << "plugin->calculate(1.5, 1.5) call:  " << plugin->calculate(1.5, 1.5) << std::endl;
    std::cout << "plugin->calculate(1.5, 1.5) second call:  " << plugin->calculate(1.5, 1.5) << std::endl;
    std::cout << "Plugin Name:  " << plugin->name() << std::endl;
}
```

## 在多个插件中搜索符号

```
#include <boost/dll/import.hpp> // for import_alias
#include <boost/make_shared.hpp>
#include <boost/function.hpp>
#include <iostream>
#include "../tutorial_common/my_plugin_api.hpp"

namespace dll = boost::dll;

std::size_t search_for_symbols(const std::vector<boost::dll::fs::path>& plugins) {
    std::size_t plugins_found = 0;

    for (std::size_t i = 0; i < plugins.size(); ++i) {
        std::cout << "Loading plugin: " << plugins[i] << '\n';
        dll::shared_library lib(plugins[i], dll::load_mode::append_decorations);
        if (!lib.has("create_plugin")) {
            // no such symbol
            continue;
        }

        // library has symbol, importing...
        typedef boost::shared_ptr<my_plugin_api> (pluginapi_create_t)();
        boost::function<pluginapi_create_t> creator
            = dll::import_alias<pluginapi_create_t>(boost::move(lib), "create_plugin");

        std::cout << "Matching plugin name: " << creator()->name() << std::endl;
        ++ plugins_found;
    }

    return plugins_found;
}

```

结果输出：

```
Loading plugin: "/test/libmy_plugin_aggregator.so"
Matching plugin name: aggregator
Loading plugin: "/test/libmy_plugin_sum.so"
Constructing my_plugin_sum
Destructing my_plugin_sum ;o)
```

## 静态链接插件到可执行程序

static_plugin.hpp

```
#include <boost/dll/alias.hpp>                          // for BOOST_DLL_ALIAS
#include <boost/shared_ptr.hpp>
#include "../tutorial_common/my_plugin_api.hpp"

namespace my_namespace {
    boost::shared_ptr<my_plugin_api> create_plugin();   // Forward declaration
} // namespace my_namespace

BOOST_DLL_ALIAS(
    my_namespace::create_plugin,                        // <-- this function is exported with...
    create_plugin                                       // <-- ...this alias name
)
```

static_plugin.cpp

```
#include "static_plugin.hpp" // this is essential, BOOST_SYMBOL_ALIAS must be seen in this file

#include <boost/make_shared.hpp>
#include <iostream>

namespace my_namespace {

class my_plugin_static : public my_plugin_api {
public:
    my_plugin_static() {
        std::cout << "Constructing my_plugin_static" << std::endl;
    }

    std::string name() const {
        return "static";
    }

    float calculate(float x, float y) {
        return x - y;
    }

    ~my_plugin_static() {
        std::cout << "Destructing my_plugin_static" << std::endl;
    }
};

boost::shared_ptr<my_plugin_api> create_plugin() {
    return boost::make_shared<my_plugin_static>();
}

} // namespace my_namespace
```

main.cpp

```
#include <boost/dll/shared_library.hpp>         // for shared_library
#include <boost/dll/runtime_symbol_info.hpp>    // for program_location()
#include "static_plugin.hpp"                    // without this headers some compilers may optimize out the `create_plugin` symbol
#include <boost/function.hpp>
#include <iostream>

namespace dll = boost::dll;

int main() {
    dll::shared_library self(dll::program_location());

    std::cout << "Call function" << std::endl;
    boost::function<boost::shared_ptr<my_plugin_api>()> creator
        = self.get_alias<boost::shared_ptr<my_plugin_api>()>("create_plugin");

    std::cout << "Computed Value: " << creator()->calculate(2, 2) << std::endl;
}
```

## 在Linux中符号被遮盖问题

## 插件卸载回调

## 查询库中的符号

## 参考记数

As noted in documentation to the boost::dll::import variables and functions returned from those functions hold a reference to the shared library. However nested objects and objects that are returned by import* functions do not hold a reference to the shared library. There's no way to solve this issue on the Boost.DLL library level, but you can take care of this problem by your own. Here's an example how this could be done.


```
#include <boost/shared_ptr.hpp>
#include <boost/make_shared.hpp>
#include <boost/dll/shared_library.hpp>

struct library_holding_deleter {
    boost::shared_ptr<boost::dll::shared_library> lib_;

    void operator()(my_refcounting_api* p) const {
        delete p;
    }
};

inline boost::shared_ptr<my_refcounting_api> bind(my_refcounting_api* plugin) {
    // getting location of the shared library that holds the plugin
    boost::dll::fs::path location = plugin->location();

    // `make_shared` is an efficient way to create a shared pointer
    boost::shared_ptr<boost::dll::shared_library> lib
        = boost::make_shared<boost::dll::shared_library>(location);

    library_holding_deleter deleter;
    deleter.lib_ = lib;

    return boost::shared_ptr<my_refcounting_api>(
        plugin, deleter
    );
}
```


## 从windows dll中导入c函数

```
#include <boost/dll/import.hpp>         // for dll::import
#include <boost/dll/shared_library.hpp> // for dll::shared_library
#include <boost/function.hpp>
#include <iostream>
#include <windows.h>

namespace dll = boost::dll;

int main() {
    typedef HANDLE(__stdcall GetStdHandle_t)(DWORD );       // function signature with calling convention

    // OPTION #0, requires C++11 compatible compiler that understands GetStdHandle_t signature.

    auto get_std_handle = dll::import<GetStdHandle_t>(
        "Kernel32.dll",
        "GetStdHandle",
        boost::dll::load_mode::search_system_folders
    );
    std::cout << "0.0 GetStdHandle() returned " << get_std_handle(STD_OUTPUT_HANDLE) << std::endl;

    // You may put the `get_std_handle` into boost::function<>. But boost::function<Signature> can not compile with
    // Signature template parameter that contains calling conventions, so you'll have to remove the calling convention.
    boost::function<HANDLE(DWORD)> get_std_handle2 = get_std_handle;
    std::cout << "0.1 GetStdHandle() returned " << get_std_handle2(STD_OUTPUT_HANDLE) << std::endl;


    // OPTION #1, does not require C++11. But without C++11 dll::import<> can not handle calling conventions,
    // so you'll need to hand write the import.
    dll::shared_library lib("Kernel32.dll", dll::load_mode::search_system_folders);
    GetStdHandle_t& func = lib.get<GetStdHandle_t>("GetStdHandle");

    // Here `func` does not keep a reference to `lib`, you'll have to deal with that on your own.
    std::cout << "1.0 GetStdHandle() returned " << func(STD_OUTPUT_HANDLE) << std::endl;

    return 0;
}
```


# 参考

https://www.boost.org/doc/libs/1_72_0/doc/html/boost_dll/tutorial.html
