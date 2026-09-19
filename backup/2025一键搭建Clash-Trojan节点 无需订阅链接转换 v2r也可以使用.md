1.购买云服https://lisahost.com/aff.php?aff=1461
 解析域名cloudflare.com

2.输入一键安装脚本
```PYTHON
source <(curl -sL https://git.io/trojan-install)
```
如果提示curl命令找不到command not found，通过以下方法先安装curl

centos操作系统：
```PYTHON
yum update -y && yum install curl -y
```
ubuntu操作系统：
```PYTHON
apt-get update -y && apt-get install curl -y
```
3.选择证书方式和域名
trojan安装完成，提示重启trojan成功后，选择证书方式：Let’s Encrypt证书，输入注册的域名，可使用二级域名。
4.选择mysql安装方式
此处选择安装docker版mysql即可。

5.输入用户名和密码
在安装完成后，提示输入用户名和密码，默认会生成一个随机用户名和密码，可直接使用默认。
6.查看最终的trojan节点链接信息
复制分享链接

ClashForWindows导入trojan自建节点
1.下载yaml模板并调整配置。
打开链接https://clashyun.com/wp-content/uploads/clash_trojan_config.yaml
下载模板配置文件，用记事本、VS Code、Notepad++等编辑器打开，
找到trojan配置块，把 server、port、password改成你服务器的信息：



V2RayN导入trojan自建节点
打开V2rayN，点击【服务器】->【从剪贴板导入批量URL】，系统自动完成导入。

关于v2rayN的使用教程可参见：v2rayN windows最新版本下载安装详细教程

FinalShell下载
www.hostbuf.com

Clash for windows 与 Clash for Android 中文汉化版仓库地址
https://github.com/Z-Siqi/Clash-for-Windows_Chinese/releases
v2rayN客户端
Windows（v2rayN）：https://github.com/2dust/v2rayN/releases/tag/6.23