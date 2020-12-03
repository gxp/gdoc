# Runtime

[awesome-wasm-runtimes](https://github.com/appcypher/awesome-wasm-runtimes)

## wasm-micro-runtime

A Bytecode Alliance project

WebAssembly Micro Runtime (WAMR) is a standalone WebAssembly (WASM) runtime with a small footprint. It includes a few parts as below:

  The "iwasm" VM core, supporting WebAssembly interpreter, ahead of time compilation (AoT) and Just-in-Time compilation (JIT)

  The application framework and the supporting API's for the WASM applications

  The dynamic management of the WASM applications


[src](https://github.com/bytecodealliance/wasm-micro-runtime)

[跨越嵌入式到云端的新型容器：WebAssembly Micro Runtime](https://www.infoq.cn/article/PjjSD5W6XzT5X6Fw1ZRc)

[Web Assembly (WASM) on ESP32 with WAMR](https://nick.zoic.org/art/web-assembly-on-esp32-with-wasm-wamr/)


## wasmer

The leading WebAssembly Runtime supporting WASI and Emscripten

Wasmer enables super lightweight containers based on WebAssembly that can run anywhere: from Desktop to the Cloud and IoT devices, and also embedded in any programming language.

Features

    Fast & Safe. Wasmer runs WebAssembly at near-native speed in a fully sandboxed environment.

    Pluggable. Wasmer supports different compilation frameworks to best suit your needs (LLVM, Cranelift...).

    Universal. You can run Wasmer in almost any platform (macOS, Linux and Windows) and chipset.

    Standards compliant. The runtime passes official WebAssembly test suite supporting WASI and Emscripten.

[src](https://github.com/wasmerio/wasmer)

## wasmtime

Standalone JIT-style runtime for WebAssembly, using Cranelift

[src](https://github.com/bytecodealliance/wasmtime)


## WAVM

WebAssembly Virtual Machine

WAVM is a WebAssembly virtual machine, designed for use in non-web applications.


[src](https://github.com/WAVM/WAVM)

## wasm3

The fastest WebAssembly interpreter (and the most universal wasm runtime)

A high performance WebAssembly interpreter written in C.

∼ 8x faster than other known wasm interpreters
∼ 4-5x slower than state of the art wasm JIT engines
∼ 12x slower than native execution

https://github.com/wasm3/wasm3


# Library

## asm-dom

A minimal WebAssembly virtual DOM to build C++ SPA (Single page applications)

https://github.com/mbasso/asm-dom

# Tools

## wabt

The WebAssembly Binary Toolkit

WABT (we pronounce it "wabbit") is a suite of tools for WebAssembly, including:

    wat2wasm: translate from WebAssembly text format to the WebAssembly binary format
    wasm2wat: the inverse of wat2wasm, translate from the binary format back to the text format (also known as a .wat)
    wasm-objdump: print information about a wasm binary. Similiar to objdump.
    wasm-interp: decode and run a WebAssembly binary file using a stack-based interpreter
    wasm-decompile: decompile a wasm binary into readable C-like syntax.
    wat-desugar: parse .wat text form as supported by the spec interpreter (s-expressions, flat syntax, or mixed) and print "canonical" flat format
    wasm2c: convert a WebAssembly binary file to a C source and header
    wasm-strip: remove sections of a WebAssembly binary file
    wasm-validate: validate a file in the WebAssembly binary format
    wast2json: convert a file in the wasm spec test format to a JSON file and associated wasm binary files
    wasm-opcodecnt: count opcode usage for instructions
    spectest-interp: read a Spectest JSON file, and run its tests in the interpreter

These tools are intended for use in (or for development of) toolchains or other systems that want to manipulate WebAssembly files. Unlike the WebAssembly spec interpreter (which is written to be as simple, declarative and "speccy" as possible), they are written in C/C++ and designed for easier integration into other systems. Unlike Binaryen these tools do not aim to provide an optimization platform or a higher-level compiler target; instead they aim for full fidelity and compliance with the spec (e.g. 1:1 round-trips with no changes to instructions).
Online Demos

Wabt has been compiled to JavaScript via emscripten. Some of the functionality is available in the following demos:

    index
    wat2wasm
    wasm2wat


[wabt](https://github.com/WebAssembly/wabt)

# app

## 参考

[WebAssembly: Building Standalone and Dynamic Linking Modules in Windows](https://www.dynamsoft.com/codepool/webassembly-standalone-dynamic-linking-wasm.html)

# 参考

[Faasm 轻量级隔离实现高效的有状态无服务器计算](https://zhuanlan.zhihu.com/p/134152415)

[C/C++面向WebAssembly编程 开源书](https://github.com/3dgen/cppwasm-book)

[awesome-wasm-zh](https://github.com/chai2010/awesome-wasm-zh)

[awesome-wasm-langs](https://github.com/appcypher/awesome-wasm-langs)

[C/C++面向WebAssembly编程](https://cntofu.com/book/150/index.html)

[awesome-wasm](https://github.com/mbasso/awesome-wasm)

[WebAssembly](https://developer.mozilla.org/zh-CN/docs/WebAssembly)

[WebAssembly: Building Standalone and Dynamic Linking Modules in Windows](https://www.dynamsoft.com/codepool/webassembly-standalone-dynamic-linking-wasm.html)

[Wasm 在物联网、云和多媒体领域发展现状](https://cloud.tencent.com/developer/news/614891)
