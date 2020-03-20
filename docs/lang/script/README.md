# fake

[github](https://github.com/esrrhs/fake)

## 简介

fake是一款轻量级的嵌入式脚本语言, 使用c++语言编写, 语法吸取自lua、golang、erlang, 基于flex、bison生成语法树, 编译成字节码解释执行。

## 脚本特性

  * 运行环境linux amd64、MacOS amd64
  * 支持VM, JIT(实验性质)
  * 支持fake testfunc(param1)产生routine, 在单线程上实现多线程效果(此特性不支持JIT)
  * 支持调试, 自带gdb风格的命令行调试器, 以及VS风格的可视化编辑调试ide, 也可在C里直接通过接口调用, 开始命令行调试
  * 支持热更新
  * 支持C风格函数和C++类成员函数的绑定
  * 支持profile, 可获取脚本各个函数运行时间
  * 支持array, map, 可以无限嵌套
  * 支持多返回值
  * 支持Int64
  * 支持const定义
  * 支持包
  * 支持struct
  * 支持打包bin文件或可执行文件


# ChaiScript

Embedded Scripting Language Designed for C++ http://chaiscript.com

ChaiScript is one of the only embedded scripting language designed from the ground up to directly target C++ and take advantage of modern C++ development techniques, working with the developer how they would expect it to work. Being a native C++ application, it has some advantages over existing embedded scripting languages:

    It uses a header-only approach, which makes it easy to integrate with existing projects.
    It maintains type safety between your C++ application and the user scripts.
    It supports a variety of C++ techniques including callbacks, overloaded functions, class methods, and stl containers.


## 参考

 [github](https://github.com/ChaiScript/ChaiScript)

 [ChaiScript-基本要点](https://www.jianshu.com/p/1774ee3b031b)

 [ChaiScript—入门](https://www.jianshu.com/p/da7b7a488922)

 [ChaiScript 体验手册](http://www.cppblog.com/besterChen/archive/2009/08/03/92098.html)
