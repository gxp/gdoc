# rr

rr is a lightweight tool for recording, replaying and debugging execution of applications (trees of processes and threads). Debugging extends gdb with very efficient reverse-execution, which in combination with standard gdb/x86 features like hardware data watchpoints, makes debugging much more fun. More information about the project, including instructions on how to install, run, and build rr, is at https://rr-project.org. The best technical overview is currently the paper Engineering Record And Replay For Deployability: Extended Technical Report.

[src](https://github.com/mozilla/rr)


# C++ Insights

可以探查编译器做了什么

C++ Insights - See your source code with the eyes of a compiler 

C++ Insights is a clang-based tool which does a source to source transformation. Its goal is it to make things visible which normally, and intentionally, happen behind the scenes. It's about the magic the compiler does for us to make things work.

译文：c++ Insights是一个基于clang的工具，它进行源代码到源代码的转换。它的目标是使那些通常或有意地发生在幕后的事情变得可见。它是关于编译器为我们做的魔术，使事情正常工作。

[src](https://github.com/andreasfertig/cppinsights)

[online](https://cppinsights.io/)


# 参考

[编译器自带的调试神器sanitizers](https://zhuanlan.zhihu.com/p/257939964)