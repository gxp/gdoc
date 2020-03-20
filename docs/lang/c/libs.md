# stb

single-file public domain (or MIT licensed) libraries for C/C++

Noteworthy:

    image loader: stb_image.h
    image writer: stb_image_write.h
    image resizer: stb_image_resize.h
    font text rasterizer: stb_truetype.h
    typesafe containers: stb_ds.h

[github](https://github.com/nothings/stb)

# tbox

TBOX是一个用c语言实现的跨平台开发库。

针对各个平台，封装了统一的接口，简化了各类开发过程中常用操作，使你在开发过程中，更加关注实际应用的开发，而不是把时间浪费在琐碎的接口兼容性上面，并且充分利用了各个平台独有的一些特性进行优化。

这个项目的目的，是为了使C开发更加的简单高效。

特性:

* 流库 http、file、socket、data
* 协程库
* 数据库
* xml库
* 内存库
* 容器库
* 算法库
* 网络库

...

全，c语言中，标准库 or boost的替代。

[github](https://github.com/tboox/tbox)


# klib

A standalone and lightweight C library

Klib: a Generic Library in C
Overview

Klib is a standalone and lightweight C library distributed under MIT/X11 license. Most components are independent of external libraries, except the standard C library, and independent of each other. To use a component of this library, you only need to copy a couple of files to your source code tree without worrying about library dependencies.

Klib strives for efficiency and a small memory footprint. Some components, such as khash.h, kbtree.h, ksort.h and kvec.h, are among the most efficient implementations of similar algorithms or data structures in all programming languages, in terms of both speed and memory use.

A new documentation is available here which includes most information in this README file.
Common components

    khash.h: generic hash table with open addressing.
    kbtree.h: generic search tree based on B-tree.
    kavl.h: generic intrusive AVL tree.
    ksort.h: generic sort, including introsort, merge sort, heap sort, comb sort, Knuth shuffle and the k-small algorithm.
    kseq.h: generic stream buffer and a FASTA/FASTQ format parser.
    kvec.h: generic dynamic array.
    klist.h: generic single-linked list and memory pool.
    kstring.{h,c}: basic string library.
    kmath.{h,c}: numerical routines including MT19937-64 pseudorandom generator, basic nonlinear programming and a few special math functions.
    ketopt.h: portable command-line argument parser with getopt_long-like API.


[github](https://github.com/attractivechaos/klib)


# gear-lib

Gear-Lib, C library for IOT Embedded Multimedia and Network

这是一组通用的Ｃ基础库

    全部用POSIX C实现，目标是为了跨平台兼容linux, windows, android, ios.
    适用于物联网，嵌入式，以及网络服务开发等场景

    数据结构

        libdict: 哈希字典
        libhash: linux内核原生哈希库
        libringbuffer: 循环缓冲
        libqueue: 数据队列
        librbtree: 内核rbtree
        libsort:
        libvector: 容器库
        libmacro: 通用宏定义
        libdarray: 动态数组

    网络库

        librtsp: RTSP协议，适合IPCamera和NVR开发
        librtmpc: RTMP协议，适合推流直播
        libskt: Socket封装
        librpc: 远程过程调用库
        libipc: 进程间通信
        libp2p: p2p穿透传输
        libhomekit: Apple homekit协议库

    异步

        libgevent: 事件驱动
        libthread: 线程
        libworkq: 工作队列

    I/O

        libbase64: Base64/32 编解码
        libconfig: 配置文件库
        liblog: 日志库
        libfile: 文件操作库
        libstrex:
        libsubmask: 网络地址翻译

    多媒体

        libuvc: USB摄像头库
        libmp4parser: MP4解析库
        libjpeg-ex:
        libmedia-io: 音频视频格式定义

    系统抽象层

        libposix4win: windows平台poxix适配库
        libposix4rtos: FreeRTOS平台poxix适配库

    其他

        libdebug: 调试辅助库
        libhal: 硬件抽象层
        libplugin: 动态加载库
        libtime: 时间库
        libfsm: 有限状态机

License: MIT

[github](https://github.com/gozfree/gear-lib)


# mmx

My single header libraries for C/C++.

|library | lastest version | category | LoC | license | description
| --------------------- | ---- | -------- | --- | --- | --------------------------------
|**lexer.h** | 1.00 | parser | 1155 | zlib | simple lexer for C-like languages
|**json.h** | 1.00 | parser | 848 | zlib | non-allocating json parser
|**sched.h** | 1.00 | multithreading | 699 | zlib | multithreaded task scheduler
|**vec.h** | 0.02 | math | 2240 | zlib | vector math
|**web.h** | 1.00 | network | 1455 | BSD |  lightweight webserver
