# 框架和库

##  apache/arrow

Apache Arrow is a cross-language development platform for in-memory data. It specifies a standardized language-independent columnar memory format for flat and hierarchical data, organized for efficient analytic operations on modern hardware. It also provides computational libraries and zero-copy streaming messaging and interprocess communicationâ€¦ https://arrow.apache.org

https://github.com/apache/arrow



## grpc/grpc-web

gRPC for Web Clients

https://github.com/grpc/grpc-web


## ballista
https://github.com/andygrove/ballista

Experimental Distributed Compute Platform based on Kubnernetes and Apache Arrow


## timberio/vector

https://github.com/timberio/vector

Collect, transform, & route all observability data with one simple tool. https://vector.dev

lang:Rust

Vector is an open-source utility for building observability pipelines. Collect, transform, and route log, metrics and events with one simple tool.

Built in Rust, Vector places high-value on performance, correctness, and operator friendliness. It compiles to a single static binary and is designed to be deployed across your entire infrastructure, serving both as a light-weight agent and a highly efficient service. Take back ownership and control of your observability data with Vector.


## swupdate

https://github.com/sbabic/swupdate

Software Update for Embedded Systems

SWUpdate is a Linux Update agent with the goal to provide an efficient and safe way to update an embedded system. SWUpdate supports local and remote updates, multiple update strategies and it can be well integrated in the Yocto build system by adding the meta-swupdate layer.


## Habitat

Habitat is open source software that creates platform-independent build artifacts and provides built-in deployment and management capabilities.


[src](https://github.com/habitat-sh/habitat)


## fractalide

https://github.com/fractalide/fractalide

Fractalide is a free and open source service programming platform using dataflow graphs. Graph nodes represent computations, while graph edges represent typed data (may also describe tensors) communicated between them. This flexible architecture can be applied to many different computation problems, initially the focus will be Microservices to be expanded out into the Internet of Things.

Fractalide是一个使用数据流图的免费开源服务编程平台。图节点表示计算，而图边表示它们之间通信的类型化数据(也可以描述张量)。这种灵活的架构可以应用于许多不同的计算问题，最初的重点将是扩展到物联网的微服务。


## Tokio

A runtime for writing reliable, asynchronous, and slim applications with the Rust programming language.

Tokio is an event-driven, non-blocking I/O platform for writing asynchronous applications with the Rust programming language. At a high level, it provides a few major components:

[src](https://github.com/tokio-rs/tokio)

[web site](https://tokio.rs/)

[Tokio，Rust异步编程实践之路](https://www.cnblogs.com/hymenz/p/9334297.html)

[Tokio中文](https://tokio-zh.github.io/)

[Tokio中文](https://github.com/tokio-zh/tokio-zh)

[rustlang-cn](https://rustlang-cn.org/crates/tokio/)


# Pothos

Pothos is a scheduling framework and an API for solving problems with interconnected processing blocks. Some of its prominent features are the network-distributed topologies, minimal-boilerplate for creating new processing blocks, and buffer management techniques. Read more on the features page.
Graphical tools

Pothos has a GUI design tool to accompany the library (Pothos GUI). Some prominent features of the GUI are live evaluation, live topology reconfiguration, support for networked topologies, and embedded widgets and plotters. Learn more on the GUI tutorial.

可GUI 模块化配置应用(系统) ?

[Overview](https://github.com/pothosware/PothosCore/wiki/Overview)

[ComponentsMap](https://github.com/pothosware/PothosCore/wiki/ComponentsMap)

# PothosFlow

GUI frontend and designer tool for the Pothos framework

[src](https://github.com/pothosware/PothosFlow)

# ECS/DOD

现代的程序设计思想要求我们以计算机的方式去解决问题（而不是以人脑的方式），“面向数据的设计”思想可以说是沿着这个方向又前进了一大步。这种程序设计的思想的出现和流行和计算机硬件的发展是息息相关的。乔布斯曾经引用过 Alan Kay 的一句名言说软件开发者必须关心硬件。下面我就结合计算机硬件的发展现状来说明一下这种设计思路的优势在哪里，也就是说为什么 ECS 之类是更好的设计！

并行计算是软件开发的下一次变革,面向对象在并行编程方面有天生的劣势,面向数据的设计，从起点就考虑并行的问题.

ECS 只是“面向数据的设计”思想下的一种设计模式，可以预见接下来在各个特定的领域会产生更多的以数据为中心的设计模式，特别是在并行计算领域，面向数据的设计将占主导地位！

[ECS 与面向数据的设计](https://blog.csdn.net/Neil3D/article/details/84670943)

[simple C++ header-only type-safe entity component system library](https://github.com/redxdev/ECS)

[EnTT a fast and reliable entity component system (ECS)](https://github.com/skypjack/entt)


# ACL

acl 工程是一个跨平台（支持LINUX，WIN32，Solaris，MacOS，FreeBSD）的网络通信库及服务器编程框架，同时提供更多的实用功能库。通过该库，用户可以非常容易地编写支持多种模式(多线程、多进程、非阻塞、触发器、UDP方式、协程方式)的服务器程序，WEB 应用程序，数据库应用程序。此外，该库还提供了常见应用的客户端通信库（如：HTTP、SMTP、ICMP、redis、memcache、beanstalk、handler socket），常见流式编解码库：XML/JSON/MIME/BASE64/UUCODE/QPCODE/RFC2047 etc。

[src](https://github.com/acl-dev/acl)

https://github.com/acl-dev/microservice

microservice
基于acl框架 设计实现的轻量级微服务框架
http_rpc rpc框架
publisher 二进制包 发布服务。
nameservice 服务注册
gateservice api网关
mqservice 消息队列服务
configservice 配置服务
logservice log服务
authservice 认证服务
msgservice 消息推送服务
monitorservice 服务监控
