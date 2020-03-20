# VPN

## boringtun

https://github.com/cloudflare/boringtun

Userspace WireGuard® Implementation in Rust

## WireGuard

WireGuard是Jason A. Donenfeld开发的开源VPN协议。目前支持Linux, macOS, Android以及OpenWrt。Windows官方客户端还在开发，但第三方Windows客户端已经出现。WireGuard被视为下一代VPN协议。

它是一个构建快速、现代、安全的 FQ 的协议和工具套件，它具有以下优点

    使用最先进的加密技术，防范攻击（RSA, SHA 广被诟病都将被淘汰）
    性能远超 OpenV*N
    效率极高，WireGuard 协议作为 Linux 内核模块运行
    通用用途，支持嵌入式和非嵌入式设备
    跨平台，初期在 Linux 平台发布，现已支持所有平台
    易用，用过 OpenV*N 等工具集的人都明白这其中的痛苦
    工作在 3 层（链路层），支持漫游，地址变更对用户无感知，使用更简单，切换更平滑
    使用 UDP 传输数据，轻量、高效、节能、节省带宽（适用于 IOT 领域）
    基于 GPLv2 （Linux Kernel 基于 GPLv2）免费开源

由于 WireGuard 是 UDP 传输，部分地区运营商对 UDP 有干扰，可能导致断流等问题，暂不推荐作为日常 FQ 手段使用，但是在 TCP 被阻断的 VPS 上不失为一种解决办法。

当前 VPN 领域，已经有了 IPSEC, PPTP, L2TP, OpenVPN，为什么我们还需要另一种？

WireGuard协议的速度几乎秒杀其它VPN协议，

*  更少的实现代码 相比OpenVPN 600,000 行代码来说，WireGuard 只有4,000 行，对于安全组件，代码量越少，可能遭受到的攻击越少，也更容易被世界各地的开发者 review。
*  更容易部署 作为比较，一个完全不熟悉 VPN 的技术人员，使用 OpenVPN 和 WireGuard 部署一套 VPN 所使用的时间大概是 48小时对 6 小时。
*  更强的加密算法 其中使用了 Curve25519 秘钥交换算法；ChaCha20 对称加解密算法（比 AES 更快更高效）； Poly1305 消息摘要算法； BLAKE2 和 SipHash24 HASH 算法；HKDF 秘钥衍生算法。
*  更快的连接 在 OpenVPN，OpenSSL 的世界里，等待是习以为常的事情，因为协议的复杂性决定了连接的建立非常耗时，通常你需要主动告诉用户 VPN 正在建立连接中，否则用户会以为程序挂掉了，而当你第一次用 WireGuard 客户端后，你发现它的速度超乎想象，跟你在 shell 里敲一个echo命令一样快。
Linus Torvalds 如何评价？

让我们先看一段 Linus Torvalds 在邮件组中的一段话，世界上能入 Torvalds 法眼的东西太少了，从他的这段话中我们可以看出 WireGuard 的分量，当然这其中也有其前任 OpenVPN 和 IPSec 等的使用极其复杂，同时还频频爆出安全漏洞的原因。

Can I just once again state my love for it and hope it gets merged soon? Maybe the code isn't perfect, but I've skimmed it, and compared to the horrors that are OpenVPN and IPSec, it's a work of art.

https://github.com/WireGuard/
