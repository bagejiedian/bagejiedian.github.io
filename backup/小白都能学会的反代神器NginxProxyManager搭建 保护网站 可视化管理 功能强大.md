项目地址：
https://nginxproxymanager.com
1，vps一台
丽莎主机 原生ip 48小时可退
https://lisahost.com/aff.php?aff=1461
六六云服 原生ip 48小时可退
https://666clouds.com/aff.php?aff=1128
vultr云服按时计费
https://www.vultr.com/?ref=9580630

2，必要的更新
Debian/Ubuntu系统
```python
apt update -y  && apt install -y curl
```
3，放行端口
```python
ufw allow 443
ufw allow 80
ufw allow 81
ufw allow 
```
4，安装 Docker
```python
wget qO get.docker.com | bash
docker -v  #查看 docker 版本
systemctl enable docker  # 设置开机自动启动
```
5，安装 Docker-compose
```python
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version  #查看 docker-compose 版本
```
6，安装 Nginx Proxy Manager
新建文件夹
```python
mkdir -p /root/.data/docker_data/npm
```
进入文件夹
```python
cd /root/data/docker_data/npm
```
新建一个文件命名为
docker-compose.yml
把下面的东西复制到文件里面
```python
version: '3.8'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
```
然后保保存文件

7，后台运行
```python
docker-compose up -d
```
8，登录
ip:81访问

默认管理员用户：
Email:    admin@example.com
Password: changeme

