# CMake Tutorial

## CMakeLists.txt

```
cmake_minimum_required (VERSION 2.6)
project (Tutorial)
add_executable(Tutorial tutorial.cxx)
```

## 为程序增加版本号

在工程和可执行程序上加一个版本号。虽然你可以直接在源代码里面这么做，然而如果用CMakeLists文件来做的话会提供更多的灵活性。为了增加版本号，我们可以如此更改CMakeLists文件：

```
cmake_minimum_required (VERSION 2.6)
project (Tutorial)
# The version number.
set (Tutorial_VERSION_MAJOR 1)
set (Tutorial_VERSION_MINOR 0)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")

# add the executable
add_executable(Tutorial tutorial.cxx)

```

由于配置文件必须写到binary tree中，因此我们必须将这个目录添加到头文件搜索目录中。我们接下来在源码目录中创建了TutorialConfig.h.in文件，其内容如下：

接下来在源码目录中创建了TutorialConfig.h.in文件，其内容如下：

```
// the configured options and settings for Tutorial
#define Tutorial_VERSION_MAJOR @Tutorial_VERSION_MAJOR@
#define Tutorial_VERSION_MINOR @Tutorial_VERSION_MINOR@
```

当CMake配置了这个头文件， @Tutorial_VERSION_MAJOR@ 和 @Tutorial_VERSION_MINOR@ 的值将会被改变。接下来，我们修改了tutorial.cxx来包含配置的头文件并且使用版本号。最终的源代码如下所示：
```
// A simple program that computes the square root of a number
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "TutorialConfig.h"

int main (int argc, char *argv[])
{
  if (argc < 2)
    {
    fprintf(stdout,"%s Version %d.%d\n",
            argv[0],
            Tutorial_VERSION_MAJOR,
            Tutorial_VERSION_MINOR);
    fprintf(stdout,"Usage: %s number\n",argv[0]);
    return 1;
    }
  double inputValue = atof(argv[1]);
  double outputValue = sqrt(inputValue);
  fprintf(stdout,"The square root of %g is %g\n",
          inputValue, outputValue);
  return 0;
}
```
最主要的变更是包含了TutorialConfig.h头文件，并输出了版本号。

## Adding a Library (Step 2)

现在我们给工程添加一个库。这个库会包含我们自己的平方根实现。如此，应用程序就可以使用这个库而非编译器提供的库了。在这个教程中，我们将库放入一个叫MathFunctions的子文件夹中。它会使用如下的一行CMakeLists文件：

```
add_library(MathFunctions mysqrt.cxx)
```

原文件mysqrt.cxx有一个叫做mysqrt的函数可以提供与编译器的sqrt相似的功能。为了使用新的库，我们需要在顶层的CMakeLists 文件中添加add_subdirectory的调用。我们也要添加一个另外的头文件搜索目录，使得MathFunctions/mysqrt.h可以被搜索到。最后的改变就是将新的库加到可执行程序中。顶层的CMakeLists 文件现在看起来是这样：

```
include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
add_subdirectory (MathFunctions)

# add the executable
add_executable (Tutorial tutorial.cxx)
target_link_libraries (Tutorial MathFunctions)
```

### 库可选

现在我们来考虑如何使得MathFunctions库成为可选的。虽然在这个教程当中没有什么理由这么做，然而如果使用更大的库或者当依赖于第三方的库时，你或许希望这么做。第一步是要在顶层的CMakeLists文件中加上一个选择项。

```
## should we use our own math functions?
option (USE_MYMATH
        "Use tutorial provided math implementation" ON)
```

这个选项会显示在CMake的GUI，并且其默认值为ON。当用户选择了之后，这个值会被保存在CACHE中，这样就不需要每次CMAKE都进行更改了。下面一步条件构建和链接MathFunctions库。为了达到这个目的，我们可以改变顶层的CMakeLists文件，使得其看起来像这样：

```
# add the MathFunctions library?

if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
  add_subdirectory (MathFunctions)
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)

# add the executable
add_executable (Tutorial tutorial.cxx)
target_link_libraries (Tutorial  ${EXTRA_LIBS})
```

