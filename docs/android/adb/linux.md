# 确保设备已经连接正常

     首先需要取得root权限，这个没啥说的。然后用lsusb命令列一下所有USB设备，如下图所示：



     这里可以比较清楚的看到有一个设备，ID号是1782：5d04，如果你的系统上有很多USB设备连接你一时看不清楚，可以插拔设备打出ID号对比一下，确保找到这个ID。

      这个ID的前面实际上是厂商编号，后面是产品编号。厂商编号是唯一的，比如htc是0x0bb4，Samsung是0x04e8，Qualcomm是0x05c6，华为则是0x12d1。这里我们看见的0x1782则是展讯的厂商号。
# 在/etc/udev/rules.d/下创建一个配置文件

      这个配置文件将在设备连接时被查询，比如51-android.rules。

      编辑内容如下：

      SUBSYSTEM=="usb",ATTR(idVendor)=="1782", MODE="0666", GROUP="plugdev"

      这里解释一下这几个选项，

      SUBSYSTEM是标识这是一个USB设备，

      ATTR(idVendor)r这一项就是描述厂商的ID号了，

      MODE描述的是访问权限

      GROUP描述成即插即用，不过这里用处不大，写不写都可以

      其实还应该写一个OWNER项，用来指定是哪个用户有权限操作，如果不写则是root（不是所有用户都可以访问），这点需要注意一下，有时候有些同学会在这里被卡住。因为我个人一直使用root权限操作的，所以这里就省略了。

      还有一点，有些时候我们会看到SYSFS{"High Tech Computer Corp."}这样的一个项，这个参数也是设备厂商的意思，貌似以前的官方就是这么写的，当初因为HTC帮Google做的手机，所以一开始用例上写的是“High Tech Computer Corp.”，不过现在官方的示例已经改成ATTR(idVendor)了。



# 给这个文件设置权限

      chmod a+r/etc/udev/rules.d/51-android.rules



# 重启udev

      /etc/init.d/udev restart



# 增加adb_usb.ini文件

      在~/.android目录下增加一个adb_usb.ini文件，这里的路径实际上是各个用户的根目录，如果你需要切换用户的话，记得每个用户下都需要增加这个东东。

      adb_usb.ini文件中写入厂商ID号，和前面不同的是这里需要写上0x的前缀，比如我的展讯手机就是写0x1782

网上搜过不少资料，这一步有些资料上都没提到，估计他们是没有用这步就成功了，但我个人死活不成功，直到增加了这个文件才行，卡了不少时候。



# 重启adb

      adb kill-server

      adb start-server

      adb devices

      这时应该可以看见设备了，下面就可以正常使用adb了

# 参考

[Android Ubuntu平台下ADB驱动的安装](https://blog.csdn.net/sakulafly/article/details/8484538)

[Ubuntu18.04配置ADB调试环境](https://blog.csdn.net/ppggxn/article/details/81709350)
