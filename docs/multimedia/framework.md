# PulseAudio

PulseAudio is a sound system for POSIX OSes, meaning that it is a proxy for your sound applications. It allows you to do advanced operations on your sound data as it passes between your application and your hardware. Things like transferring the audio to a different machine, changing the sample format or channel count and mixing several sounds into one are easily achieved using a sound server.

[wiki](https://www.freedesktop.org/wiki/Software/PulseAudio/)
PulseAudio的主要特点包括:

    可对每一个应用程序进行音量控制Per-application volume controls
    可扩展的插件与支持可装载模块架构
    兼容性许多流行的音频应用程序
    支持多重音源和多重输出
    低延时操作和支持延迟测量
    一个对处理器资源效率零拷贝内存架构
    能够发现本地网络上使用PulseAudio的其他计算机并通过其扬声器直接播放声音
    能够改变一个应用程序的声音输出设备，就算这个应用程序在播放声音（程序不需要支持这特性，而事实上，程序甚至没有意识到改变）
    带有脚本功能的命令行界面
    一个功能完善且带有命令行重新配置功能的守护进程
    内置采样转换和重采样功能
    能够合并多块声卡成一个声卡
    能够同步播放多个音频流
    动态检测蓝牙音频设备
    使全系统均衡的能力 
