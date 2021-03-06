# c++ 全局变量初始化的一点总结

注意：本文所说的全局变量指的是 variables with static storage，措词来自 c++ 的语言标准文档。

## 什么时候初始化

根据 C++ 标准，全局变量的初始化要在 main 函数执行前完成，常识无疑，但是这个说法有点含糊，main 函数执行前到底具体是什么时候呢？是编译时还是运行时？答案是既有编译时，也可能会有运行时(seriously), 从语言的层面来说，全局变量的初始化可以划分为以下两个阶段（c++11 N3690 3.6.2)：

    static initialization: 静态初始化指的是用常量来对变量进行初始化,主要包括 zero initialization 和 const initialization，静态初始化在程序加载的过程中完成，对简单类型(内建类型，POD等)来说，从具体实现上看，zero initialization 的变量会被保存在 bss 段，const initialization 的变量则放在 data 段内，程序加载即可完成初始化，这和 c 语言里的全局变量初始化基本是一致的。

    dynamic initialization：动态初始化主要是指需要经过函数调用才能完成的初始化，比如说：int a = foo()，或者是复杂类型（类）的初始化（需要调用构造函数）等。这些变量的初始化会在 main 函数执行前由运行时调用相应的代码从而得以进行(函数内的 static 变量除外)。

需要明确的是：静态初始化执行先于动态初始化！ 只有当所有静态初始化执行完毕，动态初始化才会执行。显然，这样的设计是很直观的，能静态初始化的变量，它的初始值都是在编译时就能确定，因此可以直接 hard code 到生成的代码里，而动态初始化需要在运行时执行相应的动作才能进行，因此，静态初始化先于动态初始化是必然的。

## 初始化的顺序

对于出现在同一个编译单元内的全局变量来说，它们初始化的顺序与他们声明的顺序是一致的（销毁的顺序则反过来），而对于不同编译单元间的全局变量，c++ 标准并没有明确规定它们之间的初始化（销毁）顺序应该怎样，因此实现上完全由编译器自己决定，一个比较普遍的认识是：不同编译单元间的全局变量的初始化顺序是不固定的，哪怕对同一个编译器，同一份代码来说，任意两次编译的结果都有可能不一样[1]。

因此，一个很自然的问题就是，如果不同编译单元间的全局变量相互引用了怎么办？

当然，最好的解决方法是尽可能的避免这种情况(防治胜于治疗嘛)，因为一般来说，如果出现了全局变量引用全局变量的窘况，那多半是程序本身的设计出了问题，此时最应该做的是回头重新思考和修改程序的结构与实现，而不是急着穷尽技巧来给错误的设计打补丁。

## 几个技巧

好吧，我承认总有那么一些特殊的情况，是需要我们来处理这种在全局变量的初始化函数里竟然引用了别的地方的全局变量的情况，比如说在全局变量的初始化函数里调用了 cout, cerr 等(假设是用来打 log, 注意 cout 是标准库里定义的一个全局变量)[2]，那么标准库是怎样保证 cout 在被使用前就被初始化了呢？ 有如下几个技巧可以介绍一下。

....

[原文](https://www.cnblogs.com/catch/p/4314256.html)
