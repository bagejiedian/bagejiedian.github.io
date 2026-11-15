一：准备工作下载工具
1、下载FinalShell（连接vps）
https://www.hostbuf.com
2、下载代理软件：各平台客户端
Windows（v2rayN）：https://github.com/2dust/v2rayNG
Android（v2rayNG）：https://github.com/2dust/v2rayNG/releases/tag/1.8.5
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

2、部署新版Hiddify面板
bash <(curl -fsSL https://i.hiddify.com/release)

Hiddify项目地址
https://github.com/hiddify/Hiddify-Manager

安装 BBR 网络拥塞控制
```PYTHON
sh -c 'echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf' && sh -c 'echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf' && sysctl -p && lsmod | grep bbr
```
五：导入节点测试