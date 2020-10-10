## sysget

https://github.com/emilengler/sysget

A front-end for every package manager

sysget is a bridge that lets you use one syntax to every package manager on every unix-based operating system.
You probably all know the problem when you are on a new distro and don't know anything about the package manager. With sysget you just need to remember one syntax for every package manager.
The syntax is mostly same with apt so it should be easy to use.

Supported package managers:

    apt  xbps   dnf    yum  zypper    eopkg    pacman    emerge     pkg     pkg_mgr
    chromebrew     homebrew     nix  snap    npm    flatpak    slapt-get
    pip3    GNU guix    Ruby gems    MacPorts
    Your own package manager (See Add your own package manager)

Features

*    search for packages
*    install packages
*    remove packages
*    remove orphans
*    clear package manager cache
*    update database
*    upgrade system
*    upgrade single package


## clib

https://github.com/clibs/clib

Package manager for the C programming language.


## synaptic

https://github.com/mvo5/synaptic

新立德包管理器

##  apt-dater

With apt-dater you can easily keep one or more (Debian) GNU/Linux hosts up to date.

https://github.com/DE-IBH/apt-dater


## swupdate

https://github.com/sbabic/swupdate

SWUpdate is a Linux Update agent with the goal to provide an efficient and safe way to update an embedded system. SWUpdate supports local and remote updates, multiple update strategies and it can be well integrated in the Yocto build system by adding the meta-swupdate layer.


## Flatpak

https://blog.csdn.net/renajia/article/details/79171619

原文地址：http://docs.flatpak.org/en/latest/introduction.html#the-flatpak-command

Flatpak是一种构建、发布、安装和运行应用程序的技术。它主要的目标是Linux桌面系统，同时也可以适用于嵌入式等系统中。

Flatpak的设计目标是：
* 使应用程序可以安装在任何一个发行版上
* 为应用程序提供固定的环境，实施测试和减少缺陷
* 实现应用程序和操作系统的解耦和，使应用程序可以不依赖于特定的发行版本
* 使应用程序可以自带依赖，能够使用linux发行版没有提供的依赖，避免其对特定发行版本甚至特定库的依赖
* 在沙箱中独立运行应用程序，提升安全性

lang: C

## OSTree

OSTree is an upgrade system for Linux-based operating systems that performs atomic upgrades of complete filesystem trees. It is not a package system; rather, it is intended to complement them. A primary model is composing packages on a server, and then replicating them to clients.

The underlying architecture might be summarized as "git for operating system binaries". It operates in userspace, and will work on top of any Linux filesystem. At its core is a git-like content-addressed object store with branches (or "refs") to track meaningful filesystem trees within the store. Similarly, one can check out or commit to these branches.

Layered on top of that is bootloader configuration, management of /etc, and other functions to perform an upgrade beyond just replicating files.

You can use OSTree standalone in the pure replication model, but another approach is to add a package manager on top, thus creating a hybrid tree/package system.

