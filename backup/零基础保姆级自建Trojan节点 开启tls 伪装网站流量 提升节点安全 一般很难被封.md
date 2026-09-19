购买vps
https://www.vultr.com/?ref=9580630
购买域名
解析域名
https://youtu.be/lenNw3DwNco?si=V0lsGsjVGY0notHt


1、必要更新操作(Debian/Ubuntu)
```PYTHON
apt update -y && apt install -y curl socat wget
```
*注意：**如果是centos系统，则分别运行yum update -y和yum install -y curl socat wget

如果是Vultr，需要开放端口
Vultr目前机器只默认开放SSH端口22，其它一些端口全部需要手动开放，复制以下命令运行就行
```PYTHON
apt-get install firewalld -y 
&& firewall-cmd --zone=public --add-port=443/tcp --permanent 
&& firewall-cmd --zone=public --add-port=80/tcp --permanent 
&& firewall-cmd --zone=public --add-port=22/tcp --permanent 
&& firewall-cmd --reload
ufw allow 443
ufw allow 80
```
2、申请证书
curl https://get.acme.sh | sh
~/.acme.sh/acme.sh --register-account -m 邮箱
~/.acme.sh/acme.sh --issue -d 域名 --standalone

curl https://get.acme.sh | sh
~/.acme.sh/acme.sh --register-account -m 1468854170@qq.com
~/.acme.sh/acme.sh --issue -d bage.131481.xyz --standalone

正式安装Trojan
```PYTHON
curl -O https://raw.githubusercontent.com/xiaochaib/trojan_atrandys/edit/trojan_mult.sh && chmod +x trojan_mult.sh && ./trojan_mult.sh
```
获取Trojan配置信息
复制以下路径到FinalSheel中访问，找到server.conf直接在FinalShell中打开

/usr/src/trojan
如需要更改密码，修改server.conf后重新上传，再运行以下命令重启trojan生效
systemctl restart trojan

地址域名：自己的域名
端口443
密码b2ea7957

打开v2r
添加trojan节点
输入地址 端口 密码 
传输层安全 tls

FinalShell下载
www.hostbuf.com

各平台客户端
Windows（v2rayN）：https://github.com/2dust/v2rayN/releases/tag/6.23
Android（v2rayNG）：https://github.com/2dust/v2rayNG/releases/tag/1.8.5
IOS（shadowrocket）：https://apps.apple.com/app/shadowrocket/id932747118




BBR加速四合一 BBR Plus / 原版BBR / 魔改BBR一键脚本（Centos 7, Debian 8/9, Ubuntu 16/18 测试通过）
```PYTHON
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```