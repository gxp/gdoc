# 启动应用

1. 带桌面环境的自动启动

该方法由桌面去启动qt程序，这里说的桌面指窗口管理器如xface、gnome、kde等。
1.1Ubuntu

以Ubuntu 图形界面作为例子（这里使用Ubuntu16.04，基于gnome开发）如下：

在当前用户home下创建autostart目录:

mkdir -p ~/.config/autostart


创建一个**.desktop的文件如下:

cat > ~/.config/autostart/Qt_test.desktop << EOF
[Desktop Entry] 
Type=Application
Exec=/home/Qt_test
EOF

该方法可以达到自动启动应用程序的效果，但在一些比如嵌入式应用环境，Ubuntu桌面环境也不需要的时候该方法就不适合,原因在于Ubuntu桌面环境太庞大，占用资源过多。

1.2 openbox

Openbox 是一个轻量级、可高度定制以及支持大量标准的窗口管理器，几乎无冗余软件，仅是一个窗口管理器，比较适合嵌入式应用环境。让登录管理器来启动openbox、QT应用程序，或者Openbox启动QT应用程序。

2.1 窗口管理器

我们熟悉的GNOME、KDE、Xface…;使用这些桌面环境应该尽量使用对应的登录管理器来启动。
2.2 登录管理器

窗口管理和X11 需要登录管理器来启动：

​ GDM-GNOME登录管理器；

​ SDDM - 基于QML的显示管理器和KDM的后继者; 推荐用于 Plasma和 LXQt；

​ XDM - X显示管理器，支持XDMCP；

​ LightDM - 跨桌面显示管理器，可以使用任何工具包中编写的各种前端，Ubuntu16.04默认使用该管理器。
这些桌面管理器均可安装，安装后只需用systemd 启动该服即可，例如在Ubuntu16.04上安装sddm,并启用相应的systemd服务：

sudo apt-get install sddm


然后设置开机启动，当然需要先关闭自带的LightDM服务：

sudo systemctl disable lightdm.service
sudo systemctl enable sddm.service


启用sddm后/etc/systemd/system/display-manager.service应该链接到/usr/lib/systemd/system/sddm.service

2.2.1 没有窗口管理启动应用程序

登录管理器如何启动窗口管理的？

大多数登录管理器会从/usr/share/xsessions/读取可用的.desktop文件,在安装各种窗口管理器时会在/usr/share/xsessions/下生成对应的desktop文件，比如ubuntu自带的ubuntu.desktop文件,它的配置如下：

[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=untiy
Icon=
Type=Application
DesktopNames=Unity
X-Ubuntu-Gettext-Domain=gnome-session-3.0

可以在没有任何桌面或窗口管理的情况下启动应用程序，例如要启动google-chrome只需在/usr/share/xsessions/下创建web-browser.desktop文件如下：

[Desktop Entry]
Name=Web Browser
Comment=Use a web browser as your session
Exec=/usr/bin/google-chrome --auto-launch-at-startup
TryExec=/usr/bin/google-chrome --auto-launch-at-startup
Icon=google-chrome
Type=Application

2.2.2 登录管理器自动登录配置

2.3.3 没有窗口管理器启动应用程序

[ubuntu配置图形应用自启动的几种方法](https://blog.csdn.net/qq_22654551/article/details/106203114)


# 嵌入式 Linux 知识库 (eLinux.org)

[中文翻译](https://github.com/unicornx/elinux/blob/master/zh/README.md)


# 参考

[手机就是开发板](https://aggresss.blog.csdn.net/article/details/54897377)

[路由器就是开发板](https://blog.csdn.net/aggresss/article/details/52753098)

[显卡就是开发板](https://blog.csdn.net/aggresss/article/details/79724502)

[虚拟机就是开发板](https://blog.csdn.net/aggresss/category_6706568.html)
