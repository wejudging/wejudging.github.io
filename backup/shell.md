**开启root远程登录**

```bash
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
systemctl restart sshd
```

**安装docker**
```bash
curl -fsSL https://get.docker.com | bash -s docker
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

