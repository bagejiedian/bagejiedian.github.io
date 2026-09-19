1.购买服务器

 2、解析域名
cloudflare.com

3、用FinalShell连接云服
4、更新系统
apt update -y && apt upgrade -y

5、关闭防火墙
ufw disable

6、安装git
apt install git -y

7、一键申请SSL证书
git clone https://github.com/slobys/SSL-Renewal.git /tmp/acme && mv /tmp/acme/* /root && bash acme_2.0.sh

8、一键安装Marzban脚本
bash -c "$(curl -sL https://github.com/Gozargah/Marzban-scripts/raw/master/marzban.sh)" @ install

9、打开 cd /opt/marzban
修改配置文件
把本地证书路径映射到容器里面
添加管理员和密码
marzban cli admin create --sudo


重启marzban
marzban restart


打开Marzban面板：https://ma.131481:8008/dashboard/

节点配置编辑器 
https://azavaxhuman.github.io/MarzbanInboundGenerator/