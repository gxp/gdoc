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
