一键搭建VPS教程，最新的VLESS Vision和VLESS Reality防止VPS端口封禁

1，一台境外VPS主流系统
vult云服按时计费注册链接
https://www.vultr.com/?ref=9580630

2，下载并安装FinalShell SSH工具
Windows版下载地址：http://www.hostbuf.com/downloads/finalshell_install.exe 
macOS版下载地址：http://www.hostbuf.com/downloads/finalshell_install.pkg 
3,搭建 Reality
安装所需组件
## 以下为 CentOS 命令
yum update -y 
yum install curl wget -y

## 以下为 Debian / Ubuntu 命令
apt update -y 
apt install curl wget -y

4，X-UI搭建脚本代码
bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh)

可参考的域名
这里输入的域名最低标准为：国外网站，支持 TLSv1.3 、H2 、没有被阻断，千万不要写被阻断的网站，注意红框的端口，这里必须添加
# Apple
gateway.icloud.com
itunes.apple.com
swdist.apple.com
swcdn.apple.com
updates.cdn-apple.com
mensura.cdn-apple.com
osxapps.itunes.apple.com
aod.itunes.apple.com

# mozilla
download-installer.cdn.mozilla.net
addons.mozilla.org

# aws
s0.awsstatic.com
d1.awsstatic.com
images-na.ssl-images-amazon.com
m.media-amazon.com
player.live-video.net

# 其他
one-piece.com
lol.secure.dyn.riotcdn.net
www.lovelive-anime.jp
www.nokia.com
auth.riotgames.com
xsso.riotgames.com
csgo.com
可以使用这个网站
https://www.ssllabs.com/projects/index.html
来寻找 TLS1.3 / X25519 / H2 的指向站点
也可以使用这个网站
http://web.chacuo.net/netocspstapling
来查询目标网站是否支持 OCSP Stapling

5，三、各平台客户端
v2rayNG【需要最新版本】

Windows（v2rayN）：https://github.com/2dust/v2rayN/releases/tag/6.23

Android（v2rayNG）：https://github.com/2dust/v2rayNG/releases/tag/1.8.5

IOS（shadowrocket）：https://apps.apple.com/app/shadowrocket/id932747118

6，放行端口
放行指令是一样的，只要将端口443为任意端口就可以了。
iptables -I INPUT -p tcp --dport 443 -j ACCEPT
iptables -I INPUT -p tcp --dport 4321 -j ACCEPT