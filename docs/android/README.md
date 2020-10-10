
# Android 编译生产adb.exe,fastboot.exe的方法

linux下编译adb.exe的应用命令：
make USE_MINGW=y adb
make USE_MINGW=y fastboot


1、执行：apt-get install mingw32
   安装了linux-windows交叉编译环境mingwin

2、执行. build/envsetup.sh
3、执行choosecombo,选择各个参数
   这两步设置了一些编译参数和环境变量，按照你正常编译android的设置即可
4、make USE_MINGW=y adb
5、make USE_MINGW=y fastboot
最后到out/host/windows-x86/bin目录下就能找到你刚刚编译的东西。

[原文链接](https://blog.csdn.net/doublestarts/article/details/18352699)

# 其它

## anbox/anbox

Anbox is a container-based approach to boot a full Android system on a regular GNU/Linux system

https://github.com/anbox/anbox
