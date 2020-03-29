# Linux虚拟网络设备之bridge(桥)

## 什么是bridge

首先，bridge是一个虚拟网络设备，所以具有网络设备的特征，可以配置IP、MAC地址等；其次，bridge是一个虚拟交换机，和物理交换机有类似的功能。

对于普通的网络设备来说，只有两端，从一端进来的数据会从另一端出去，如物理网卡从外面网络中收到的数据会转发给内核协议栈，而从协议栈过来的数据会转发到外面的物理网络中。

而bridge不同，bridge有多个端口，数据可以从任何端口进来，进来之后从哪个口出去和物理交换机的原理差不多，要看mac地址。

```
sudo ip link add name br0 type bridge
sudo ip link set br0 up

sudo ip link add veth0 type veth peer name veth1
sudo ip addr add 192.168.3.101/24 dev veth0
sudo ip addr add 192.168.3.102/24 dev veth1
sudo ip link set veth0 up
sudo ip link set veth1 up

sudo ip link set dev veth0 master br0
#通过bridge link命令可以看到br0上连接了哪些设备
sudo bridge link

```

[Linux虚拟网络设备之bridge(桥)](https://segmentfault.com/a/1190000009491002)
[Linux 上的基础网络设备详解](https://www.ibm.com/developerworks/cn/linux/1310_xiawc_networkdevice/)
