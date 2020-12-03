
# 代码生成

## sfml-vscode-boilerplate

A cross-platform SFML 2.5.1 & C++17 build environment for Visual Studio Code

https://github.com/andrew-r-king/sfml-vscode-boilerplate

## autoprogrammer

https://github.com/flexferrum/autoprogrammer

## transformer 

Tool for parsing C/C++ code and generating output using a given Jinja-like template 

Tool for parsing C/C++ code and generating output using a given Jinja-like template. This might be useful for creating reflection/RTTI frameworks for C/C++ (or you can just wait until 2023 or 2026 year and use standard implementation... or use Java)

Currently supported features:

    struct/class fields parsing
    enum parsing
    generation output using Jinja-like template
    C++ custom attributes support

[src](https://github.com/mtiapko/transformer)

# cppast

Library to parse and work with the C++ AST 

Library interface to the C++ AST — parse source files, synthesize entities, get documentation comments and generate code.

[src](https://github.com/foonathan/cppast)

# CppAst.NET

CppAst is a .NET library providing a C/C++ parser for header files powered by Clang/libclang with access to the full AST, comments and macros 

[src](https://github.com/xoofx/CppAst.NET)


# 反射

对于C++来说倾向于使用推倒的形式获取类型信息，而不是从编译信息中直接获取信息。并且在编译时为字段添加信息的功能也完全没有，这就是需要我们自己进行扩展的内容了。我们需要：

    在编译时进行字段/方法的遍历，这个遍历需要支持用户提供的filter；为字段/类提供静态的附加元信息，并且支持constexpr的getter，matching等操作

乍眼一看非常苛刻，但是完成这两条后静态反射会被完全补全，并且完全嵌入C++这个语言中。你可以在你想要的任何地方使用功能完全的静态反射，遍历域，获取meta信息，等等等等，并且这些操作都是constexpr的。

## 参考

[SakuraEngine中的反射:写一个C++反射工具(一)](https://zhuanlan.zhihu.com/p/125127118)

[C++ Reflection Library ](https://github.com/rttrorg/rttr)

[reflect反射机制](https://blog.csdn.net/wzjking0929/article/details/83239456)

[C++语言改造: 完全静态的反射机制](https://zhuanlan.zhihu.com/p/136561745)

[现代 C++ 编译时 结构体字段反射](https://zhuanlan.zhihu.com/p/88144082)

[Header-only, tiny (99 lines) and powerful C++17 static reflection library. ](https://github.com/Ubpa/USRefl)

[c++反射----现有解决方案](https://zhuanlan.zhihu.com/p/99017367)

["全球最强" | 99 行 C++ 静态反射库](https://zhuanlan.zhihu.com/p/158147380)

[Header-only, non-intrusive and macro-free runtime reflection system in C++](https://github.com/skypjack/meta)

## SakuraEngine

跨平台的现代游戏引擎

    跨平台: Win32, Linux, Android(待定)以及IOS(待定)的跨平台基础支持;
    模块/插件化: 基于依赖图的模块管理器SPA, 支持静态/动态导出的插件/模块;

静态&动态反射: RuntimeHeader

上面读完就可以知道, 对于静态反射来说, 更大的意义是收集元信息, 以及遍历各个域。

对于动态反射来说, 则可以按名字去实例化一个类, 或者在运行时向目标添加一些额外的元信息, 这些操作都需要引入全局性的状态, 所以我们说它们属于动态反射的范畴。

大部分情况下, 静态反射已经足够用了, 这种情况下由于没有引入任何运行时状态, 依赖可以只有一个头。有了静态反射, 就可以基于静态反射实现动态反射, 当然也需要多引入一个dll来维护各种动态的元信息。


[Cross-Platform Game Engine ](https://github.com/SaeruHikari/SakuraEngine)

[文档](https://saeruhikari.github.io/SakuraEngine/#/)

## SakuraAutoCoder

Code generator of SakuraEngine, aiming to light-weight code generator for reflection and exporter for P-Invokes/Lua/etc. 

静态&动态反射: RuntimeHeader

上面读完就可以知道, 对于静态反射来说, 更大的意义是收集元信息, 以及遍历各个域。

对于动态反射来说, 则可以按名字去实例化一个类, 或者在运行时向目标添加一些额外的元信息, 这些操作都需要引入全局性的状态, 所以我们说它们属于动态反射的范畴。

大部分情况下, 静态反射已经足够用了, 这种情况下由于没有引入任何运行时状态, 依赖可以只有一个头。有了静态反射, 就可以基于静态反射实现动态反射, 当然也需要多引入一个dll来维护各种动态的元信息。

[src](https://github.com/SaeruHikari/SakuraAutoCoder)

[SakuraEngine中的反射:写一个C++反射工具(一)](https://zhuanlan.zhihu.com/p/125127118)


## refl-cpp

A modern compile-time reflection library for C++ with support for overloads, templates, attributes and proxies 

refl-cpp allows static reflection and inspection of types in C++17! On top of that, refl-cpp is extensible (build your own abstraction or runtime reflection system) and supports all of the following and more:

    overloaded and template functions - invoke and get pointers to overloaded functions without specifying type arguments in metadata
    template types - reflect and work with template classes like regular classes
    constexpr attributes- attach custom objects to reflectable members and types (create your own markers, names for external bindings or arbitrary data)
    proxy types - programmatic type generation (implement unknown interface, create a generic builder, value type wrapper, etc.)


[src](https://github.com/veselink1/refl-cpp)