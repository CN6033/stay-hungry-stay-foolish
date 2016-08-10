# VPN和Shadowsocks服务搭建

## Shadowsocks
请参考[该链接](http://www.jianshu.com/p/2f51144c35c9)

## VPN
请参考[该链接](https://www.digitalocean.com/community/tutorials/how-to-setup-your-own-vpn-with-pptp)

### 配置firewall规则
我没有使用iptables作为防火墙，而是使用firewall。请执行如下命令进行配置：
```
firewall-cmd --permanent --direct --add-rule ipv4 filter INPUT 0 -p gre -j ACCEPT
firewall-cmd --permanent --direct --add-rule ipv6 filter INPUT 0 -p gre -j ACCEPT
firewall-cmd --reload
```

## Tips
如果使用免费试用的AWS进行搭建，请注意配置【安全组】开放相应端口，例如VPN服务需要开放TCP:1723端口，Shadowsocks则需要开放TCP/UPD:443端口。
