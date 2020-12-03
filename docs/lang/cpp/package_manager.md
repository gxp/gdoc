# conan

Conan是一个可以帮C/C++进行依赖管理的包管理器。它是免费、开源、跨平台的。目前支持Windows, Linux, OSX, FreeBSD, Solaris等平台。同时也支持嵌入式、移动端（IOS，Andriod）、或者直接基于裸机之上的目标程序开发。它当前支持各种构件系统，例如CMake，Visual Studio（MSBuild），Makefiles，Scons等等。

Conan是分布式的，它允许运行自己私有的包管理器托管自己私有的包和二进制文件。Conan是基于二进制管理的，它可以为包生成各种不同配置、不同体系架构或者编译器版本的二进制文件。

Conan相对比较成熟和稳定，有一个全职团队在维护它。Conan保证前向兼容，社区相对成熟，从开源到商业公司都有使用。它有一个官方的中央仓 ConanCenter。

Conan的源码遵循 MIT license，位于github : https://github.com/conan-io/conan。

[中文Conan Tutorial](https://ccup.github.io/conan-docs-zh/)

## 增加Bincrafters公共仓库

conan remote add bincrafters https://api.bintray.com/conan/bincrafters/public-conan

[使用 Bincrafters Conan公共仓库](https://bincrafters.github.io/2017/06/06/using-bincrafters-conan-repository/)

## conan_server

启动 :

conan_server

增加remote库:

conan remote add local http://localhost:9300

conan search -r local

增加 remote 时，地址不能是0.0.0.0,  不用加 /v1

上传包 conan upload package/version -r local

https://ccup.github.io/conan-docs-zh/06-uploading-packages.html

https://docs.conan.io/en/latest/uploading_packages/running_your_server.html

## 参考

[conan使用(二)--创建私有仓库](https://www.cnblogs.com/xl2432/p/11896466.html)


# hunter

CMake driven cross-platform package manager for C/C++. Linux, Windows, macOS, iOS, Android, Raspberry Pi, etc.

https://github.com/cpp-pm/hunter

# conda

Conda 是一个开源的软件包管理系统和环境管理系统，用于安装多个版本的软件包及其依赖关系，并在它们之间轻松切换。

Package, dependency and environment management for any language—Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, FORTRAN, and more.

[conda的安装与使用（2020-08-10更新）](https://www.jianshu.com/p/edaa744ea47d)


# 参考

[打包一沓开源的 C/C++ 包管理工具送给你！](https://www.cnblogs.com/xueweihan/p/11414263.html)

[Nexus安装、使用说明、问题总结](https://www.cnblogs.com/bingyeh/p/5913486.html)