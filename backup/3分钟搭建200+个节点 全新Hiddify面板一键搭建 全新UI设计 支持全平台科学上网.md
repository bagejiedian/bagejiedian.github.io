一：准备工作下载工具
1、下载FinalShell（连接vps）
https://www.hostbuf.com
2、下载代理软件：各平台客户端
Windows/MacOS（v2rayN）：https://github.com/2dust/v2rayNG
Android（v2rayNG）：https://github.com/2dust/v2rayNG/releases/tag/1.8.5
-----------------------：https://github.com/2dust/v2rayNG/releases/tag/1.10.18
Hysteria2节点（NekoBox）：https://github.com/MatsuriDayo/NekoBoxForAndroid/releases
MacOS/Windows（Clash Verge） ：https://github.com/clash-verge-rev/clash-verge-rev/releases
IOS（shadowrocket）：https://apps.apple.com/app/shadowrocket/id932747118
苹果 电脑/手机 小火箭
美区apple ID获取：
https://acclwp.acceboy.com/
优惠码：BAGE88

下载工具教程：
https://www.youtube.com/watch?v=xp_NCDGQtYQ

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
3、解析域名
https://dash.cloudflare.com
解析域名教程
https://www.youtube.com/watch?v=lenNw3DwNco&t=6s
https://www.youtube.com/watch?v=FwqVKZB8cOs&t=327s

4、加固VPS
https://www.youtube.com/watch?v=GnVYNaCl0Cg
https://www.youtube.com/watch?v=JYwfCzZKGa0

5、延迟测试 去程线路
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
ufw allow 1237/tcp
ufw allow 443/udp
ufw allow 80/udp
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
6、部署新版Hiddify面板
```PYTHON
bash <(curl -fsSL https://i.hiddify.com/release)
```
Hiddify项目地址
https://github.com/hiddify/Hiddify-Manager

7、安装 BBR 网络拥塞控制
```PYTHON
sh -c 'echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf' && sh -c 'echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf' && sysctl -p && lsmod | grep bbr
```
五：导入节点测试