# 显示实例化后的代码

* 可以查看汇编代码，好像不能直接生成实例化后的代码。

* clang++ 可以打印实例化后的代码。
    Clang (https://clang.llvm.org/) can pretty-print AST of instantiated template:

    clang++ -Xclang -ast-print -fsyntax-only test.cpp

* 有个在线工具可以查看(试过，挺好的)

    Now there is an on-line tool which does this for you: https://cppinsights.io/ For example, this code 

    https://godbolt.org 可以查看最终生成的代码

[can-we-see-the-template-instantiated-code-by-c-compiler](https://stackoverflow.com/questions/4448094/can-we-see-the-template-instantiated-code-by-c-compiler)

# tools

## Metashell

The goal of this project is to provide an interactive template metaprogramming shell.

Metashell为模板元编程提供了一个类似于Python、Haskell和Erlang shell的交互式shell。它使用Clang来计算元程序。

[online](http://metashell.org/about/demo/index.html)

[website](http://metashell.org/)

[src ](https://github.com/metashell/metashell)

## 参考

[cppinsights](https://cppinsights.io/)

[c++ shell](http://www.cpp.sh/)

[godbolt ](https://godbolt.org)


# 资料

[《C++ Templates 第二版》中文翻译](https://github.com/Walton1128/CPP-Templates-2nd--)

[C++模板元编程实战：一个深度学习框架的初步实现 测试代码](https://github.com/bluealert/MetaNN-book)

[C++模板元编程书籍：《产生式编程：工具，方法和应用》 代码](https://github.com/nanlan2017/book-Generative_Programming)

[中文的C++ Template的教学指南](https://github.com/wuye9036/CppTemplateTutorial)

[打算用中文注释 gcc 里提供的 C++ 标准模板库（STL） ](https://github.com/zhoujianling/annotated-stl)

[C++ Templates 2ed 笔记：C++11/14/17 模板技术 ](https://github.com/downdemo/Cpp-Templates-2ed)

# 参考