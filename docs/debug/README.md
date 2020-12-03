

# rr

rr aspires to be your primary C/C++ debugging tool for Linux, replacing — well, enhancing — gdb. You record a failure once, then debug the recording, deterministically, as many times as you want. The same execution is replayed every time.

可以记录程序执行过程

[web site](https://rr-project.org/)


# strace

strace常用来跟踪进程执行时的系统调用和所接收的信号。
在Linux世界，进程不能直接访问硬件设备，当进程需要访问硬件设备(比如读取磁盘文件，接收网络数据等等)时，必须由用户态模式切换至内核态模式，通过系统调用访问硬件设备。

strace可以跟踪到一个进程产生的系统调用,包括参数，返回值，执行消耗的时间。

ltrace命令 是用来跟踪进程调用库函数的情况。

[如何使用strace+pstack利器分析程序性能](https://www.cnblogs.com/bangerlee/archive/2012/04/30/2476190.html)

pstack命令可显示每个进程的栈跟踪。pstack 命令必须由相应进程的属主或 root 运行。可以使用 pstack 来确定进程挂起的位置。此命令允许使用的唯一选项是要检查的进程的 PID。

[pstack命令](https://man.linuxde.net/pstack)

[关于linux下的死锁（程序卡住）的定位检测](https://www.cnblogs.com/LyndonYoung/articles/7364165.html)

https://github.com/peadar/pstack

[GDB 打印堆栈信息](https://github.com/bangerlee/strace_pstack/blob/master/pstack.sh)

# lsof

可以列出被进程所打开的文件的信息。被打开的文件可以是

1.普通的文件，2.目录  3.网络文件系统的文件，4.字符设备文件  5.(函数)共享库  6.管道，命名管道 7.符号链接

8.底层的socket字流，网络socket，unix域名socket

9.在linux里面，大部分的东西都是被当做文件的…..还有其他很多

列出所有的网络连接

lsof -i

[linux命令 — lsof 查看进程打开那些文件 或者 查看文件给那个进程使用](https://www.cnblogs.com/bonelee/p/7735479.html)


# systemtap

SystemTap对内核及用户态程序提供了动态追踪功能，用户可以自定探测事件来跟踪程序的运行情况，如函数的调用路径、CPU占用和磁盘IO等一系列可以探测的情况。有了systemtap，可以在程序不修改代码，甚至不用重启就能分析出程序的运行情况。

[动态追踪技术之SystemTap](https://www.cnblogs.com/shuqin/p/13196585.html)

[内核探测工具systemtap简介](https://www.cnblogs.com/hazir/p/systemtap_introduction.html)

[如何利用SystemTap统计函数执行耗时详解](https://www.jb51.net/article/124140.htm)


# gdb

[GDB 打印堆栈信息](https://github.com/bangerlee/strace_pstack/blob/master/pstack.sh)

[gdb 查看堆栈信息、加载core文件、连接到其它进程](https://blog.csdn.net/zhangzheng0413/article/details/7569364)

[gdb 打印所有线程堆栈](https://blog.csdn.net/wh8_2011/article/details/54093976)

[GDB调试（正在运行的程序）](https://blog.csdn.net/sjin_1314/article/details/11778675)

```
gdb attach PID

gcore命令生成CORE文件
进程信息可以用info  proc显示
寄存器信息可以用info reg显示
```

# boost.stacktrace

How can one display the call sequence in C++? What function called the current function? What call sequence led to an exception?

Boost.Stacktrace library is a simple C++03 library that provides information about call sequence in a human-readable form.

https://www.boost.org/doc/libs/1_74_0/doc/html/stacktrace.html


# Matrix

Matrix 是一款微信研发并日常使用的应用性能接入框架，支持iOS, macOS和Android。 Matrix 通过接入各种性能监控方案，对性能监控项的异常数据进行采集和分析，输出相应的问题分析、定位与优化建议，从而帮助开发者开发出更高质量的应用。
Matrix for iOS/macOS

当前工具监控范围包括：崩溃、卡顿和爆内存，包含以下两款插件：

    WCCrashBlockMonitorPlugin： 基于 KSCrash 框架开发，具有业界领先的卡顿堆栈捕获能力，同时兼备崩溃捕获能力。

    WCMemoryStatPlugin： 一款性能优化到极致的爆内存监控工具，能够全面捕获应用爆内存时的内存分配以及调用堆栈情况。

特性
WCCrashBlockMonitorPlugin

    接入简单，代码无侵入
    通过检查 Runloop 运行状态判断应用是否卡顿，同时支持 iOS/macOS 平台
    增加耗时堆栈提取，卡顿线程快照日志中附加最近时间最耗时的主线程堆栈

WCMemoryStatPlugin

    在应用运行期间获取对象存活以及相应的堆栈信息，在检测到应用爆内存时进行上报
    使用平衡二叉树存储存活对象，使用 Hash Table 存储堆栈，将性能优化到极致


# 参考

[linux查看线程执行状态+python获取线程id](https://blog.csdn.net/cy_shichao/article/details/85104239)

[linux查看具体进程占用的网络流量](https://blog.csdn.net/qq_40907977/article/details/103905314)

[使用strace,lstrace,truss来跟踪程序的运行过程](https://www.jianshu.com/p/5c7b735fc9c5)

[Linux下查看进程打开的文件句柄数](https://cloud.tencent.com/developer/article/1491256)

[强制进程产生coredump，检测死锁以及进程快照](https://blog.csdn.net/weixin_33777877/article/details/89863927)

[详解coredump](https://blog.csdn.net/tenfyguo/article/details/8159176)

[gdb调试coredump（使用篇）](https://zhuanlan.zhihu.com/p/46605905)

[Linux 命令 - kill: 向进程发送信号](https://www.cnblogs.com/huey/p/4871503.html)

[你用过的最好的代码阅读或编辑工具是什么](https://www.zhihu.com/question/19570229)

[开源免费的源码阅读神器 Sourcetrail](https://zhuanlan.zhihu.com/p/96685579)

[源码阅读工具 UnderStand](https://blog.csdn.net/wangming520liwei/article/details/103603077)

[强大到令人发指的代码浏览分析工具understand](https://blog.csdn.net/thisisfangsheng/article/details/46836689?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)