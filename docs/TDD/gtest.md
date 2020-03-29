# 编译官方 GoogleTest

```git clone  git@github.com:google/googletest.git

cd  googletest

// 新建cmake 构建目录
mkdir mybuild  
// cmake 构建
cmake ../
//编译
make

```

# 测试示例

如果需要构建Google Test的示例，使用以下命令替换cmake …/
```
cmake -Dgtest_build_samples=ON ${GTEST_DIR}
```


# 嵌入式平台上(Amlogic A113x 平台)构建GoogleTest

基本思路: 使用arm交叉编译器编译GoogleTest, 生成可调用的动态库，应用层通过调用GoogleTest动态库完成测试用例的编写
指定arm交叉编译器

GoogleTest默认使用CMake构建，这里通过修改googletest/CMakeLists.txt,指定 Amlogic A113x 平台使用的编译器, 如下
```
set(CMAKE_SYSTEM_NAME Linux)
set(CMAKE_SYSTEM_PROCESSOR arm)
//根据实际情况，指定交叉编译的路径
set(tools /opt/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf)
//分别指定C和C++编译器
set(CMAKE_C_COMPILER ${tools}/bin/arm-linux-gnueabihf-gcc)
set(CMAKE_CXX_COMPILER ${tools}/bin/arm-linux-gnueabihf-g++)
```
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

# 编译成动态库

方便应用层编写测试用例，这里需要编译出动态库。 还是修改googletest/CMakeLists.txt

```
option(BUILD_SHARED_LIBS "Build shared libraries (DLLs)." OFF)
改为
option(BUILD_SHARED_LIBS "Build shared libraries (DLLs)." ON)

//同时也打开编译出示例程序选项
option(gtest_build_samples "Build gtest's sample programs." ON)
```


# 使用

[gtest和gmock入门](https://blog.csdn.net/gubenpeiyuan/article/details/50678697)


# 相关项目

## gtest-runner

A cross-platform, Qt5 based Graphical User Interface for Google Test unit tests

[github](https://github.com/nholthaus/gtest-runner)


# 参考资料

[玩转Google开源C++单元测试框架Google Test系列(gtest)(总)](https://www.cnblogs.com/coderzh/archive/2009/04/06/1426755.html)
[Google C++单元测试框架GoogleTest(总)](https://www.cnblogs.com/jycboy/p/gtest_catalog.html)