[github](https://github.com/ostreedev/ostree)

## meta-updater

OTA Software updates using OSTree

Meta-updater is a Yocto layer that enables over-the-air updates (OTA) with OSTree and Aktualizr — the default client for HERE OTA Connect.

[github](https://github.com/advancedtelematic/meta-updater)
[概览最有前景的下一代嵌入式 Linux 软件更新机制](http://www.techweb.com.cn/network/system/2016-12-21/2456610.shtml)

注意： 嵌入式系统在线更新，增量更新

目前已有多个 Linux 软件商使用增量原子更新方式来传递更可靠的发行版更新，通过二进制差异实现更小体积的更新，假如出现意外状况也运行回退。这些新的发行版升级机制包含了 SWUpdate、Mender、OSTree 和 swupd。但有趣的是，幻灯片之中并没有提及 Ubuntu 的 Snappy。

SWUpdate 一种单/双镜像的模块化升级框架，支持镜像签名、可以使用 Kconfig 来进行配置、能够处理本地或者远程升级等。SWUpdate 简直就是为嵌入式系统设计的。

而 Mender 则是以无线传输进行升级位目标的升级方案。它是用 Go 编程语言编写的双镜像升级框架。

OSTree 是此次增量原子升级方案演示中最有名气的，它类似于 Git。Fedora 和 RedHat 都有它的身影，甚至 Gnome 的 Flatpak 容器系统也使用了 OSTree。

Swupd 是最后展示的一个升级系统，是由 Intel 的 Clear Linux 发行版率先使用的升级方案。它的代码放在GitHub，而它的客户端和服务端则由 Clear Linux 托管。Swupd 与 OSTree 相似，但它不必重启就可以启用更新。

## swupd

[github](https://github.com/clearlinux/swupd-client)

## mender

Mender over-the-air software updater client. https://mender.io

Mender: over-the-air updater for embedded Linux devices

Mender is an open source over-the-air (OTA) software updater for embedded Linux devices. Mender comprises a client running at the embedded device, as well as a server that manages deployments across many devices.

[github](https://github.com/mendersoftware/mender)

lang:go

## WinGUp

WinGUp is a Generic Updater running under Windows environment. The aim of WinGUp is to provide a ready to use and configurable updater which downloads a update package then installs it. By using cURL library and TinyXml module, GUP is capable to deal with http protocol and process XML data.

Originally WinGUp was made for the need of Notepad++ (a generic source code editor under MS Windows). During its conception, the idea came up in my mind : if it can fit Notepad++, it can fit for any Windows program. So here it is, with LGPL license to have no (almost not) restriction for integration in any project.

Being LGPLed, WinGUp can be integrated in both commercial (or close source) and open source project. So if you run a commercial or open a source project under MS Windows and you release your program at regular intervals, then you may need WinGUp to notice your users the new update.

WinGUp source code repository is available on GitHub:

https://github.com/donho/wingup.git

## OPKG

OPKG Package Management System
==============================

Opkg is a lightweight package management system based on Ipkg.

Website: http://code.google.com/p/opkg/
Mailing list: http://groups.google.com/group/opkg-devel
Bug tracker: http://code.google.com/p/opkg/issues/list

The previous website can still be found at:
http://wiki.openmoko.org/wiki/Opkg

https://github.com/shr-project/opkg

For latest version go to http://git.yoctoproject.org/cgit/cgit.cgi/opkg/

## meta-package-manager

CLI providing unifying interface to all package managers.

https://github.com/kdeldycke/meta-package-manager

## sys2/pacman

Pacman 是一个软件包管理器,，作为ArchLinux发行版的一部分，是 Arch Linux 的一大亮点。它将一个简单的二进制包格式和易用的构建系统结合了起来。不管软件包是来自官方的 Arch 库还是用户自己创建，Pacman 都能方便的管理。

## nix包管理工具

Nix是一个强大的包管理工具，它使得包管理更可靠并且可重现。Nix提供了原子级别的升级和回滚操作，多版本安装，多用户包管理，和方便的开发环境设置。

[nix作为包管理工具并用于发布软件的可行性研究](https://xusheng.org/blog/2020/01/06/nix/)

[Nix - Linux的纯功能包管理器](https://www.howtoing.com/nix-package-manager-for-linux)

[src](https://github.com/NixOS/nix)


## bintray-secure-ota

Over-The-Air firmware upgrades for the Internet of Things devices with JFrog @bintray

[src](https://github.com/platformio/bintray-secure-ota)

https://uptane.github.io/

Uptane is an open and secure software update system design which protects software delivered over-the-air to the computerized units of automobiles. The framework can thwart attacks from malicious actors who can compromise servers and networks used to sign and deliver updates. Hence, it is designed to be resilient even to the best efforts of nation state attackers. There are multiple different free open source and closed source implementations available. Uptane is integrated into Automotive Grade Linux, an open source system currently used by many large OEMs, and has also been adopted by a number of U.S. and international manufacturers. Within the next few years, about one-third of new cars on U.S. roads will include Uptane.

https://github.com/uptane/uptane

https://github.com/samlauzon/libuptane

## rauc

RAUC controls the update process on embedded Linux systems. It is both a target application that runs as an update client and a host/target tool that allows you to create, inspect and modify installation artifacts.

https://github.com/rauc/rauc


## Squirrel.Windows

An installation and update framework for Windows desktop apps

atom 的 update.exe 就是这东西

https://github.com/Squirrel/Squirrel.Windows



## hunter

CMake driven cross-platform package manager for C/C++.


https://github.com/cpp-pm/hunter


## cget

 The missing package manager for cmake

 cget brings C/C++ closer to parity with other language's tools (e.g. npm, pip, maven, gradle) by bringing cross-platform module resolution to cmake. cget does this in the way which is most native to each system:

 https://github.com/cget/cget-core

## winget-cli

Windows Package Manager CLI (aka winget)

https://github.com/microsoft/winget-cli

 # 参考

 [我们是否需要通用的 C++ 软件包管理器?](https://www.infoq.cn/article/does-cpp-need-a-universal-package-manager)

 C++ 在软件包管理器上并不存在短板。当前有大量的工具可用，例如 buckaroo 、 cget 、 conan 、 conda 、 cpm 、 cppan 、 hunter 等等，不胜枚举。
