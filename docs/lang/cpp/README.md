# awesome

https://github.com/fffaraz/awesome-cpp

https://github.com/jobbole/awesome-cpp-cn


# libraries

## The ffead-cpp Framework

https://github.com/sumeetchhetri/ffead-cpp

ffead-cpp is a web-framework, application framework, utilities all bundled into one. It also provides an embedded HTTP/HTT2/Web-Socket compliant high-performance server core. It is a collection of modules all geared towards performing individual roles which together form the cohesive back-bone of ffead-cpp.

It provides a very simple to use and maintain web-framework library with advanced features like Reflection, Dependency Injection (IOC), Inbuilt REST/SOAP support, Security/Authentication features. Moreover implementation for interfacing to caching tools like Memcached/Redis are provided in-built. Database integration/ORM framework (SDORM) solves all major issues with respect to interfacing with SQL/No-SQL database alike.

## 编译

INSTALL文件中有指导。

ubuntu18.04
apt update -yqq && apt install -yqq autoconf-archive gcc g++ cmake unzip libssl-dev uuid-dev odbc-postgresql unixodbc unixodbc-dev libcurl4-openssl-dev libmemcached-dev libmongoc-dev libhiredis-dev wget netcat


使用autoconf编译时

```
./autogen.sh
./configure
```
报错：syntax error near unexpected token AX_CXX_COMPILE_STDCXX

解决方法:->使用上面的指令安装相关依赖

cmake

cmake ..

报错： CMake Error at CMakeLists.txt:113 (message):
  libcuckoo includes not found

解决方法：查看INSTALL文档
备注：libcuckoo安装到/usr, 或 在CMakeLists.txt 111行增加

```
set (CMAKE_REQUIRED_INCLUDES "/usr/local/include")
```

# embedded languages

## ChaiScript

an easy to use embedded scripting language for C++.

http://chaiscript.com/

https://github.com/ChaiScript/ChaiScript




# 参考

[使用 Clang 解析 C++ 头文件实现自动脚本绑定](http://sakishum.github.io/blog/clang-ast-python/)

[LLVM与C++代码的相互调用](https://blog.csdn.net/songchuwang1868/article/details/84977794?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)