这里使用了USE_MYMATH来决定MathFunctions是否会被编译和使用。注意这里变量EXTRA_LIBS的使用方法。这是保持一个大的项目看起来比较简洁的一个方法。源代码中相应的变化就比较简单了：
```
// A simple program that computes the square root of a number
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "TutorialConfig.h"
#ifdef USE_MYMATH
#include "MathFunctions.h"
#endif

int main (int argc, char *argv[])
{
  if (argc < 2)
    {
    fprintf(stdout,"%s Version %d.%d\n", argv[0],
            Tutorial_VERSION_MAJOR,
            Tutorial_VERSION_MINOR);
    fprintf(stdout,"Usage: %s number\n",argv[0]);
    return 1;
    }

  double inputValue = atof(argv[1]);

#ifdef USE_MYMATH
  double outputValue = mysqrt(inputValue);
#else
  double outputValue = sqrt(inputValue);
#endif

  fprintf(stdout,"The square root of %g is %g\n",
          inputValue, outputValue);
  return 0;
}
```

在源代码中我们同样使用了USE_MYMATH这个宏。它由CMAKE通过配置文件TutorialConfig.h.in来提供给源代码。

```
#cmakedefine USE_MYMATH

```

## Installing and Testing (Step 3)


接下来我们会为我们的工程增加安装规则和测试支持。安装规则是非常非常简单的。对于MathFunctions库我们安装库和头文件只需要添加如下的语句：

```
install (TARGETS MathFunctions DESTINATION bin)
install (FILES MathFunctions.h DESTINATION include)
```

对于应用程序，我们只需要在顶层CMakeLists 文件中如此配置即可以安装可执行程序和配置了的头文件：
```
# add the install targets
install (TARGETS Tutorial DESTINATION bin)
install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"        
         DESTINATION include)
```
这就是所有需要做的。现在你就可以编译这个教程了，然后输入make install（或者编译IDE中的INSTALL目标），则头文件、库和可执行程序等就会被正确地安装。CMake变量CMAKE_INSTALL_PREFIX被用来决定那些文件会被安装在哪个根目录下。添加测试也是一个相当简单的过程。在最顶层的CMakeLists文件的最后我们可以添加一系列的基础测试来确认这个程序是否在正确工作。
```
# does the application run
add_test (TutorialRuns Tutorial 25)

# does it sqrt of 25
add_test (TutorialComp25 Tutorial 25)

set_tests_properties (TutorialComp25
  PROPERTIES PASS_REGULAR_EXPRESSION "25 is 5")

# does it handle negative numbers
add_test (TutorialNegative Tutorial -25)
set_tests_properties (TutorialNegative
  PROPERTIES PASS_REGULAR_EXPRESSION "-25 is 0")

# does it handle small numbers
add_test (TutorialSmall Tutorial 0.0001)
set_tests_properties (TutorialSmall
  PROPERTIES PASS_REGULAR_EXPRESSION "0.0001 is 0.01")

# does the usage message work?
add_test (TutorialUsage Tutorial)
set_tests_properties (TutorialUsage
  PROPERTIES
  PASS_REGULAR_EXPRESSION "Usage:.*number")
```

第一个测试简单地确认应用是否运行，没有段错误或者其它的崩溃问题，并且返回0。这是CTest的最基本的形式。下面的测试都使用了PASS_REGULAR_EXPRESSION测试属性来确认输出的结果中是否含有某个字符串。如果你需要添加大量的测试来判断不同的输入值，则你需要考虑创建一个类似于下面的宏：

```
#define a macro to simplify adding tests, then use it
macro (do_test arg result)
  add_test (TutorialComp${arg} Tutorial ${arg})
  set_tests_properties (TutorialComp${arg}
    PROPERTIES PASS_REGULAR_EXPRESSION ${result})
endmacro (do_test)

# do a bunch of result based tests
do_test (25 "25 is 5")
do_test (-25 "-25 is 0")
```

对do_test的任意一次调用，就有另一个测试被添加到工程中。

## Adding System Introspection (Step 4)

接下来，我们来考虑添加一些有些目标平台可能不支持的代码。在这个样例中，我们将根据目标平台是否有log和exp函数来添加我们的代码。当然大多数平台都是有这些函数的，只是本教程假设这两个函数没有被那么普遍地支持。如果平台有log，那么在mysqrt中，就用它来计算平方根。我们首先使用CheckFunctionExists.cmake来测试这些函数的是否存在，在顶层的CMakeLists文件中：

