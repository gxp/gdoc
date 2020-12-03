## 备注

eeprom 比较便宜、带保护 ID？ 可存储参数、SN、密钥
51单片机 8pin 6IO口只要1元左右，带ID、存储 ，看门狗
蓝牙芯片也较便宜， 可存储、SN、密钥，看门狗


## 使用M0E1系列模块[ESP8266]驱动TM8211廉价音频芯片

M0E1系列模块简介

M0E1系列模块是劢领智能于2016年发布的基于ESP8266开发的2.4G WIFI模块，内置2M flash。模块将ESP8266的有效引脚引出，可以支持二次开发。劢领智能的模块，不但有高效多功能的AT指令模块，MQTT版本模块，而且只要使用了M0E1系列模块的用户，就可以使用劢领智能的功能lib进行快速开发。目前我们逐一将之前每种项目中稳定的功能进行归档做成lib。
TM8211简介

TM8211是两路16位数模转换集成电路，可广泛应用于数字音频、多媒体系统。芯片采用CMOS工艺设计，内部电路结构基于R-2R电阻网络结构设计，并在全电源电压范围内实现16bit的动态范围。 TM8211可通过采用数字串行总线数据输入，采用快速R-2R网络结构来支持8X的过采样音频信号处理。
TM8211 支持较宽范围的采样频率，并与PT8211、TDA1311兼容，输入采用LSBJ (Least Significant Bit Justified ) 格式, 数字编码格式采用MSB在前的补码格式。TM8211 采用8-pin SOP封装。

TM8211 只有几毛钱一个，立创商场有卖


[github](https://blog.csdn.net/mqlinks/article/details/88409929?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-5&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-5)

[ESP8266Audio](https://github.com/earlephilhower/ESP8266Audio)

[esp-audio-player](https://github.com/tuanpmt/esp-audio-player)

[ESP8266AudioMP3](https://github.com/earlephilhower/ESP8266AudioMP3)

[用ESP8266播放音乐](https://blog.csdn.net/weixin_33884611/article/details/89659490?depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2&utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2)

几经努力我们终于找到了一个非常实用的方案，根本不需要增加任何的附加硬件就以直接播放mp3!

这都归功于ESP8266Audio这个库，将喇叭直接接到一个数字输出口就可以直接播放MP3了,为了能有更大的功率加个普通三极管就可以完美推动一个小功率喇叭正常动作了。


## ESP32 Audio

ESP32 官方使用的codec也比较便宜.


# 模块化

## elfloader

The goal of this project is provide a loader for ELF file format for ARMv7-M (thumb-2) architecture (Aka Cortex-M, Cortex-R in Thumb2 mode) over bare-metal or RTOS enviroment.

This loader not required MMU or special OS support (only aligned memory alloc) and run with minimun memory overhead (only required parts of files is loaded in memory).

[src](https://github.com/martinribelotta/elfloader)
