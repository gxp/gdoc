# wxFormBuilder

wxFormBuilder是一款非常好用的界面编辑设计工具，用于生成跨平台编译代码，能够快速搭建GUI开发环境，wxFormBuilder支持快速生成C++，python, Lua 等代码和 XRC 资源文件，搭建高效的带有GUI界面编辑器的开发环境。欢迎大家前来下载使用。

备注:
wxWidgets  发布库比较小

## 参考

[github](https://github.com/wxFormBuilder/wxFormBuilder)

[痞子衡嵌入式：极易上手的可视化wxPython GUI构建工具(wxFormBuilder)](https://www.cnblogs.com/henjay724/p/9426966.html)

[wxFormBuilder python图形界面设计工具安装与使用图文教程](https://www.jb51.net/softjc/696020.html)

# V UI

V UI is a cross-platform UI toolkit written in the V programming language for Windows, macOS, Linux, and soon Android, iOS and the web (JS/WASM). V UI uses native widgets on Windows and macOS, on all other platforms the widgets are drawn by V UI. Right now only the non-native widgets are available.

[src](https://github.com/vlang/ui)


# CopperSpice

CopperSpice is a set of individual libraries which can be used to develop cross platform software applications in C++. It is a totally open source project released under the LGPL V2.1 license and was initially derived from the Qt framework. Over the last several years CopperSpice has completely diverged, with a goal of providing a first class GUI library to unite the C++ community.

[src](https://github.com/copperspice/copperspice)


# yue

A library for creating native cross-platform GUI apps.

[src](https://github.com/yue)


# asm-dom

A minimal WebAssembly virtual DOM to build C++ SPA (Single page applications)

asm-dom is a minimal WebAssembly virtual DOM to build C++ SPA (Single page applications). You can write an entire SPA in C++ and compile it to WebAssembly (or asmjs as fallback) using Emscripten, asm-dom will call DOM APIs for you.

https://github.com/mbasso/asm-dom

# GuiLite

Small: Just under 5,000 lines of C++ and header-only: GuiLite.h

zapFast: Render a GUI within one invocation, independent of any OS or 3rd party library

syringeEmbeddable: Runs inside Qt/MFC/Winform/Cocoa/Web - Keep legacy Qt/MFC code reusable

gear️Hardware Minimum Requirements:


    Supported OSes: iOS/macOS/WathOS, Android, Linux, Windows, RTOS... or MCU without OS
    Supported languages: C/C++, Swift, Java, Javascript, C#, Golang...
    Supported 3rd party libraries: Qt, MFC, Winforms, CoCoa...


[src](https://github.com/idea4good/GuiLite)

# qml

## qmlweb

A QML engine in a web browser. Current state: fixing things… 

This project aims at bringing the power of QML to the web browser. Here's a sample of how QML looks like:

https://github.com/qmlweb/qmlweb


Related efforts

### Qt Quick WebGL streaming

That will allow users to run the main Qt process on the server and render on HTML clients through WebGL. Qt WebGL streaming requires one application process on server per each client — only the painting is delegated to the client.

The usecase differs significantly from QmlWeb, as QmlWeb runs all code on the clients, attempting to reuse browser APIs as much as possible to provide better integration. No server-side code is needed, server provides static files.

### PureQml framework

PureQml aims to implement a language close to original QML, but it does not target 100% compatibility with Qt QML, unlike QmlWeb. They also provide a framework based on their language and target support for a great variety of platforms.

### Qt/QML + Emscripten

Transplitting all the required Qt/QML libraries to JS/WebAssembley and rendering everything to Canvas provides the best possible compatibility with upstream Qt. That comes at a price, though — the runtime is pretty big, and that approach does not allow to reuse many existing browser APIs and components.

### Qt for WebAssembly port

Similar as the above «Qt/QML + Emscripten», but more up to date. Upstream issue: QTBUG-63917.

Examples at https://msorvig.github.io/qt-webassembly-examples/.

## qmlcore

QML to Javascript/HTML5 translator, both for mobile and desktop targets 

QmlCore is a simple set of tools we (a small team of QML advocates) use since years to simplify the development of HTML5 UIs for both mobile and desktop devices. It was designed with the original QML in mind, while it's not 100% compatible and improved in some aspects. The main concepts are the same though, so if you're familiar with original QML, you could start right away.

[qmlcore](https://github.com/pureqml/qmlcore)

# 参考

[rust gui list ](https://lib.rs/gui)
