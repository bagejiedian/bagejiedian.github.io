1.准备一台VPS 一个域名
https://www.vultr.com/?ref=9580630
2.解析两条记录 neza   ip 
cloudflare
3.部署Nginx Proxy Manager 反代
更新下VPS系统环境
apt update -y && apt install -y curl socat wget sudo

放行端口
ufw allow 443
ufw allow 80
ufw allow 81
ufw allow 8008
ufw allow 5555

安装 Docker：
curl -fsSL https://get.docker.com | sh

一键安装 Nginx Proxy Manager
docker run -d \
  --name=npm \
  -p 80:80 \
  -p 81:81 \
  -p 443:443 \
  -v /home/npm/data:/data \
  -v /home/npm/letsencrypt:/etc/letsencrypt \
  --restart=always \
  jc21/nginx-proxy-manager:latest

安装成功后进入NGINX后台面板：
服务器IP加81端口访问网页
用户：admin@example.com
密码：changeme
登入后记得先修改密码

4.GitHub上 创建一个 OAuth Apps
https://github.com/settings/developers

Application name – 随意填写
Homepage URL – 填写面板的访问域名，如：https://解析过的二级域名
Authorization callback URL – 填写回调地址，如：https://解析过的二级域名/oauth2/callback

5.一键安装哪吒监控面板
curl -L https://raw.githubusercontent.com/naiba/nezha/master/script/install.sh -o nezha.sh && chmod +x nezha.sh
sudo ./nezha.sh 

GitHub用户名
标题随便输入

设置
解析过的第二个二级域名
保存