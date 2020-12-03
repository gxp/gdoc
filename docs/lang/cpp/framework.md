# fruit

Fruit, a dependency injection framework (IOC) for C++

[src](https://github.com/google/fruit)

# boost.di

DI: C++14 Dependency Injection Library

https://github.com/boost-ext/di

https://github.com/boost-ext/sml

SML: C++14 State Machine Library

https://github.com/boost-ext/ut

UT: C++20 μ(micro)/Unit Testing Framework

# Folly

Folly (acronymed loosely after Facebook Open Source Library) is a library of C++14 components designed with practicality and efficiency in mind. Folly contains a variety of core library components used extensively at Facebook. In particular, it's often a dependency of Facebook's other open source C++ efforts and place where those projects can share code.

https://github.com/facebook/folly


# RuntimeCompiledCPlusPlus

Change C++ code at runtime

https://github.com/RuntimeCompiledCPlusPlus/RuntimeCompiledCPlusPlus

# easy-just-in-time

LLVM Optimization to extract a function, embedded in its intermediate representation in the binary, and execute it using the LLVM Just-In-Time compiler.

[src](https://github.com/jmmartinez/easy-just-in-time)

# JUCE

JUCE is an open-source cross-platform C++ application framework for desktop and mobile applications, including VST, VST3, AU, AUv3, RTAS and AAX audio plug-ins.

[src](https://github.com/juce-framework/JUCE)


# 插件

模块/插件/扩展/组件框架：为什么重新发明轮子，使用一个好的框架来让我们专注于我们的应用的特殊之处。这里有很多选择。 Objective-C有它的NSBundles; C++拥有像Boost.Extension，Pluma，DynObj，FxE​​ngine等库; C有C-Pluff;我甚至会说有太多的选择。

DynObj Boost.Extension : 无人维护

http://pluma-framework.sourceforge.net/?page_id=25 无维护  https://github.com/armFunNing/pluma

[Runtime Compiled C & C++ Solutions](https://github.com/RuntimeCompiledCPlusPlus/RuntimeCompiledCPlusPlus/wiki/Alternatives)

# XBMC

XBMC 中有自己的插件框架

Kodi is an award-winning free and open source home theater/media center software and entertainment hub for digital media. With its beautiful interface and powerful skinning engine, it's available for Android, BSD, Linux, macOS, iOS and Windows.

https://github.com/xbmc/xbmc


# taskflow

Parallel and Heterogeneous Task Programming in Modern C++

Taskflow helps you quickly write parallel tasks programs in modern C++


[src](https://github.com/taskflow/taskflow)

# workflow

Sogou’s C++ Asynchronous Programming Engine

搜狗公司C++服务器引擎，支撑搜狗几乎所有后端C++在线服务，包括所有搜索服务，云输入法，在线广告等，每日处理超百亿请求。这是一个设计轻盈优雅的企业级程序引擎，可以满足大多数C++后端开发需求。

 * 快速搭建http服务器
 * 作为万能异步客户端。目前支持http，redis，mysql和kafka协议。
 * 实现自定义协议client/server，构建自己的RPC系统。
 *      srpc就是以它为基础，作为独立项目开源。支持srpc，brpc和thrift等协议。
 *   构建异步任务流，支持常用的串并联，也支持更加复杂的DAG结构。
 *   作为并行编程工具使用。除了网络任务，我们也包含计算任务的调度。所有类型的任务都可以放入同一个流中。
 *   在Linux系统下作为文件异步IO工具使用，性能超过任何标准调用。磁盘IO也是一种任务。
 *   实现任何计算与通讯关系非常复杂的高性能高并发的后端服务。
 *   构建服务网格（service mesh）系统。
 *      项目内置服务治理与负载均衡等功能。


https://github.com/sogou/workflow


# WindFlow

A C++17 Data Stream Processing Parallel Library for Multicores and GPUs

WindFlow is a C++17 library for parallel data stream processing targeting heterogeneous shared-memory architectures equipped with multi-core CPUs and GPUs. The library provides common stream processing operators like map, flatmap, filter, fold/reduce as well as sliding-window operators designed with complex parallel processing methods. The API allows building streaming applications through the MultiPipe and the PipeGraph programming constructs. The first is used to create parallel pipelines, while the second one allows several MultiPipe instances to be interconnected through merge and split operations, thus creating complex directed acyclic graphs of interconnected operators.

The web site of the library is available at: https://paragroup.github.io/WindFlow/.

https://github.com/ParaGroup/WindFlow

# actor-framework

An Open Source Implementation of the Actor Model in C++

Actor模型是一个概念模型，用于处理并发计算。它定义了一系列系统组件应该如何动作和交互的通用规则.
一个Actor指的是一个最基本的计算单元。它能接收一个消息并且基于其执行计算。

[src](https://github.com/actor-framework/actor-framework)

# lager

lager is a C++ library to assist value-oriented design by implementing the unidirectional data-flow architecture. It is heavily inspired by Elm and Redux, and enables composable designs by promoting the use of simple value types and testable application logic via pure functions. And you get time-travel for free!

[src](https://github.com/arximboldi/lager)


# zeek

Zeek is a powerful network analysis framework that is much different from the typical IDS you may know.

[src](https://github.com/zeek/zeek)

# Drogon

 A C++14/17 based HTTP web application framework running on Linux/macOS/Unix/Windows

[src](https://github.com/an-tao/drogon)

# handy

简洁易用的C++11网络库 / 支持单机千万并发连接 / a simple C++11 network server framework

[src](https://github.com/yedf/handy)


# PothosCore

The Pothos data-flow framework

https://github.com/pothosware/PothosCore

# CppMicroService


# NoahGameFrame

A fast, scalable, distributed game server engine/framework for C++, include the actor library, network library, can be used as a real time multiplayer game engine ( MMO RPG/MOBA ), which support C#/Lua script/ Unity3d, Cocos2dx and plan to support Unreal.

https://github.com/ketoo/NoahGameFrame


# dynamic-graph

Efficient data-flow library for robotics.

This software provides an efficient way to modelize a C++ data-flow.

A dynamic graph data-flow is composed of:

    entities (graph nodes)
    signals (input/output of a graph action)

Output signals can then be plugged into input signals to data transmission.

An efficient caching mechanism avoid useless data recomputation and a simple built-in language can be used to control the graph actions.

It is released under the BSD-clause 2 license.

https://github.com/stack-of-tasks/dynamic-graph

# seastar

High performance server-side application framework

SeaStar is an event-driven framework allowing you to write non-blocking, asynchronous code in a relatively straightforward manner (once understood). It is based on futures.

https://github.com/scylladb/seastar

# neutralinojs

Portable and lightweight cross platform application development framework

Neutralino is a lightweight and portable application development framework. It lets you develop cross-platform applications using JavaScript/TypeScript, HTML and CSS.

https://github.com/neutralinojs/neutralinojs


# shaka-packager

A media packaging and development framework for VOD and Live DASH and HLS applications, supporting Common Encryption for Widevine and other DRM Systems.

Shaka Packager is a tool and a media packaging SDK for DASH and HLS packaging and encryption. It can prepare and package media content for online streaming.

https://github.com/google/shaka-packager

# ULib

C++ application development framework, to help developers create and deploy applications quickly and simply

ULib is a highly optimized class framework for writing C++ applications. I wrote this framework as my tool for writing applications in various contexts. It is a result of many years of work as C++ programmer. I think, in my opinion, that its strongest points are simplicity, efficiency and sophisticate debugging.

https://github.com/stefanocasazza/ULib


# asylo

An open and flexible framework for developing enclave applications

Asylo is an open and flexible framework for developing enclave applications. Asylo lets you take advantage of a range of emerging trusted execution environments (TEEs), including both software and hardware isolation technologies.

Asylo provides:

    The ability to execute trusted workloads in an untrusted environment, inheriting the confidentiality and integrity guarantees from the security backend, i.e., the underlying enclave technology.
    Ready-to-use containers, an open source API, libraries, and tools so you can develop and run applications that use one or more enclaves.
    A choice of security backends.
    Portability of your application's source code across security backends.

Asylo is under active development. We want to expand Asylo's capabilities to meet more developers' needs. To do this, we plan to add support for more backends, libraries, and languages.

https://github.com/google/asylo

# alembic

Alembic is an open framework for storing and sharing scene data that includes a C++ library, a file format, and client plugins and applications.


Alembic is an open computer graphics interchange framework. Alembic distills complex, animated scenes into a non-procedural, application-independent set of baked geometric results. This �distillation' of scenes into baked geometry is exactly analogous to the distillation of lighting and rendering scenes into rendered image data.

https://github.com/alembic/alembic

http://www.alembic.io/


# ffead-cpp

Framework for Enterprise Application Development, webrtc signalling server, peerjs webrtc, c++ framework, c++ web framework, c++ application framework, c++ rest framework, c++ soap framework, c++ web sites, c++ web applications, c++ driven web development - c++

ffead-cpp is a web-framework, application framework, utilities all bundled into one. It also provides an embedded HTTP/Web-Socket compliant high-performance server core. It is a collection of modules all geared towards performing individual roles which together form the cohesive back-bone of ffead-cpp.

It provides a very simple to use and maintain web-framework library with advanced features like Reflection, Dependency Injection (IOC), Inbuilt REST/SOAP support, Security/Authentication features. Moreover implementation for interfacing to caching tools like Memcached/Redis are provided in-built. Database integration/ORM framework (SDORM) solves all major issues with respect to interfacing with SQL/No-SQL database alike.

https://github.com/sumeetchhetri/ffead-cpp


# ARK

ARK is a lightweight, agility, elastic, distributed plugin framework written in C++，make it easier and faster to create your own application service.


    Flexible apps, plugins, and modules
    The general abstract data system
    Interface-oriented and data-oriented programming(IOP & DOP)
    Event-driven and data-driven
    Data & procedure tracing
    Use Excel as configuration files, easier for the designers
    Lower training and education costs
    Based on C++ standard, easy to handle and learn
    Cross-platform (Include Windows and Linux)
    High availability architectures
    High concurrency and performance of the network
    With existed simple Unity3D client for rapid development
    Plentiful plugins(DB, script, HTTP, WebSocket, etc.)
    Customization service for business customer

https://github.com/ArkNX/ARK


# faasm

High-performance stateful serverless runtime based on WebAssembly

Faasm provides multi-tenant isolation, yet allows functions to share regions of memory. These shared memory regions give low-latency concurrent access to data, and are synchronised globally to support large-scale parallelism.

Faasm combines software fault isolation from WebAssembly with standard Linux tools, to provide security and resource isolation at low cost. Faasm runs functions side-by-side as threads of a single runtime process, with low overheads and fast boot times.

云计算中的无服务器计算正在成为部署数据密集型应用程序的一种流行方式。一个函数即服务（FaaS）模型将计算分解为多个函数，可以有效地利用云的海量并行性。以前的工作已经展示了无服务器计算如何支持map/reduce风格的作业、机器学习训练和推理以及线性代数计算。因此，越来越多的应用程序，用不同的编程语言实现，正在迁移到无服务器平台。

https://github.com/faasm/faasm

[Faasm 轻量级隔离实现高效的有状态无服务器计算](https://zhuanlan.zhihu.com/p/134152415)


# Mars

Mars 是微信官方的跨平台跨业务的终端基础组件


    comm：可以独立使用的公共库，包括 socket、线程、消息队列、协程等；
    xlog：高可靠性高性能的运行期日志组件；
    SDT： 网络诊断组件；
    STN： 信令分发网络模块，也是 Mars 最主要的部分。


[src](https://github.com/Tencent/mars)


# omr

Eclipse OMR™ Cross platform components for building reliable, high performance language runtimes 

The Eclipse OMR project is a set of open source C and C++ components that can be used to build robust language runtimes that support many different hardware and operating system platforms.

Our current components are:

    gc: Garbage collection framework for managed heaps
    compiler: Components for building compiler technology, such as JIT compilers.
    jitbuilder: An easy to use high level abstraction on top of the compiler technology.
    port: Platform porting library
    thread: A cross platform pthread-like threading library
    util: general utilities useful for building cross platform runtimes
    omrsigcompat: Signal handling compatibility library
    omrtrace: Tracing library for communication with IBM Health Center monitoring tools
    tool: Code generation tools for the build system
    vm: APIs to manage per-interpreter and per-thread contexts
    example: Demonstration code to show how a language runtime might consume some Eclipse OMR components
    fvtest: A language-independent test framework so that Eclipse OMR components can be tested outside of a language runtime


[src](https://github.com/eclipse/omr)


# Hypodermic

Hypodermic is an IoC container for C++. It provides dependency injection to your existing design. 

Hypodermic is a non-intrusive header only IoC container for C++. It provides dependency injection to your existing design by managing the creation of your components and their dependencies in the right order, sparing you the trouble of writing and maintaining boiler plate code.

Used in production environments since 2012.

[Hypodermic](https://github.com/ybainier/Hypodermic)


# kangaroo

kangaroo A dependency injection container for C++11, C++14 and later 

Kangaru is an inversion of control container for C++11, C++14 and later. It provides many features to automate dependency injection and reduce the amount of wiring boilerplate in your code. We are achiving that by exposing in code configuration for autowiring, constructor and function parameters injection. We aim to keep the simplest interface possible and keep boilerplate to a minimum. On top of that, we don't want to be intrusive into user/library code.

Kangaru is a header only library because of it's extensive use of templates. The name kangaru comes from the container's feature to inject itself into a service as a dependency, and because kangaroos are awesome.

[](https://github.com/gracicot/kangaru)

# qaop

C++ AOP framework. Intuitive and fast to do AOP with C++. 

[src](https://github.com/whitebob/qaop)