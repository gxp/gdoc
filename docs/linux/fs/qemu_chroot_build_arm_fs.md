# qemu+chroot构建arm aarch64虚拟机


在X86环境下构建出arm虚拟机可以模拟arm环境进行开发、在arm linux的文件系统中安装相应的库文件，编译arm版本等。

简单介绍下在X86环境下构建ARM虚拟机的步骤。

 
1、x86环境安装qemu-user-static

sudo apt-get install qemu-user-static
2、准备arm linux根文件系统

arm linux根文件系统可以直接下载干净的版本

或者从运行的arm单板上进行备份获取。

arm单板上备份根文件系统命令：

sudo tar -cvpzf rootfs.tgz --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/rootfs.tgz /

解压根文件系统命令：

tar -xvpfz rootfs.tgz -C ./

或者使用qemu-debootstrap构建

sudo qemu-debootstrap --verbose --arch=arm64 --variant=buildd xenial  ubuntu_arm64_xenial  http://mirrors.ustc.edu.cn/ubuntu-ports

https://www.cnblogs.com/lianghong881018/p/10336839.html
https://www.cnblogs.com/aaronLinux/p/6886163.html

3、构建虚拟机

创建rootfs目录，在rootfs下执行根文件系统解压命令，解压完成后，copy qemu执行命令到arm文件系统中

sudo cp /usr/bin/qemu-arm-static usr/bin/
sudo cp /usr/bin/qemu-aarch64-static usr/bin/

在rootfs录下创建proc、sys、host目录

在rootfs所在目录下创建ch-mount.sh文件
ch-mount.sh

执行ch-mount.sh，创建虚拟机

sudo ./ch-mount.sh -m rootfs/

arm虚拟机准备完毕，可以在虚拟的arm环境上进行相应的操作，创建用户、编译arm版本、......
4、卸载虚拟机

在虚拟机环境中执行exit退出。然后执行命令卸载挂载的相关文件。

 

sudo ./ch-mount.sh -u rootfs/

 
