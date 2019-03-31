# Ansible-AWX

System Requirements for AWX Server
At least 4GB of memory.
At least 2 cpu cores.
At least 20GB of space.
Disable firewalld

```
systemctl stop firewalld 
systemctl disable firewalld
```
Enable epel repo
```
yum install -y epel-release
```
Install the packages
```
yum install -y yum-utils device-mapper-persistent-data lvm2 ansible git python-devel python-pip python-docker-py vim-enhance
```
Configure docker ce stable repository
```
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Installing docker,start docker service,enable docker service
```
yum install docker-ce -y
systemctl start docker
systemctl enable docker
```
Cloning the AWX repo
```
https://github.com/kolomyya/Ansible-AWX.git
```
Go into the installer directory within /root/Ansinle-AWX
```
cd awx
cd installer/
```
Edit the following parameters in inventory

vim inventory 
postgres_data_dir=/var/lib/pgdocker 
awx_alternate_dns_servers="8.8.8.8"
awx_official=true 
project_data_dir=/var/lib/awx/projects 
Now deploying AWX via Docker
```
ansible-playbook -i inventory install.yml -vv
```
AWX is ready and can be accessed from the browser

username is "admin" and the password is "password"


