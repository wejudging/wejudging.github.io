**开启root远程登录2**

```bash
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
systemctl restart sshd
```

**官网安装docker**
```bash
curl -fsSL https://get.docker.com | bash -s docker
systemctl start docker
systemctl enable docker
```

**国内安装docker**
```bash
bash <(curl -sSL https://linuxmirrors.cn/docker.sh)
systemctl start docker
systemctl enable docker
```

**BBR-PLUS脚本**
```bash
bash <(curl -Lso- https://git.io/kernel.sh)
```

**centos关闭防火墙**
```bash
systemctl stop firewalld
systemctl disable firewalld
```

**swap**
```bash
wget https://www.moerats.com/usr/shell/swap.sh && bash swap.sh
azure swap
dd if=/dev/zero of=/swapfile count=4096 bs=1M
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
vi /etc/fstab
/swapfile   none    swap    sw    0   0
```

**myip**
```bash
ip=$(curl -s http://myip.ipip.net)
echo "My public IP address is: $ip"
```

**danate**
```bash
wget --no-check-certificate https://raw.github.com/Lozy/danted/master/install.sh -O install.sh
bash install.sh  --port=18888 --user=weijiajin --passwd=weijiajin

/etc/init.d/sockd adduser USERNAME PASSWORD
sudo sed -i 's/del_uer/del_user/g' /etc/init.d/sockd
/etc/init.d/sockd deluser USERNAME
bash install.sh --uninstall
systemctl enable sockd.service
service sockd state
/etc/init.d/sockd state
```

**增加网卡**
```bash
ifconfig eth0:1 10.0.0.5 up
ifconfig eth0:2 10.0.0.6 up
```

**x-ui**
```bash
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```
**重装系统 Debain12**
```bash
apt install wget -y
wget --no-check-certificate -qO InstallNET.sh 'https://raw.githubusercontent.com/leitbogioro/Tools/master/Linux_reinstall/InstallNET.sh' && chmod a+x InstallNET.sh
bash InstallNET.sh -debian

For Linux: LeitboGi0ro
```

**debian10安装docker**
```bash
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common
y
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo \ "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
y
git clone https://github.com/wejudging/x-ui.git
cd x-ui
docker compose up -d
```

**重装系统Debain12**
```
curl -O https://raw.githubusercontent.com/bin456789/reinstall/main/reinstall.sh || wget -O reinstall.sh $_
bash reinstall.sh debian 12 --password password
```

**下载新的yum源**
```
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.cloud.tencent.com/repo/centos6_base.repo
```

**清除yum缓存并更新**
```
yum clean all
yum makecache
```

**debian10安装x-ui**
```
commands = [
        "sudo apt-get update",
        "sudo apt-get install apt-transport-https -y",
        "sudo apt-get install ca-certificates -y",
        "sudo apt-get install curl -y",
        "sudo apt-get install gnupg2 -y",
        "sudo apt-get install software-properties-common -y",
        "curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg",
        "echo \"deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable\" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null",
        "sudo apt-get update",
        "sudo apt-get install docker-ce docker-ce-cli containerd.io -y",
        "git clone https://github.com/wejudging/x-ui.git",
        "cd /root/x-ui && docker compose up -d"
    ]
```

**测速**
```
wget http://updates-http.cdn-apple.com/2019WinterFCS/fullrestores/041-39257/32129B6C-292C-11E9-9E72-4511412B0A59/iPhone_4.7_12.1.4_16D57_Restore.ipsw
```
