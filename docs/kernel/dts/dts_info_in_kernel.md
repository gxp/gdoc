# 编译设备树

设备树有三种形式：
- 文本文件 (.dts) - 源
- 二进制对象 (.dtb) - 目标码
- Linux系统中/proc/device-tree目录 - 调试和逆向信息

启用/proc/device-tree目录需要打开配置CONFIG_PROC_DEVICETREE:

`    Device Drivers --->
    Device Tree and Open Firmware support --->
    [*] Support for device tree in /proc
`

对于设备树，我们一般的使用流程是：编辑DTS文件，然后用一个工具将其编译成DTB文件，这个工具就在Linux内核源码scripts/dtc/目录下。

设备树编译器也可以单独下载并编译：

$ git clone git://www.jdl.com/software/dtc.git dtc
$ cd dtc
$ make

但是下文的描述都使用内核原码中的dtc工具。

设备树的语法在这里描述。注意这种语言并不作任何执行操作，不像XML，这只是一种组织数据的语法。一些架构有自动产生设备树的工具，来自于XPS项目。但目前对于Zynq EPP平台还没有此工具。

DTS编译为DTB：

`$ scripts/dtc/dtc -I dts -O dtb -o /path/to/my-tree.dtb /path/to/my-tree.dts`

这样就创建了my-tree.dtb二进制文件。dtc是主机上的一个程序。如果内核没有编译过，则先需要编译好DTS编译器：配置内核，也可以复制一份已有的配置文件到内核根目录下的.config。如下：

$ `make ARCH=arm digilent_zed_defconfig`

生成DTS编译器：

$ `make ARCH=arm scripts`

dtc也可以从一个DTB文件或/proc/device-tree文件系统反编译。例如从DTB反编译：

$ `scripts/dtc/dtc -I dtb -O dts -o /path/to/fromdtb.dts /path/to/booted_with_this.dtb`

生成的dts文件仍然可以被用来生成dtb。但最好还是使用最初的DTS文件，因为一些参考标签在反编译的DTS文件中显示为数字。

从运行中的内核生成DTS文件：

`# scripts/dtc/dtc -I fs -O dts -o ~/effective.dts /proc/device-tree/`


# 在系统运行时，查看设备树信息

可以在/proc/device-tree 查看device tree中的具体内容，在有些内核中，proc/device-tree 是链接到sys/firmware/devicetree/base的。



If dtc is available on your platform (else, install the device-tree-compiler package), you can use:

dtc -I fs /sys/firmware/devicetree/base

查看二进制数据时，使用hexdump:

hexdump -C '/proc/device-tree/#size-cells'

可直接使用cat查看文本内容:

cat '/proc/device-tree/axi@0/compatible'

# 在系统运行时编辑设备树(Edit device tree at run time)

Introduction

Sometimes, when we are working on an embedded device adding a new module or debugging an existing one, we need to constantly modify the device tree. This wiki page explains an easy way of doing it from the same target board without the need of going to the source code. For this purpose we'll use a tool called devocet-tree-compitler
Using the tool

Install the tool

sudo apt-get install device-tree-compiler

After this should have these tools installed: fdtdump fdtget fdtput
Dumping the dtb

To dump the dtb you can use fdtdump as follows:

`fdtdump [options] <file>`

For instance:

`fdtdump /boot/tegra186-quill-p3310-1000-c03-00-base.dtb`

Getting a property

To get a property you can use fdtget as follows:

`fdtget <options> <dt file> [<node> <property>]...`

For instance, to get the clock frequency for i2c0:

`fdtget /boot/tegra186-quill-p3310-1000-c03-00-base.dtb i2c0 clock-frequency`

Setting a property

To set a property you can use fdtput as follows:

`fdtput <options> <dt file> <node> <property> [<value>...]`

So for example, to set the clock frequency for i2c0:

`sudo fdtput -t i /boot/tegra186-quill-p3310-1000-c03-00-base.dtb i2c0 clock-frequency 100000`

After this you should restart your board for the changes to take effect.
