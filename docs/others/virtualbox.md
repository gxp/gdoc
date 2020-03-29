# 在VirtualBox 6.1里面打开嵌套 VT-x/AMD-V 功能

原来需要用VBoxManage 命令行的方式来打开这个选项：

```
VBoxManage.exe list vms

VBoxManage.exe modifyvm "Ubuntu" --nested-hw-virt on
```

[参考](https://blog.csdn.net/holderlinzhang/article/details/104260531)
[VirtualBox 无法启用嵌套 VT-x/AMD-V](http://www.linuxcoming.com/blog/2019/09/03/virtualbox_can_not_enable_nest_vt_x.html)
