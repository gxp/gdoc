# HTML5桌面应用程序开发

## easy-window

easy-window 是一个旨在简化桌面开发难度的通用窗体，它可以让你使用当前主流的HTML5技术快速地创建Windows桌面应用程序。创作桌面应用，不需要掌握QT，C++，C#，Java那些繁琐的东西，只要会创建网页就可以。同时相较于NW.js和Electron，使用方式更加简洁，体积更小（只有几M）。

https://github.com/lixk/easy-window

## Miniblink

免费小巧开源的浏览器控件，全球最小的基于chromium的浏览器控件，没有之一

https://weolar.github.io/miniblink/


## webview

Tiny cross-platform webview library for C/C++/Golang. Uses WebKit (Gtk/Cocoa) and Edge (Windows) 

[webview](https://github.com/webview/webview)

## DeskGap

A cross-platform desktop app framework based on Node.js and the system webview 

To enable native capabilities while keeping the size down, DeskGap bundles a Node.js runtime and leaves the HTML rendering to the operating system‘s webview.

[src](https://github.com/patr0nus/DeskGap)

[website](deskgap.com/)

## tauri

Build smaller, faster, and more secure desktop applications with a web frontend. 

Tauri is a framework for building tiny, blazing fast binaries for all major desktop platforms. Developers can integrate any front-end framework that compiles to HTML, JS and CSS for building their user interface. The backend of the application is a rust-sourced binary with an API that the front-end can interact with.

The user interface in Tauri apps currently leverages Cocoa/WebKit on macOS, gtk-webkit2 on Linux and MSHTML (IE10/11) or Webkit via Edge on Windows. Tauri uses (and contributes to) the MIT licensed project that you can find at webview and the related webview organization.

[src](https://github.com/tauri-apps/tauri)

## aardio

aardio 专注于桌面软件开发，十余年精益求精，一直保持活跃更新，并且被多年用于生产项目实践，久经测试和锤炼。
aardio 小、轻、快，轻便利索，体积仅5.6MB，aardio虽然小，但提供了大量开源的标准库、扩展库 - 这些库基本都是由纯aardio代码实现，涉及到了桌面编程的方方面面。aardio 中的所有库基本都是由作者一个人编写，所以拥有良好的一致性。aardio为每一个库的每一个接口函数都编写了文档，并且提供了大量的演示范例。aardio 使用流行的类C语法(非常接近Javascript)，在设计中尽可能的避免哗众取宠、标新立异，并且吸取和借鉴流行语言的习惯用法。不少aardio用户都表示只要有一点编程基础，aardio几乎不用特别学习，看几天就会用了，仅仅是复制拼凑范例都能快速开发出不错的软件。

aardio 是属于易用性极强的动态语言、 但也是一种混合语言，可以罕见的、非常方便的操作静态类型，因此可以直接调用C语言、C++等等静态语言的API接口函数( 不需要像VB那样先声明API )，aardio可以支持非常多的API调用约定，例如 stdcall，cdecl，thiscall，fastcall，regparm(n) 等调用约定 aardio 都可以支持。因为 aardio奇特的语言特性，aardio的胶水能力极强，在aardio中可以非常方便的调用C语言、C++、VB、C#、Java、Python、Javascript、Node.Js、Flash ActionScript、PHP、VBScript、NewLISP、Delphi、Go语言 ...... 甚至可以直接嵌入汇编机器码并且转换为普通的aardio函数。aardio 可直接调用、嵌入、交互的第三方编程语言数量非常多，实现这些第三方语言接口的功能模块基本都是开源的（很多只用了极少的代码）。

http://www.aardio.com/

## ecletron


## Cocos

https://github.com/cocos-creator

Cocos Creator is a complete package of game development tools and workflow, including a game engine, resource management, scene editing, game preview, debug and publish one project to multiple plat…


## maxence-charriere/app

A WebAssembly framework to build GUI with Go, HTML and CSS.

https://github.com/maxence-charriere/app

## Yew

什么是 Yew ？

Yew 是一个设计先进的 Rust 框架，目的是使用 WebAssembly 来创建多线程的前端web应用。

    基于组件的框架，可以轻松的创建交互式UI。拥有 React 或 Elm 等框架经验的开发人员在使用Yew时会感到得心应手。

    高性能 ，前端开发者可以轻易的将工作分流至后端来减少 DOM API 的调用，从而达到异常出色的性能。

    支持与Javascript交互 ，允许开发者使用NPM包，并与现有的Javascript应用程序结合。

https://yew.rs/docs/v/zh_cn/

https://github.com/yewstack/yew

## Sass

Sass 是一种 CSS 的预编译语言。它提供了 变量（variables）、嵌套（nested rules）、 混合（mixins）、 函数（functions）等功能，并且完全兼容 CSS 语法。Sass 能够帮助复杂的样式表更有条理， 并且易于在项目内部或跨项目共享设计。


## azul

https://azul.rs/

A free, functional, immediate-mode GUI framework for rapid development of desktop applications written in Rust, supported by the Mozilla WebRender rendering engine

## neutralinojs(c++)

Neutralino is a lightweight and portable application development framework. It lets you develop cross-platform applications using JavaScript/TypeScript, HTML and CSS.



[src](https://github.com/neutralinojs/neutralinojs)


## tauri(rust)

Tauri is a framework for building tiny, blazing fast binaries for all major desktop platforms. Developers can integrate any front-end framework that compiles to HTML, JS and CSS for building their user interface. The backend of the application is a rust-sourced binary with an API that the front-end can interact with.

[src](https://github.com/tauri-apps/tauri)

## orbtk(rust)

The Orbital Widget Toolkit is a cross-platform (G)UI toolkit for building scalable user interfaces with the programming language Rust. It's based on the Entity Component System Pattern and provides a functional Reactive-like API.

Web client or native ui

https://github.com/redox-os/orbtk

## druid(rust)

Druid is an experimental Rust-native UI toolkit. Its main goal is to offer a polished user experience. There are many factors to this goal, including performance, a rich palette of interactions (hence a widget library to support them), and playing well with the native platform. See the goals section for more details.

https://github.com/linebender/druid

## moxie(rust)

a lightweight platform-agnostic interactive runtime, written in rust, aiming to empower anyone to build efficient and robust interactive software for humans.

https://moxie.rs

https://github.com/anp/moxie

## iced(rust)

A cross-platform GUI library for Rust focused on simplicity and type-safety. Inspired by Elm.

Cross-platform support (Windows, macOS, Linux, and the Web)

https://github.com/hecrj/iced

## asm-dom

A minimal WebAssembly virtual DOM to build C++ SPA (Single page applications)

asm-dom is a minimal WebAssembly virtual DOM to build C++ SPA (Single page applications). You can write an entire SPA in C++ and compile it to WebAssembly (or asmjs as fallback) using Emscripten, asm-dom will call DOM APIs for you.

https://github.com/mbasso/asm-dom


## nodegui

[src](https://github.com/nodegui/nodegui)

[用NodeGUI开发比electron更好性能的app ](https://bbs.deepin.org/post/182172#mod=viewthread&tid=182172)

[使用Node构建桌面GUI](https://blog.csdn.net/junmoxi/article/details/98251812)

[使用packer 打包nodegui 应用](https://www.cnblogs.com/rongfengliang/p/11488802.html)


## ftr

A GUI typesetting display engine and cross platform GUI application development framework based on NodeJS/OpenGL 

ftr is a cross-platform (Android/iOS) front-end development framework. The core code is written in C++. The bottom layer is based on OpenGL drawing. The upper layer implements a streamlined typesetting engine and a JS/JSX running environment. The goal is to develop GUI applications on this basis, which can take both development speed and operation efficiency into account.

    Only iOS and Android systems are supported for the time being, this does not include AndroidTV, because TV applications are very different from mobile applications

    From here, Go API Index can go to API Documents Index


[src](https://github.com/louis-tru/ftr)

[开源跨平台移动项目Ngui【入门】](https://zhuanlan.zhihu.com/p/31312344)


## react native

A framework for building native Windows(10) apps with React. 

[react-native-windows](https://github.com/Microsoft/react-native-windows)

## Neutralinojs

Build lightweight cross-platform desktop apps with JavaScript, HTML, and CSS

使用 webview技术

[website](https://neutralino.js.org/)


## boden

Purely native C++ cross-platform GUI framework for Android and iOS development. https://www.boden.io

https://github.com/AshampooSystems/boden

## asm-dom

A minimal WebAssembly virtual DOM to build C++ SPA (Single page applications) 

https://github.com/mbasso/asm-dom


## uni-app与framework7+cordova

对比下uni-app与framework7+cordova的优缺点：

framework7比uni-app强的地方

    提供了一套完整的ui，ui非常漂亮而且整体风格统一，动画组件丰富。虽然uni-app的插件库丰富，但都是各个大神各自为战写出来但组件，确少全局性和整体性。如果您公司有大神坐镇这就不是问题了。当然你也可以购买graceui 来
    framework7做出的应用可以根据ios和android系统的不同，有不同的显示风格和动画风格。uni-app没有考虑这个差异。
    f7提供了黑色皮肤和浅色皮肤。uni-app没有提供皮肤切换的功能。
    f7为强封装，许多常用组件都封装了，调用都时候，几句话就实现了。uni可以算弱封装，调用都时候要好几个组件拼凑，如果前端没有高手都话，做起来会稍微显得吃力。

除了这俩点外，我找不出f7比uni-app强的地方了。

uni-app比f7强的地方：

    uni跟vue的整合是无缝的，而f7虽然提供了f7-vue，但是个不伦不类的鸡肋，用起来非常痛苦，而且功能也没有f7-html强大。
    uni结合原生要方便多了，虽然f7+cordova也可以结合原生，但基本都是靠大脑想象没法看到相应效果，只能边开发边通过调试器来查看。
    uni-app的文档是中文，f7基本都是英文，这个为啥是优势，大家是懂的。
    uni-app的编程思维是中国化的，灵活性高，而且想到了你需要的各个方面。f7基本就靠大家自己研究了。
    uni-app跟中国各大生态平台的整合，这个就不用介绍了，这也是uni的最大卖点了。
    uni-app打包要方便，而f7+cordova打包都需要自己去配置，自己摸索。出个问题还没地方可以问。

[uni-app（一）uni-app与framework7+cordova选择对比](https://blog.csdn.net/weiyongliang_813/article/details/108649662)

[uni-app website](https://uniapp.dcloud.io/)

## Flutter

使用drat语言，可以编译到 windows android ios linux web(javascript).

[Flutter 实战](https://flutterchina.club/)

[flutter.cn 中文文档 官方？](https://flutter.cn)

[dartcn](https://www.dartcn.com/)

[dart.cn 中文文档 官方？](https://dart.cn/get-dart)

[在线测试](https://dartpad.cn/)

[U4 内核团队再出发，打造全新 Flutter 渲染引擎 —— Hummer](https://zhuanlan.zhihu.com/p/196631839)

[flutter 开发者帮助 APP，包含 flutter 常用 140+ 组件的demo 演示与中文文档 ](https://github.com/alibaba/flutter-go)

[Flutter桌面应用开发：创建并运行桌面应用](https://www.jianshu.com/p/6f7c9f2acfff)

[清华Flutter 镜像安装帮助](https://mirrors.tuna.tsinghua.edu.cn/help/flutter/)

[在中国网络环境下使用 Flutter](https://flutter.cn/community/china)

[Flutter 桌面支持](https://flutter.cn/desktop)

[开始使用 Flutter 构建 Windows 桌面应用吧！](https://blog.csdn.net/jILRvRTrc/article/details/109088490)

[使用 Flutter 构建 Web 应用](https://flutter.cn/docs/get-started/web)

[Go Flutter Desktop (一) 初探](https://blog.csdn.net/qq_28478281/article/details/95615208)

[go-flutter - A package that brings Flutter to the desktop](https://github.com/go-flutter-desktop/go-flutter)

[Flutter 开发桌面应用——迁移已有应用到桌面版 flutter-desktop 对比 go-flutter](https://www.jianshu.com/p/fcf115868768)

[Flutter + Kotlin Multiplatform, Write Once Run Anywhere](https://www.jianshu.com/p/0f93ab9182de)


## Kotlin Multiplatform

Support for multiplatform programming is one of Kotlin’s key benefits. It reduces time spent writing and maintaining the same code for different platforms while retaining the flexibility and benefits of native programming.

[website](https://kotlinlang.org/docs/reference/multiplatform.html)

[Kotlin Multiplatform - 下一代全平台开发技术](https://www.jianshu.com/p/80eddf62a99a)

# 参考

[浅谈前端八大UI库-2020-05-25](https://blog.csdn.net/u011068996/article/details/106339790)

[uniapp与flutter，跨平台解决方案你该如何选择](https://zhuanlan.zhihu.com/p/55466963)
