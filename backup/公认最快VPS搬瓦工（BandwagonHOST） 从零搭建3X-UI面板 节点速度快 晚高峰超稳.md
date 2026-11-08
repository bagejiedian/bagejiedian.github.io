一：准备工作下载工具
1、下载FinalShell（连接vps）
https://www.hostbuf.com
2、下载代理软件：各平台客户端
Windows（v2rayN）：https://github.com/2dust/v2rayNG
Android（v2rayNG）：https://github.com/2dust/v2rayNG/releases/tag/1.8.5
-----------------------：https://github.com/2dust/v2rayNG/releases/tag/1.10.18
Hysteria2节点（NekoBox）：https://github.com/MatsuriDayo/NekoBoxForAndroid/releases
MacOS/Windows（Clash Verge） ：https://github.com/clash-verge-rev/clash-verge-rev/releases
IOS（shadowrocket）：https://apps.apple.com/app/shadowrocket/id932747118
苹果 电脑/手机 小火箭
美区apple ID获取：
https://acclwp.acceboy.com/
优惠码：BAGE88

二：购买云服
1、搬瓦工 速度极快 30天内可退
https://bandwagonhost.com/aff.php?aff=75423

莱卡云 价格便宜 3天可退
https://www.lcayun.com/aff/BOWLAKCX

2、关闭代理检测IP是否开通
按Win+r
```PYTHON
ping 自己的ip -t
```
3、延迟测试 去程线路
https://www.itdog.cn

三：FinalShell连接vps

1、Debian / Ubuntu 系统安装 sudo curl 必要的运行环境
```PYTHON
apt update && apt install -y sudo curl
```
2、安装 防火墙UFW
首先更新软件包列表并安装 UFW
```PYTHON
apt install ufw -y
```
3、放行目标端口
```PYTHON
ufw allow 22/tcp
ufw allow 58888/tcp
ufw allow 443/udp
ufw allow 8443/udp
ufw allow 48888:50000/udp
```
4、启用防火墙
激活 UFW 以使规则生效：
```PYTHON
ufw enable
```
5、验证配置结果
最后，检查防火墙的状态和当前生效的规则：
```PYTHON
ufw status
```
6、安装防火墙工具Debian / Ubuntu 系统安装防火墙工具
```PYTHON
apt install -y iptables iptables-persistent
```
7、将端口跳跃的 48888端口 到 50000端口 的 UDP 流量重定向到指定端口 (IPv4)
```PYTHON
iptables -t nat -A PREROUTING -p udp --dport 48888:50000 -j REDIRECT --to-ports 443
```
8、固化防火墙规则
为了防止服务器重启后刚才敲的规则丢失
```PYTHON
netfilter-persistent save
```
四、安装 3X - UI 面板
```PYTHON
bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh) v3.7.0
```
五：导入节点测试
检查您自己的IP地址
https://whoer.net/zh
IP检测
https://ping0.cc/
六：挂载双ISP住宅IP
https://github.com/bagejiedian/bagejiedian.github.io/issues/34