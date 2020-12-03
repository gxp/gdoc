# 查看udev信息

```
udevadm info -a -p $(udevadm -q path        -n      /dev/hda1)

or

udevadm info -a /dev/hda1
```


# 参考

[详解udev](https://www.cnblogs.com/sopost/archive/2013/01/09/2853200.html)

[udev使用笔记](https://www.jianshu.com/p/dd6cecd7755a)
