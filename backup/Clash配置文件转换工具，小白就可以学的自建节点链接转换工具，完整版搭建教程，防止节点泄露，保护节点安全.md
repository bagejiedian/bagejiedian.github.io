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
1、必要更新操作(Debian/Ubuntu)
```PYTHON
apt update -y && apt install -y curl socat wget
```
*注意：**如果是centos系统，则分别运行yum update -y和yum install -y curl socat wget
放行端口
```python
ufw allow 25500
ufw allow 58080
ufw allow 80
```
2、安装 Docker（非大陆服务器）
```python
wget qO get.docker.com | bash
```
查看docker 版本
```python
docker -v  
```
# 设置开机自动启动
```python
systemctl enable docker
```
3、安装 Docker-compose（非大陆服务器)
```python
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
#查看docker-compose 版本
docker-compose --version
```
4、部署后端
```python
docker run  -d --name=subconverter --restart=always -p 25500:25500 stilleshan/subconverter
```
验证是否安装成功
```python
curl http://localhost:25500/version
```
浏览器里输入
curl http://149.28.152.99:25500/version

5、搭建前端
下载源码
```python
git clone https://github.com/CareyWang/sub-web.git
```
查看
ls
6、进入sub-wed文件夹
cd /root/sub-web

编辑.env文件
# API 后端
VUE_APP_SUBCONVERTER_DEFAULT_BACKEND = "https://149.28.152.99:25500/"


7、构建当前项目
```python
docker build -t subweb-local:latest .
```
8、执行
```python
docker run -d -p 58080:80 --restart always --name subweb subweb-local:late
```
ip:58080访问


前端网页端
Docker
https://github.com/CareyWang/sub-web

后端
docker 部署
项目地址：https://github.com/tindy2013/subconverter
[https://github.com/tindy2013/subconverter/blob/master/README-docker.md](https://www.youtube.com/redirect?event=comments&redir_token=QUZZTVljRms0ZnZaU0JzeHZ1S0Qtcnhzc1M3OXxBTl9pYzRkTkRqTUpxYVQya3JhQmRtX0pxZW5GXy1vX0lIdGxMamdITnRjZUhCRzBjMXZJNzRGZDlyVGFYQUpGQ25KLW41dHZjLWt1ZHk4YlAtcGVVU3hNSGRwc2RnSUt1VnNN&q=https%3A%2F%2Fgithub.com%2Ftindy2013%2Fsubconverter%2Fblob%2Fmaster%2FREADME-docker.md)