```
# does this system provide the log and exp functions?
include (CheckFunctionExists.cmake)
check_function_exists (log HAVE_LOG)
check_function_exists (exp HAVE_EXP)
```
接下来我们修改TutorialConfig.h.in来定义CMake是否找到这些函数的宏
```
// does the platform provide exp and log functions?
#cmakedefine HAVE_LOG
#cmakedefine HAVE_EXP
```
重要的一点是，对tests和log的测试必须要在配置文件命令前完成。配置文件命令会使用CMake中的配置立马配置文件。最后在mysqrt函数中我们提供了两种实现方式：
```
// if we have both log and exp then use them
#if defined (HAVE_LOG) && defined (HAVE_EXP)
  result = exp(log(x)*0.5);
#else // otherwise use an iterative approach
  . . .
```

## Adding a Generated File and Generator (Step 5)

在这一节当中，我们会告诉你如何将一个生成的源文件加入到应用程序的构建过程中。在此例中，我们会创建一个预先计算好的平方根的表，并将这个表编译到应用程序中去。为了达到这个目的，我们首先需要一个程序来生成这样的表。在MathFunctions这个子目录下一个新的叫做MakeTable.cxx的源文件就是用来干这个的。
```
// A simple program that builds a sqrt table
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main (int argc, char *argv[])
{
  int i;
  double result;

  // make sure we have enough arguments
  if (argc < 2)
    {
    return 1;
    }

  // open the output file
  FILE *fout = fopen(argv[1],"w");
  if (!fout)
    {
    return 1;
    }

  // create a source file with a table of square roots
  fprintf(fout,"double sqrtTable[] = {\n");
  for (i = 0; i < 10; ++i)
    {
    result = sqrt(static_cast<double>(i));
    fprintf(fout,"%g,\n",result);
    }

  // close the table with a zero
  fprintf(fout,"0};\n");
  fclose(fout);
  return 0;
}
```
注意到这张表是由一个有效的C++代码产生的，并且输出文件的名字是由参数代入的。下一步就是添加合适的命令到MathFunctions的CMakeLists文件中来构建MakeTable这个可执行程序，并且作为构建过程中的一部分。完成它需要一些命令，如下：
```
# first we add the executable that generates the table
add_executable(MakeTable MakeTable.cxx)

# add the command to generate the source code
add_custom_command (
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/Table.h
  COMMAND MakeTable ${CMAKE_CURRENT_BINARY_DIR}/Table.h
  DEPENDS MakeTable
  )

# add the binary tree directory to the search path for
# include files
include_directories( ${CMAKE_CURRENT_BINARY_DIR} )

# add the main library
add_library(MathFunctions mysqrt.cxx ${CMAKE_CURRENT_BINARY_DIR}/Table.h  )
```
首先，就像其它可执行程序一样，MakeTable被添加为可执行程序。然后我们添加了一个自定义命令来详细描述如何通过运行MakeTable来产生Table.h。接下来，我们需要让CMake知道mysqrt.cxx依赖于生成的文件Table.h。这是通过往MathFunctions这个库里面添加生成的Table.h来实现的。我们也需要添加当前的生成目录到搜索路径中，从而Table.h可以被mysqrt.cxx找到。

当这个工程被构建时，它首先会构建MakeTable这个可执行程序。然后运行MakeTable从而生成Table.h。最后，它会编译mysqrt.cxx来生成MathFunctions library。

