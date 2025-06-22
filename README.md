# ubuntu2504notes
Notes on setting up Ubuntu 25.04 on VM
## Initial host setup
```
apt-get update
apt-get upgrade

hostnamectl --pretty set-hostname "knode204 - control"
hostnamectl set-hostname knode204.kozik.net
```
## Install Git
```
apt install git
git config --global user.name "Jack Kozik"
git config --global user.email "jackkozik@email.com"
git config --list
user.name=Jack Kozik
user.email=jackkozik@email.com
```
## Install NFS Client
I have NFS servers on my home LAN.  I will be mounting them on to this VM
```
apt install nfs-common
showmount -e 192.168.101.152
Export list for 192.168.101.152:
/home/nfs/pv-2            192.168.100.0/24
/home/nfs/pv-1            192.168.100.0/24
/home/nfs/zabbix/enc      192.168.100.0/24
/home/weewx/nfs/archive   192.168.100.0/24
/home/weewx/nfs/conf      192.168.100.0/24
/home/nfs/kubedata        192.168.100.0/24
/home/weather/public_html 192.168.100.0/24
/home/wjr/public_html     192.168.100.0/24
/var/nfsshare             192.168.100.0/24
```
## Time Zone
```
timedatectl list-timezones | grep Chicago
America/Chicago
timedatectl set-timezone America/Chicago
```

## Update .ssh/config file
```
Host knode204
  HostName 192.168.100.204
  User jkozik
  IdentityFile ~/.ssh/052720id_rsa
```
