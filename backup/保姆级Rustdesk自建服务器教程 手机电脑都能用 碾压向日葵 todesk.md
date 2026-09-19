Rustdesk的官网及Github地址
官网：https://rustdesk.com/zh
Github开源项目：https://github.com/rustdesk/rustdesk
Github服务端页面：https://github.com/rustdesk/rustdesk-server
rustdesk安卓下载
https://github.com/rustdesk/rustdesk/releases/tag/1.2.3

1、购买vps
丽莎主机 原生ip 48小时可退
https://lisahost.com/aff.php?aff=1461
六六云服原生ip
https://666clouds.com/aff.php?aff=1128
vultr云服按时计费
https://www.vultr.com/?ref=9580630
2、
购买域名
解析域名dash.cloudflare.com
看之前的视频https://youtu.be/FwqVKZB8cOs?si=17rrwT0cVbXMMOa9

3、FinalShell SSH工具下载
https://www.hostbuf.com/t/988.html

4、必要更新操作(Debian/Ubuntu)
apt update -y && apt install -y curl socat wget
*注意：**如果是centos系统，则分别运行yum update -y和yum install -y curl socat wget

5、关闭防火墙
sudo ufw disable

6、将Rustdesk服务端的hbbr和hbbs两个ded的文件下载到购买的服务器里面
下载
wget https://github.com/rustdesk/rustdesk-server/releases/download/1.1.11-1/rustdesk-server-hbbr_1.1.11-1_amd64.deb
wget https://github.com/rustdesk/rustdesk-server/releases/download/1.1.11-1/rustdesk-server-hbbs_1.1.11-1_amd64.deb

7、安装
sudo dpkg -i rustdesk-server-hbbr_1.1.11-1_amd64.deb
sudo dpkg -i rustdesk-server-hbbs_1.1.11-1_amd64.deb

8、检测服务是否生效
sudo systemctl status rustdesk-hbbr.service
# 查看中继服务状态

sudo systemctl status rustdesk-hbbs.service
# 查看ID服务状态

查询KEY
sudo cat /lib/systemd/system/rustdesk-hbbs.service
# 查看WorkingDirectory目录

sudo cat /var/lib/rustdesk-server/id_ed25519.pub
# 查看key