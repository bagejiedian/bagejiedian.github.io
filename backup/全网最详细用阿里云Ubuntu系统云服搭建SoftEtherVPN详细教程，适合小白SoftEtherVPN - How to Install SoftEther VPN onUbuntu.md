丽莎主机 原生ip 48小时可退
https://lisahost.com/aff.php?aff=1461
六六云服 原生ip 48小时可退
https://666clouds.com/aff.php?aff=1128
狗云 便宜
https://www.dogyun.com/?ref=bage13
搬瓦工 速度快
https://bandwagonhost.com/aff.php?aff=75423

vultr云服按时计费
https://www.vultr.com/?ref=9580630
Softether Vpn下载中心
http://softether.fishinfo.cn/cn.aspx


softvpn
1·环境:
```python
apt-get update -y
apt-get install build-essential gnupg2 gcc make -y
```

下载
```python
wget https://www.softether-download.com/files/softether/v4.41-9787-rtm-2023.03.14-tree/Linux/SoftEther_VPN_Server/64bit_-_Intel_x64_or_AMD64/softether-vpnserver-v4.41-9787-rtm-2023.03.14-linux-x64-64bit.tar.gz
```
解压
```python
tar -zxvf softether-vpnserver-v4.41-9787-rtm-2023.03.14-linux-x64-64bit.tar.gz
```
导航到提取目录 安装 softether VPN
```python
cd /root/vpnserver
make
```
返回主目录将目录移动到/ust/local目录
cd ..

mv vpnserver /usr/local/
接下来，为 vpnserver目录设置适当的权限:
cd /usr/local/vpnserver/
chmod 600 *
chmod 700 vpnserver
chmod 700 vpncmd

开机自启
```python
sudo vim /etc/init.d/vpnserver
```
添加以下行:
#!/bin/sh
# chkconfig: 2345 99 01
[#description](https://www.youtube.com/hashtag/description): SoftEther VPN Server
DAEMON=/usr/local/vpnserver/vpnserver
LOCK=/var/lock/subsys/vpnserver
test -x $DAEMON || exit 0
case "$1" in
start)
$DAEMON start
touch $LOCK
;;
resfart)
SDAEMON stop
sleep 3
$DAEMON start
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
exit 0

保存并关闭文件，
Esc  
Shift+:
wq
然后创津所需的目录并使用以下命令为 systemd 服务文件设置适当的权限:
mkdir /var/lock/subsys
chmod 755 /etc/init.d/vpnserver
接下来，便用以下命念启动 SoftEther VPN:
/etc/init.d/vpnserver start
接下来，启用 SoftEther VPN 服务以在系统更启时启动:
update-rc.d vpnserver defaults

配置vpn server
cd /usr/local/vpnserver
./vpncmd

1
回撤
回撤
设置密码
VPN Server>ServerPasswordSet
 123456
123456
设置完毕

创建一个hub
HubCreate minghub
设置密码
123456
123456

进入Hub
Hub minghub
让集线器作为虚拟lan工作 运行以下命令
SecureNatEnable

创建一个VPN用户
UserCreate vpnming
回撤
创建客户端
Assigned Group Name: 

User Full Name: vpnming11

User Description:id
再设置密码
UserPasswordSet  vpnming
123456
123456

启用ipsec 多协议工作
IPsecEnable

yes
yes
yes
vpns
用户名
vpnming
最后退出
exit

开启端口
ufw allow 443/tcp
ufw allow 5555/tcp
ufw allow 992/tcp

重启端口
ufw reload