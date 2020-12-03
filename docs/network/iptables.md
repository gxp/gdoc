# NAT

echo "1" >/proc/sys/net/ipv4/ip_forward

```
iptables –t nat –A POSTROUTING –s 192.168.10.10 –o eth1 –j SNAT --to-source 111.196.221.212

```

```

IPTABLES='/sbin/iptables'
EXTERNAL='eth1'
EXTERNIP='159.226.41.141'
INTERNAL='eth0'
INTERNIP='10.20.10.0/24'

#enable ip masquerade
    echo "1" >/proc/sys/net/ipv4/ip_forward
    $IPTABLES -t nat -A POSTROUTING -o $EXTERNAL -s $INTERNIP -j MASQUERADE
    # $IPTABLES -t nat -A POSTROUTING -s $IPDOMAIN -j SNAT --to $OUTIP
    # $IPTABLES -t nat -A PREROUTING -d $EXTERNIP -p tcp --dport 21 -j DNAT --to $FTPIP
    # $IPTABLES -t nat -A PREROUTING -d $EXTERNIP -p tcp --dport 80 -j DNAT --to $WEBIP
————————————————
原文链接：https://blog.csdn.net/colin719/article/details/449342
```


# 参考

[iptables详解](http://www.zsythink.net/archives/1199)
