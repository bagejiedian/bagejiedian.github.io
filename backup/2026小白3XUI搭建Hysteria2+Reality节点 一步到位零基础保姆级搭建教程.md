一、准备工作
1、购买vps
丽萨主机
https://lisahost.com/aff.php?aff=1461

2、域名在 Cloudflare 上做好解析，没有域名跳过。

3、下载 FinalShell SSH 工具（点击下方链接即可下载）
Windows 下载：
https://dl.hostbuf.com/finalshell3/finalshell_windows_x64.exe
MacOS M芯片下载：
https://dl.hostbuf.com/finalshell3/finalshell_macos_arm64.pkg
MacOS intel 芯片下载：
https://dl.hostbuf.com/finalshell3/finalshell_macos_x64.pkg
V2rayN下载地址：
https://github.com/2dust/v2rayN/releases/tag/7.25.1
Clash下载地址：
https://github.com/clash-verge-rev/clash-verge-rev/releases
https://www.clashverge.dev/install.html

二、Debian / Ubuntu 系统安装 sudo curl 必要的运行环境
```PYTHON
apt update && apt install -y sudo curl
```
三、放行 VPS 端口
1、安装 防火墙UFW
首先更新软件包列表并安装 UFW
```PYTHON
apt update
apt install ufw -y
```
2、放行目标端口
```PYTHON
ufw allow 22/tcp
ufw allow 58888/tcp
ufw allow 443/udp
ufw allow 8443/udp
ufw allow 48888:50000/udp
```
3、启用防火墙
激活 UFW 以使规则生效：
```PYTHON
ufw enable
```
4、验证配置结果
最后，检查防火墙的状态和当前生效的规则：
```PYTHON
ufw status
```
四、安装防火墙工具
1、Debian / Ubuntu 系统安装防火墙工具
```PYTHON
apt install -y iptables iptables-persistent
```
2、将端口跳跃的 48888端口 到 50000端口 的 UDP 流量重定向到指定端口 (IPv4)
```PYTHON
iptables -t nat -A PREROUTING -p udp --dport 48888:50000 -j REDIRECT --to-ports 8443
```
3、固化防火墙规则
为了防止服务器重启后刚才敲的规则丢失
```PYTHON
netfilter-persistent save
```
五、安装 BBR 网络拥塞控制
```PYTHON
sh -c 'echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf' && sh -c 'echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf' && sysctl -p && lsmod | grep bbr
```
六、安装 3X - UI 面板
```PYTHON
bash <(curl -Ls https://raw.githubusercontent.com/mhsanaei/3x-ui/master/install.sh) v3.7.0
```