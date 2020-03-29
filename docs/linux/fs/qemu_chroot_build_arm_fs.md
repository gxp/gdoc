# qemu+chroot构建arm aarch64虚拟机


在X86环境下构建出arm虚拟机可以模拟arm环境进行开发、在arm linux的文件系统中安装相应的库文件，编译arm版本等。

简单介绍下在X86环境下构建ARM虚拟机的步骤。


# 1、x86环境安装qemu-user-static

sudo apt-get install qemu-user-static

# 2、准备arm linux根文件系统

arm linux根文件系统可以直接下载干净的版本

或者从运行的arm单板上进行备份获取。

arm单板上备份根文件系统命令：
```
sudo tar -cvpzf rootfs.tgz --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/rootfs.tgz /
```
解压根文件系统命令：
```
tar -xvpfz rootfs.tgz -C ./
```
或者使用qemu-debootstrap构建
```
sudo qemu-debootstrap --verbose --arch=arm64 --variant=buildd xenial  ubuntu_arm64_xenial
```
http://mirrors.ustc.edu.cn/ubuntu-ports

https://www.cnblogs.com/lianghong881018/p/10336839.html
https://www.cnblogs.com/aaronLinux/p/6886163.html

# 3、构建虚拟机

创建rootfs目录，在rootfs下执行根文件系统解压命令，解压完成后，copy qemu执行命令到arm文件系统中

sudo cp /usr/bin/qemu-arm-static usr/bin/
sudo cp /usr/bin/qemu-aarch64-static usr/bin/

在rootfs录下创建proc、sys、host目录

在rootfs所在目录下创建ch-mount.sh文件

```
#!/bin/bash

function mnt() {
    echo "MOUNTING"
    sudo mount -t proc /proc ${2}proc
    sudo mount -t sysfs /sys ${2}sys    
    sudo mount -o bind /dev ${2}dev
    sudo mount -o bind /run ${2}run
    sudo mount --bind / ${2}host
    #sudo mount -vt tmpfs shm ${2}dev/shm
    #sudo mount -t /dev/shm ${2}dev/shm
    sudo chroot ${2}
}

function umnt() {
    echo "UNMOUNTING"
    sudo umount ${2}proc
    sudo umount ${2}sys
    #sudo umount ${2}dev/shm
    sudo umount ${2}dev
    sudo umount ${2}run
    sudo umount ${2}host
}


if [ "$1" == "-m" ] && [ -n "$2" ] ;
then
    mnt $1 $2
elif [ "$1" == "-u" ] && [ -n "$2" ];
then
    umnt $1 $2
else
    echo ""
    echo "Either 1'st, 2'nd or both parameters were missing"
    echo ""
    echo "1'st parameter can be one of these: -m(mount) OR -u(umount)"
    echo "2'nd parameter is the full path of rootfs directory(with trailing '/')"
    echo ""
    echo "For example: ch-mount -m /media/sdcard/"
    echo ""
    echo 1st parameter : ${1}
    echo 2nd parameter : ${2}
fi  
```

执行ch-mount.sh，创建虚拟机

sudo ./ch-mount.sh -m rootfs/

arm虚拟机准备完毕，可以在虚拟的arm环境上进行相应的操作，创建用户、编译arm版本、......

# 4、卸载虚拟机

在虚拟机环境中执行exit退出。然后执行命令卸载挂载的相关文件。



sudo ./ch-mount.sh -u rootfs/


# 可能的问题

chroot: failed to run command ‘/bin/bash’: Exec format error

1. 确认是否安装 binfmt-support
2. 重启 binfmt-support服务

You can also look in /proc/sys/fs/binfmt_misc if there exists a file qemu-arm. If not restart the service binfmt_support.

update-binfmts --display 显示系统当前支持的二进制格式.
