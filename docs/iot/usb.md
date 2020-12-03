# ecb_rndis

## Teeny USB

设备栈 Device Stack

    HID class
    MSC 大容量存储设备，U盘。 Mass storage class
    CDC ACM 虚拟串口。 Communication device class, abstract control mode, known as virtual serial port.
    CDC RNDIS 虚拟网口。 Communication device class, remote NDIS
    Vendor 厂商自定义设备。 vendor class

[一个简易的STM32 USB主机和设备协议栈](https://github.com/xtoolbox/TeenyUSB)

## 参考

[stm32 ethernet over usb (rndis + lwip) ](https://github.com/fetisov/lrndis)

# 芯片方案

[SR9900 USB2.0低功耗以太网芯片 4-5元](http://www.corechip-sz.com/productsview.asp?id=24)

 GD32F350G + SR9900  = 5 + 4 元   usbfs

 esp32 12-15元

## SL2.1A 

1.1 元

SL2.1A 是一颗高集成度,高性能,低功耗的 USB2.0 集线器主控芯片；该芯片采用 STT 技术,单电源供电方式，芯片供电电压为 5v, 内部集成 5V 转 3.3V,只需在外部电源添加滤波电容；芯片自带复位电路，低功耗技术让他更加出众。


芯片可以使用外部晶体（建议使用外部晶振，这样更加稳定！），也可以使用内置晶体。如果使用内置晶体，需要将芯片的 XI 输入接地。
 ■ 完美支持 USB2.0 高速(480MHz),USB2.0 全速(12MHz),和低速模式(1.5MHz)
 ■ 集成 12M 晶体振荡器
 ■ 集成 12MHz-to-480MHz PPL(Phase Lock Loop)
 ■ 采用 Single Transaction Translator (STT)技术,是*TT系列中最具成本和效率方案

 ■ 支持自供电到总线供电的自动枚举切换 

[这个16脚的 SL2.1A usb hub芯片大家量产过吗，有没有坑坑？价格不贵，外围还特简单](https://whycan.com/t_3463.html)

[PCB 开源的， 直接打板就行](https://oshwhub.com/li-chuang-zhi-neng-ying-jian-bu/sl2-1a-fang-an-yan-zheng-ban)

[国内首款USB2.0 HUB控制器芯片SL2.2s](https://wenku.baidu.com/view/5bfdec3c182e453610661ed9ad51f01dc28157a9.html)

AU6268-JES-GR  2元