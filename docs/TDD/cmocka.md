# 介绍

CMocka 是一款支持 mock 对象、面向C语言的单元测试框架，CMocka 往往是编译成库的形式，供C单元测试程序链接调用。其前身是谷歌开发的 Cmockery，由于后者缺少维护，因此 CMocka 继承了 Cmockery 并继续维护。

CMocka 框架的特性：

    支持模拟对象，可设置模拟函数的期望返回值，期望输出参数，可检查模拟函数的输入参数、函数调用顺序。
    支持Test fixtures（包括setup和teardown）.
    不依赖第三方库，只需要一个C库即可.
    支持众多平台（Linux, BSD, Solaris, Windows和嵌入式平台）和编译器（GCC, LLVM, MSVC, MinGW等）.
    提供对异常信号(SIGSEGV, SIGILL, …)的处理。
    非fork()执行.
    提供基本的内存检测，包括内存泄露，内存溢出检测.
    提供丰富的断言宏.
    支持多种格式输出 (STDOUT, SUBUNIT, TAP, XML).
    开源.

# 编译安装

git clone git://git.cryptomilk.org/projects/cmocka.git

```
cd cmocka
mkdir build && cd build
cmake ..
make
make install
```

指定安装目录 

cmake -DCMAKE_INSTALL_PREFIX=/path/to/install




