第六步：创建普通 sudo 管理用户bage（换成自己的用户名）
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
su bage
```
行使sudo 权限
```PYTHON
sudo whoami
```
要切换到 root 用户
```PYTHON
sudo -i
```
第七步：禁用 root 密码登录，生成密钥
步骤 1:打开powershell，执行：
```PYTHON
ssh-keygen -t ed25519 -C "my-vps-key"
```
确认密钥文件路径在 PowerShell 中运行以下命令，进入你的 SSH 密钥目录：
```PYTHON
cd $HOME\.ssh
```
查看目录内容，确认公钥文件存在：
ls
你应该看到 id_ed25519 (私钥) 和 id_ed25519.pub (公钥) 两个文件。

步骤 2: 复制公钥内容
我们将使用 cat 命令来读取公钥文件的内容，然后复制它。
读取公钥内容（请使用你实际的公钥文件名）：
```PYTHON
cat id_ed25519.pub
```
PowerShell 会显示一长串字符，例如：
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICe3hCj...wNn...d5 your_email@example.com
请将显示出的这一整行内容全部复制下来。

步骤 3: 登录vps并添加公钥
在 VPS 上执行以下命令：
1. 确保 .ssh 目录存在并设置正确权限 (700)
```PYTHON
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```
2. 将公钥内容追加到 authorized_keys 文件中
我们使用 echo 命令配合单引号，确保内容完全不被修改
```PYTHON
echo '公钥' >>~/.ssh/authorized_keys
```
3. 设置 authorized_keys 文件权限 (600)
```PYTHON
chmod 600 ~/.ssh/authorized_keys
```
重要提示： 在运行 echo 命令时，请将 '...' 中的文本替换为你刚才复制的公钥内容，不要遗漏任何字符。
退出 VPS 会话：
```PYTHON
exit
```
验证连接
现在，回到你的 PowerShell，不带密码，再次尝试连接：
```PYTHON
ssh   -p 33213 root@192.220.58.36
```
修改ssh配置文件，开启密钥登录，关闭密码登录
```PYTHON
sudo nano /etc/ssh/sshd_config
```
PubkeyAuthentication yes
PasswordAuthentication no
交互登录
ChallengeResponseAuthentication no
重启ssh服务
```PYTHON
sudo systemctl restart ssh
```
把 root 的 SSH 钥匙“复制”给 bage：
```PYTHON
# 1. 创建 .ssh 目录
mkdir -p /home/bage/.ssh

# 2. 把 root 的授权公钥复制过去
cp /root/.ssh/authorized_keys /home/bage/.ssh/authorized_keys

# 3. 把目录和文件的所有权给 bage 用户
chown -R bage:bage /home/bage/.ssh

# 4. 修改权限（极其关键，权限不对 SSH 会拒绝）
chmod 700 /home/bage/.ssh
chmod 600 /home/bage/.ssh/authorized_keys
```