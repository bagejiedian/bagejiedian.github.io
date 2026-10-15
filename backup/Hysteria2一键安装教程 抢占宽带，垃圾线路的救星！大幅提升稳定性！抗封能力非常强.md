1、官方开源项目地址
https://github.com/apernet/hysteria

2、购买服务器
莱卡云（性价比高）24小时全额退 3天内按已使用天数折算
https://www.lcayun.com/aff/BOWLAKCX
丽莎主机 原生ip 48小时可退
https://lisahost.com/aff.php?aff=1461
六六云服 原生ip 48小时可退
https://666clouds.com/aff.php?aff=1128
vultr云服
https://www.vultr.com/?ref=9580630

3、必要更新操作(Debian/Ubuntu)
apt update -y && apt install -y curl socat wget

4、放行端口
ufw allow 443
ufw allow 80
ufw allow 5678
ufw allow 
5、一键安装脚本
wget -N --no-check-certificate https://raw.githubusercontent.com/flame1ce/hysteria2-install/main/hysteria2-install-main/hy2/hysteria.sh && bash hysteria.sh

www.bing.com  #伪装网址

启动hysteria或者设置hysteria开机自启
启动：systemctl start hysteria-server.service
查看状态：systemctl status hysteria-server.service
开机自启：systemctl enable hysteria-server.service
重启：systemctl restart hysteria-server.service

客户端配置
下载客户端配置文件：https://github.com/apernet/hysteria/releases
把下载好的文件替换到v2rayN的这个目录下：\zz_v2rayN-With-Core-SelfContained\zz_v2rayN-With-Core-SelfContained\bin\hysteria


FinalShell下载
www.hostbuf.com
各平台客户端
Windows（v2rayN）：https://github.com/2dust/v2rayN/releases/tag/6.23
Android（v2rayNG）：https://github.com/2dust/v2rayNG/releases/tag/1.8.5
IOS（shadowrocket）：https://apps.apple.com/app/shadowrocket/id932747118