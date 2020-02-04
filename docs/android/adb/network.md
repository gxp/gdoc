# 通过网络调试

## 连接

```
adb connect android-dev-ip:5555

```


## Android手机启动adbd

需要root

```
su
setprop service.adb.tcp.port 5555
stop adbd
start adbd

```

## 参考

https://www.cnblogs.com/shengs/p/10177801.html
