# os

## 参考

[主流嵌入式操作系统（RTOS）有哪些？看看这14种 ](https://www.sohu.com/a/332985081_100281310)

[GNU GPL 许可证常见问题解答](https://zhuanlan.zhihu.com/p/39513925)

[使用了GPL软件开发的产品，如何避免GPL感染？](https://www.zhihu.com/question/19771481)

[一图看懂开源许可协议：GPL、BSD、MIT、Mozilla、Apache、LGPL](http://www.techbulo.com/2489.html)

[嵌入式 Linux 法律问题](http://tinylab.org/embedded-linux-legal-issues/)

[PlatformIO 玩转单片机开发](https://www.zhihu.com/column/c_1094956718374633472)


# 平台

## evm

超轻量级物联网虚拟机 

EVM 全称 Embedded Virtural Machine，本质上是一款通用、精简的嵌入式虚拟机，由语法解析前端框架和字节码运行后端构成，可运行在资源受限制的单片机上。

EVM 优势特点

    纯C开发、零依赖、跨平台、内置REPL；
    最小编译体积40KB，最小内存占用2KB;
    支持多语言混合开发，目前支持Javascript、Python、Lua、QML、Json、XML等语言;
    先进的内存管理，无内存泄露和内存碎片问题;
    高效的运行性能，性能媲美QuickJs;
    灵活的虚拟机扩展技术，多语言可共享扩展功能;

[src](https://github.com/scriptiot/evm)


## Tengine

Tengine is a lite, high performance, modular inference engine for embedded device 

Tengine Lite 由 OPEN AI LAB 主导开发，该项目实现了深度学习神经网络模型在嵌入式设备上的快速、高效部署需求。为实现在众多 AIoT 应用中的跨平台部署，本项目基于原有 Tengine 项目使用 C 语言进行重构，针对嵌入式设备资源有限的特点进行了深度框架裁剪。同时采用了完全分离的前后端设计，有利于 CPU、GPU、NPU 等异构计算单元的快速移植和部署。同时兼容 Tengine 框架原有 API 和 模型格式 tmfile，降低评估、迁移成本。

Tengine Lite 核心代码由 4 个模块组成：

    dev：NN Operators 后端模块，当前提供 CPU 代码，后续逐步开源 GPU、NPU 参考代码；
    lib：框架核心部件，包括 NNIR、计算图、硬件资源、模型解析器的调度和执行模块；
    op：NN Operators 前端模块，实现 NN Operators 注册、初始化；
    serializer：模型解析器，实现 tmfile 格式的网络模型参数解析。

https://github.com/OAID/Tengine


# 参考

[立创开源硬件平台](https://oshwhub.com/)