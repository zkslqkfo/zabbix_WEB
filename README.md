# 실무에서 꼭 필요한 서버 모니터링(Zabbix)

## 설치 환경

```
OS : Amazon Linux 2
모니터링 : Zabbix 5.0
DB : MySQL 5.7
WEB : Nginx
언어 : PHP 7.2
```

-----


## Zabbix Server 설치
```
amazon-linux-extras install epel -y
rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm
rpm -Uvh https://rpmfind.net/linux/centos/7.9.2009/extras/x86_64/Packages/centos-release-scl-rh-2-3.el7.centos.noarch.rpm
rpm -Uvh https://rpmfind.net/linux/centos/7.9.2009/extras/x86_64/Packages/centos-release-scl-2-3.el7.centos.noarch.rpm
yum install zabbix-web-mysql-scl
yum install zabbix-nginx-conf-scl
yum install zabbix-server-mysql.x86_64
rpm -ivh https://dev.mysql.com/get/mysql80-community-release-el7-1.noarch.rpm
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
yum -y install mysql-community-server --disablerepo=mysql80-community --enablerepo=mysql57-community
```

-------

## Zabbix agent 설치
```
amazon-linux-extras install epel -y
rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm
rpm -Uvh https://rpmfind.net/linux/centos/7.9.2009/extras/x86_64/Packages/centos-release-scl-rh-2-3.el7.centos.noarch.rpm
rpm -Uvh https://rpmfind.net/linux/centos/7.9.2009/extras/x86_64/Packages/centos-release-scl-2-3.el7.centos.noarch.rpm
yum install -y zabbix-agent

```

## Zabbix agent 설치
```
```
