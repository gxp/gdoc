# linux usb子系统.调试方法

linux kernel usb调试方法：

*  sysfs/debugfs
*  usbmon
*  Dynamic debug interface
*  Tracepoints

调试信息文件路径：

ls  /sys/bus/usb/devices/

cat  /sys/kernel/debug/usb/devices   
cat  /proc/bus/input/devices  # 查找系统的usb输入设备

## 工具抓包分析：

usbmon源码路径 Kernel\drivers\usb\mon

usbmon in lowercase refers to a facility inkernel which is used to collect traces of I/O on the USB bus.

usbmon的相关命令行：

```
$ sudo mount -t debugfs none_debugs /sys/kernel/debug
$ sudo modprobe usbmon
#Verify that bus sockets are present. 我的电脑有3个usb插口。可以看到每个插口有usbmon
$ sudo ls  /sys/kernel/debug/usb/usbmon         
0s  0u	1s  1t	1u  2s	2t  2u

$ls /dev | grep usb
usbmon0  usbmon1  usbmon2
$sudo tcpdump -i usbmon1 -w usbmon11.pcap  

```

## Protocol  Analyzer软件(USB  tethering和vusb-analyzer)

ubuntu vusb-analyzer安装

$sudoapt-get install vusb-analyzer



vusb-analyzer运行

$sudo cat /sys/kernel/debug/usb/usbmon/1u >usbmon12.mon
$vusb-analyzer  usbmon12.mon


## dmesg是用于检测和控制内核环缓冲，它可以用来帮助用户了解系统的信息。

列出日志

# dmesg | less

查看usb相关的信息

# dmesg | grep -i usb

输出最新20行日志

# dmesg | tail -20

清空dmesg缓存日志

# dmesg -c

查看实时日志

# watch "dmesg | tail -20"


[linux usb子系统.调试方法](https://blog.csdn.net/cutter2002/article/details/69808345)