在这一刻，我们添加了所有的特征到最顶层的CMakeLists文件，它现在看起来是这样的：
```
cmake_minimum_required (VERSION 2.6)
project (Tutorial)

# The version number.
set (Tutorial_VERSION_MAJOR 1)
set (Tutorial_VERSION_MINOR 0)

# does this system provide the log and exp functions?
include (${CMAKE_ROOT}/Modules/CheckFunctionExists.cmake)

check_function_exists (log HAVE_LOG)
check_function_exists (exp HAVE_EXP)

# should we use our own math functions
option(USE_MYMATH
  "Use tutorial provided math implementation" ON)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file (
  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
  )

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories ("${PROJECT_BINARY_DIR}")

# add the MathFunctions library?
if (USE_MYMATH)
  include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
  add_subdirectory (MathFunctions)
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
endif (USE_MYMATH)

# add the executable
add_executable (Tutorial tutorial.cxx)
target_link_libraries (Tutorial  ${EXTRA_LIBS})

# add the install targets
install (TARGETS Tutorial DESTINATION bin)
install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"        
         DESTINATION include)

# does the application run
add_test (TutorialRuns Tutorial 25)

# does the usage message work?
add_test (TutorialUsage Tutorial)
set_tests_properties (TutorialUsage
  PROPERTIES
  PASS_REGULAR_EXPRESSION "Usage:.*number"
  )


#define a macro to simplify adding tests
macro (do_test arg result)
  add_test (TutorialComp${arg} Tutorial ${arg})
  set_tests_properties (TutorialComp${arg}
    PROPERTIES PASS_REGULAR_EXPRESSION ${result}
    )
endmacro (do_test)

# do a bunch of result based tests
do_test (4 "4 is 2")
do_test (9 "9 is 3")
do_test (5 "5 is 2.236")
do_test (7 "7 is 2.645")
do_test (25 "25 is 5")
do_test (-25 "-25 is 0")
do_test (0.0001 "0.0001 is 0.01")
```
TutorialConfig.h是这样的：

```
// the configured options and settings for Tutorial
#define Tutorial_VERSION_MAJOR @Tutorial_VERSION_MAJOR@
#define Tutorial_VERSION_MINOR @Tutorial_VERSION_MINOR@
#cmakedefine USE_MYMATH

// does the platform provide exp and log functions?
#cmakedefine HAVE_LOG
#cmakedefine HAVE_EXP
```

最后MathFunctions的CMakeLists文件看起来是这样的：

```
# first we add the executable that generates the table
add_executable(MakeTable MakeTable.cxx)
# add the command to generate the source code
add_custom_command (
  OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/Table.h
  DEPENDS MakeTable
  COMMAND MakeTable ${CMAKE_CURRENT_BINARY_DIR}/Table.h
  )
# add the binary tree directory to the search path
# for include files
include_directories( ${CMAKE_CURRENT_BINARY_DIR} )

# add the main library
add_library(MathFunctions mysqrt.cxx ${CMAKE_CURRENT_BINARY_DIR}/Table.h)

install (TARGETS MathFunctions DESTINATION bin)
install (FILES MathFunctions.h DESTINATION include)
```

## Building an Installer (Step 6)

最后假设我们想要把我们的工程发布给别人从而让他们去使用。我们想要同时给他们不同平台的二进制文件和源代码。这与步骤3中的install略有不同，install是安装我们从源代码中构建的二进制文件。而在此例中，我们将要构建安装包来支持二进制安装以及cygwin，debian，RPMs等的包管理特性。为了达到这个目的，我们会使用CPack来创建平台相关的安装包。具体地说，我们需要在顶层CMakeLists.txt文件中的底部添加数行。

```
# build a CPack driven installer package
include (InstallRequiredSystemLibraries)
set (CPACK_RESOURCE_FILE_LICENSE  
     "${CMAKE_CURRENT_SOURCE_DIR}/License.txt")
set (CPACK_PACKAGE_VERSION_MAJOR "${Tutorial_VERSION_MAJOR}")
set (CPACK_PACKAGE_VERSION_MINOR "${Tutorial_VERSION_MINOR}")
set (CPACK_PACKAGE_VERSION_PATCH "${Tutorial_VERSION_PATCH}")
include (CPack)
```
这就是所有要做的。我们首先包含了InstallRequiredSystemLibraries。这个模块将会包含当前平台所需要的所有运行时库。接下来，我们设置了一些CPack的变量来保存license以及工程的版本信息。版本信息利用了我们在早前的教程中使用到的变量。最后我们包含了CPack这个模块来使用这些变量和你所使用的系统的其它特性来设置安装包。

接下来一步是用通常的方式构建工程，然后在CPack上运行它。如果要构建一个二进制包你需要运行：
```
cpack --config CPackConfig.cmake
```

如果要创建一个关代码包你需要输入
```
cpack --config CPackSourceConfig.cmake
```

## Adding Support for a Dashboard (Step 7)

将测试结果上传到dashboard上是非常简单的。我们在早前的步骤中已经定义了一些测试。我们仅需要运行这些例程然后提交到dashboard上。为了包含对dashboards的支持，我们需要在顶层的CMakeLists文件中包含CTest模块。
# enable dashboard scripting
include (CTest)

