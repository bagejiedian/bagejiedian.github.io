第一步：检查vps
1.查看ip有没有被攻击
```PYTHON
journalctl -u ssh | grep "Failed password"
```
2.查最近10分钟的SSH爆破情况
```PYTHON
journalctl -u ssh --since "10 min ago" | grep "Failed password" | wc -l
```
3.找出这10分钟内攻击你最狠的IP：
```PYTHON
journalctl -u ssh --since "10 min ago" | grep "Failed password" | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr | head -5
```
4.查当前20个网络连接与在线用户
```PYTHON
ss -tnp | grep ESTAB | head -20
who
```
ss 命令会列出当前所有已建立的 TCP 连接。你可以看看是否有陌生 IP 连着你的 SSH 22 或其他端口。
who 会显示当前谁在登录你的服务器。确保只有你自己的 IP（比如 123.9.67.99）
5. 统计被攻击次数最多的20个 IP（找出攻击源）
```PYTHON
journalctl -u ssh | grep "Failed password" | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr | head -20
```
这个命令会列出尝试登录失败次数最多的前 20 个 IP

6. 查看是否已经有 IP 成功登录 并列出最近20个，显示登录时间，journalctl 看精确到秒的动作（极其重要！）：
```PYTHON
journalctl -u ssh | grep "Accepted password" | tail -20
```
如果看到了你不认识的 IP 登录成功，说明服务器已经被入侵了！

7.查看有没有ip已经成功登录 并列出最后20个ip，显示登录及退出时间，last 看登录的持续时间。
```PYTHON
journalctl -u ssh | grep "Accepted password"
last -n 20
```
如果输出了 Accepted password，并且登录的 IP 你完全不认识，那就意味着黑客已经成功登录过！请立刻重置所有密码。
如果全是 Failed password，没有任何 Accepted password，那恭喜你，目前安全
8. 修改 root 密码（最紧急）立刻执行 
```PYTHON
passwd root
```
输入一个非常复杂的密码（大小写+数字+符号，15位以上）。
9. 检查是否被留了后门（SSH 密钥）
```PYTHON
cat /root/.ssh/authorized_keys
```
如果里面有你不认识的密钥（通常是一长串 ssh-rsa 开头的内容），立刻删掉这个文件或删除未知密钥，这会成为黑客免密登录的后门
10. 检查是否有恶意定时任务
```PYTHON
crontab -l
ls -la /etc/cron.*
```
看看有没有执行奇怪脚本（比如 wget 下载、curl 外连、/tmp/ 下的可执行文件）的定时任务，如果有，立刻删除
11. 检查是否有异常进程和网络连接
```PYTHON
top -c
ss -tulnp
```
看看有没有 CPU 占用极高的未知进程（通常是挖矿程序），或者连向陌生 IP 的异常端口
12. 检查是否新增了未知用户
```PYTHON
cat /etc/passwd | grep -v nologin
```
如果发现了奇怪的账号，立即 userdel -r <用户名>。删除用户

第二步：更新系统安全补丁
```PYTHON
sudo apt update && sudo apt upgrade -y
```
检查是否需要重启：
```PYTHON
test -f /var/run/reboot-required && cat /var/run/reboot-required
```
如果提示需要重启，在确认当前没有重要任务以后执行：
```PYTHON
sudo reboot
```
重新连接服务器以后，检查自动安全更新：
```PYTHON
systemctl status unattended-upgrades --no-pager
```
如果服务已经正常运行，不需要重复配置。
如果没有安装：
```PYTHON
sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades
```
自动安全更新主要用于系统安全补丁。

第三步：安装 防火墙UFW
1、首先更新软件包列表并安装 UFW
```PYTHON
sudo apt update
```
```PYTHON
apt install ufw -y
```
2、放行目标端口
```PYTHON
ufw allow 22/tcp
ufw allow 33213/tcp
ufw allow 443/udp
```
不确定协议用ufw allow 端口号
3、启用防火墙
激活 UFW 以使规则生效：
```PYTHON
ufw enable
```
4、验证配置结果
最后，检查防火墙的状态和当前生效的规则：
```PYTHON
ufw status
```
第四步：修改端口
1.备份配置文件（重要）：登录服务器后，先备份原有配置，以防修改出错时恢复
```PYTHON
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config_bak
```
2.编辑配置文件：使用 nano 打开 SSH 配置文件，把22端口修改为33213（200-60000）
```PYTHON
sudo nano /etc/ssh/sshd_config
```
移动光标：用键盘的 ↑ ↓ ← → 方向键，找到 #Port 22 这一行。
修改内容：
删掉 #Port 22 前面的 #，让它变成 Port 22（保留旧端口作为退路）。
在它下面新起一行，输入你想要的端口，比如 Port 33213（注意：前面绝对不能带 #）。
保存并退出（这是最关键的一步）：
按键盘上的 Ctrl + O（字母O），底部会提示文件名，直接按 回车键（Enter）保存。
按键盘上的 Ctrl + X，退回到命令行。当前这个 SSH 窗口千万不要关。
检查配置有没有语法错误
```PYTHON
sudo sshd -t
```
如果没有任何输出，说明你的配置文件完全正确
3.重启 SSH 服务：让新配置生效，sshd 是 CentOS/RedHat 系统的服务名。ssh 是 Ubuntu/Debian 系统的服务名。
```PYTHON
sudo systemctl restart ssh
```
```PYTHON
sudo systemctl restart sshd
```
4.验证监听：确认 SSH 服务状态（最直观）
```PYTHON
sudo systemctl status ssh
```
```PYTHON
sudo systemctl status sshd
```
看到绿色的 active (running) 就说明服务好好的。
查一下 sshd 进程在监听什么
```PYTHON
sudo ss -tlnp | grep sshd
```
这时候你应该能看到类似 0.0.0.0:22 和 0.0.0.0:33213 同时存在。

第五步：
安装 Fail2Ban 自动封禁爆破 IP
```PYTHON
sudo apt update
sudo apt install fail2ban -y
```
开机启动
```PYTHON
sudo systemctl enable fail2ban
```
立即启动该服务
```PYTHON
sudo systemctl start fail2ban
```
安装后它会自动监控 SSH 日志，同一个 IP 输错 5 次密码自动拉黑 10 分钟，彻底解放你的日志。

第六步：：创建普通 sudo 管理用户bage（换成自己的用户名）
```PYTHON
sudo adduser bage
```
 需要修改新用户名
将用户加入 sudo 组：
```PYTHON
sudo usermod -aG sudo bage
```
检查用户：
```PYTHON
id bage
```
检查 sudo 权限：
```PYTHON
sudo -l -U bage
```
切换用户：
```PYTHON
su - bage
```
测试：
```PYTHON
sudo whoami
```
预期：
```PYTHON
root
```
第七步：禁用 root 密码登录
禁用密码登录，改用密钥登录（终极方案）
在本地生成密钥对，把公钥传回服务器，然后在 /etc/ssh/sshd_config 里设置 PasswordAuthentication no。这样黑客哪怕有你的密码也登录不了。