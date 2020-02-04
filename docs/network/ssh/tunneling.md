# 端口转发-隧道

https://www.ibm.com/developerworks/cn/linux/l-cn-sshforward/index.html

## 本地转发

```
ssh -L <local port>:<remote host>:<remote port> <SSH hostname>
```

## 远程转发

```
ssh -R <local port>:<remote host>:<remote port> <SSH hostname>
```
