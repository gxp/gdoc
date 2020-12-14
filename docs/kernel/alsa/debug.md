# 调试

## 查看信息

* 可以从/proc/asound查看声卡相关信息

[ALSA-ASOC音频驱动框架简述](https://blog.csdn.net/linuxarmbiggod/article/details/80600633)

### 查看示例 

1. 查看当前codec
# cd /sys/class/sound
# ls -alh
lrwxrwxrwx  1 root root 0 2019-12-04 14:29 card0 -> ../../devices/soc/soc:sound-9335/sound/card0
lrwxrwxrwx  1 root root 0 2019-12-04 14:29 controlC0 -> ../../devices/soc/soc:sound-9335/sound/card0/controlC0
 
可以看出使用的codec是wcd9335
# cd /sys/devices/soc/soc:sound-9335/sound/card0
 
2. 查看asoc的codec、dai、platforms
<1>. 查看codec
# cat /sys/kernel/debug/asoc/codecs
tasha_codec
soc:qcom,msm-stub-codec
tfa98xx.7-0034
9a0000.qcom,hdmi_tx:qcom,msm-hd
snd-soc-dummy
 
<2>. 查看dai
# cat /sys/kernel/debug/asoc/dais
msm_htc_mi2s_codec
msm-stub-tx
msm-stub-rx
tfa98xx-aif-7-34 //nxp tfa98xx
msm_hdmi_audio_codec_rx_dai
snd-soc-dummy-dai
 
<3>. 查看platforms
# cat /sys/kernel/debug/asoc/platforms
soc:qcom,msm-pcm-voice
soc:qcom,msm-voip-dsp
soc:qcom,msm-cpe-lsm@3
soc:qcom,msm-cpe-lsm
soc:qcom,msm-pcm-dsp-noirq
soc:qcom,msm-pcm-loopback
soc:qcom,msm-lsm-client
soc:qcom,msm-pcm-afe
soc:qcom,msm-compr-dsp
soc:qcom,msm-compress-dsp
soc:qcom,msm-pcm-routing
soc:qcom,msm-ultra-low-latency
soc:qcom,msm-pcm-low-latency
soc:qcom,msm-pcm
soc:qcom,msm-pcm-hostless
snd-soc-dummy
 
 
3. 查看codec寄存器
# cat /sys/kernel/debug/regmap/7-0034/registers
00: d05f
01: 0326
02: 0019
03: 0092
04: 889b
05: 9392
06: 000f
07: 8fff
08: 3832
.....
 
# cat /sys/kernel/debug/asoc/realtek,rt5651-codec/ff88xxx.i2s/dapm/Capture
Capture: On //打开录音时
Capture: Off //关闭录音时
 
# cat cat /sys/kernel/debug/regmap/7-0034/name
tfa98xx
 
4.查看i2c设备
# cat /sys/bus/i2c/devices/i2c-7/7-0034/of_node/compatible
rockchip,rt5651
 
# cat /sys/bus/i2c/devices/i2c-7/7-0034/of_node/name
rt5651
 
# cat /sys/bus/i2c/devices/i2c-7/7-0034/of_node/status
okay
 
[以上来源 高通音频驱动调试(Updating)](https://blog.csdn.net/u010164190/article/details/103395962) 
 