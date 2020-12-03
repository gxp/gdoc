# 编译

## 环境

[gcc如何指定编译头文件的位置](https://www.jianshu.com/p/7d0f9d987dc9)

## 加速编译

hot reload

差分编译 分段编译 只编译修改的代码行

把一个.cpp文件，通过工具分成多个文件,每个文件类似如下:

```
#include "all.h"

void f();  //函数前置申明

代码块

```
这样可以把一个文件按“代码块”分成多个代码块文件，第次有代码块变动时，编译相应代码块文件。 



May be you're looking for this :

ld -r src1.o src2.o src3.o -o final.o

But its always nice to have them archived, using

ar rvs libmy.a file1.o file2.o file3.o

Then use -lmy to link.

相关技术：

1. 通过管道输入文件

cat m.cpp | gcc -x c++ -c -o m.o -

通过管道生成的文件，调试信息中找不到文件名，这对源码调试有影响。

是不是可以通过临时文件编译，生成文件后，再修改 .o 或.obj文件，修正文件名信息.

2. 使用内存文件系统

```
mount -osize=10M tmpfs /home/chill/tmp/supersikrit -t tmpfs

```

### 参考 

[C++ 预编译头文件](https://www.cnblogs.com/nzbbody/p/3437868.html)

[GCC中使用预编译头文件](https://blog.csdn.net/wind19/article/details/6332908)

[ 加快C++代码的编译速度方法](https://www.cnblogs.com/myd620/p/11792013.html)

[gcc Using Precompiled Headers](https://apimirror.com/gcc~9/precompiled-headers)

[Compile multiple C source fles into a unique object file](https://stackoverflow.com/questions/18182176/compile-multiple-c-source-fles-into-a-unique-object-file)

[Chromium GN构建工具的使用 gn增量构建最快](https://www.cnblogs.com/bigben0123/p/12626012.html)

[Ninja——小而快的构建系统](https://www.jianshu.com/p/16cbac21da3e)

[Ninja编译过程分析](https://www.cnblogs.com/wangym/p/8317310.html)

[GCC全过程详解+剖析生成的.o文件](https://blog.csdn.net/gt1025814447/article/details/80442673)

[Is it possible to get GCC to read from a pipe?](https://stackoverflow.com/questions/1003644/is-it-possible-to-get-gcc-to-read-from-a-pipe)

[ ELF parsing/loading library ](https://github.com/elfmaster/libelfmaster)

[C++11 ELF/DWARF parser ](https://github.com/aclements/libelfin)

[使用objdump objcopy查看与修改符号表](https://blog.csdn.net/foruok/article/details/21157467)

[模仿操作系统，加载pe文件到内存中 ](https://github.com/potats0/PeLoader)

[A Windows PE format file loader ](https://github.com/polycone/pe-loader)

[ARMv7M ELF loader ](https://github.com/martinribelotta/elfloader)

[Dynamic COFF object loader ](https://github.com/lieff/dynobj)

[ELF & PE & COFF](https://www.jianshu.com/p/9884c8823712)

[COFF、ELF、OMF](https://blog.csdn.net/guo_wangwei/article/details/1902260)

## 编译缓存

Ccache (or “ccache”) is a compiler cache. It speeds up recompilation by caching previous compilations and detecting when the same compilation is being done again.

ccache是一个编译器缓存。它通过缓存以前编译的结果并检测何时再次执行相同的编译来加速重新编译。支持的语言是C、c++、Objective-C和objective - c++

[ compiler cache](https://ccache.dev/)

[CCache](https://blog.csdn.net/pengyuan_D/article/details/80214784)

[ccache - 让Xcode编译速度飞起来](https://www.cnblogs.com/fishbay/p/7217398.html)

[ccache的使用](https://blog.csdn.net/shui1025701856/article/details/78527151)

[v8-compile-cache 源码分析 ](https://flyyang.me/2019/01/16/v8-compile-cache/)