我们也创建了一个CTestConfig.cmake文件来指定这个工程在dashobard上的的名字。
set (CTEST_PROJECT_NAME "Tutorial")

CTest会读这个文件并且运行它。如果要创建一个简单的dashboard，你可以在你的工程上运行CMake，改变生成路径的目录，然后运行ctest -D Experimental。你的dashboard的结果会被上传到Kitware的公共dashboard中。

最后，可以在[这里](https://link.jianshu.com/?t=http://oawflafkv.bkt.clouddn.com/xz/code/Tutorial.rar)下载到整个教程的源代码。

[原文](https://www.jianshu.com/p/bbf68f9ddffa)


# 如何设置Debug和Release编译模式

一般Debug和Release必须在不同的目录下编译，否则每次当切换模式时必须把编译文件全部删掉。

这里假设新建两个目录Debug和Release来分别用于构建相应的模式：

```
   mkdir Release  
   cd Release  
   cmake -DCMAKE_BUILD_TYPE=Release ..  
   make  

```

```
   mkdir Debug  
   cd Debug  
   cmake -DCMAKE_BUILD_TYPE=Debug ..  
   make  
```

windows下的注意事项

如果是windows下，想使用CMAKE_BUILD_TYPE参数，cmake时必须用-G"NMake Makefiles"，而不能用-G"Visual Studio 14"（这里假设vs2015为例。如果你使用了-G"Visual Studio 14"且要指定release/debug，我觉得应该在msbuild命令参数中设置，具体如何设置还没去研究），否则会提示无法识别CMAKE_BUILD_TYPE。

用法示例：

```
   cmake -G"NMake Makefiles" -DCMAKE_BUILD_TYPE=Release path\to\source\dir  
   nmake  
```

注意：如果不使用CMAKE_BUILD_TYPE参数，则默认是Debug

注意：windowns下，需在Developer Command Prompt for ...下执行，否则找不到nake cl 等


其他参考：

http://stackoverflow.com/questions/7724569/debug-vs-release-in-cmake

# cross-compile

* Create in the root of GoogleTest folder  toolchain-arm-linux-gnueabihf.cmake file with the following content:

```
# Target system
SET(CMAKE_SYSTEM_NAME Linux)
SET(CMAKE_SYSTEM_VERSION 1)

set(CMAKE_FIND_ROOT_PATH /usr/arm-linux-gnueabihf)

# Cross compiler
SET(CMAKE_C_COMPILER   /usr/bin/arm-linux-gnueabihf-gcc)
SET(CMAKE_CXX_COMPILER /usr/bin/arm-linux-gnueabihf-g++)

# Search for programs in the build host directories
SET(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)

# Libraries and headers in the target directories
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_PACKAGE ONLY)
```

* Configure CMake
```
cmake -DCMAKE_TOOLCHAIN_FILE=./toolchain-arm-linux-gnueabihf.cmake
```


# 查看所有配置选项

```
cmake . -LH


# uninstall

cmake不提供uninstall支持，但可从文件install_manifest.txt中查看安装了哪些文件，可使用如下命令删除安装：
```
cat ./install_manifest.txt | xargs sudo rm
```


# x64

How to build x86 and/or x64 on Windows from command line with CMAKE?

This cannot be done with CMake. You have to generate two separate build folders. One for the x86 NMake build and one for the x64 NMake build. You cannot generate a single Visual Studio project covering both architectures with CMake, either.

To build Visual Studio projects from the command line for both 32-bit and 64-bit without starting a Visual Studio command prompt, use the regular Visual Studio generators.

For CMake 3.13 or newer, run the following commands:

cmake -G "Visual Studio 16 2019" -A Win32 -S \path_to_source\ -B "build32"
cmake -G "Visual Studio 16 2019" -A x64 -S \path_to_source\ -B "build64"
cmake --build build32 --config Release
cmake --build build64 --config Release

For earlier versions of CMake, run the following commands:

mkdir build32 & pushd build32
cmake -G "Visual Studio 15 2017" \path_to_source\
popd
mkdir build64 & pushd build64
cmake -G "Visual Studio 15 2017 Win64" \path_to_source\
popd
cmake --build build32 --config Release
cmake --build build64 --config Release

CMake generated projects that use one of the Visual Studio generators can be built from the command line with using the option --build followed by the build directory. The --config options specifies the build configuration.
