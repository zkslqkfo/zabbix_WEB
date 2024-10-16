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
Zabbix 및 필수 툴 설치 [ PHP 7.2 이상 ]
Amazon Linux 2023에서는 대신 "Extra Packages for Enterprise Linux (EPEL)" 레포지토리 활성화
sudo amazon-linux-extras install epel -y

Zabbix 레포지토리 설치
rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm

Amazon Linux 사용 시 패키지 누락으로 인한 추가 설치
yum clean all

vi /etc/yum.repos.d/zabbix.repo
[zabbix-frontend]
[zabbix-debuginfo]
enabled=1 활성화

sudo vi /etc/yum.repos.d/CentOS-SCLo-scl.repo
[centos-sclo-rh]
name=CentOS-7 - SCLo rh
baseurl=http://vault.centos.org/7.9.2009/sclo/x86_64/rh/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

[centos-sclo-sclo]
name=CentOS-7 - SCLo sclo
baseurl=http://vault.centos.org/7.9.2009/sclo/x86_64/sclo/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

GPG 키 수동 다운로드
sudo mkdir -p /etc/pki/rpm-gpg
sudo curl -o /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7 https://vault.centos.org/7.9.2009/os/x86_64/RPM-GPG-KEY-CentOS-7
yum clean all

Zabbix-web-mysql 패키지 설치
yum install zabbix-web-mysql-scl

Zabbix-nginx 패키지 설치
yum install zabbix-nginx-conf-scl

Zabbix Server 설치 (mysql)
yum install zabbix-server-mysql.x86_64

MySQL 설치
레포지토리 추가
rpm -ivh https://dev.mysql.com/get/mysql80-community-release-el7-1.noarch.rpm

[root@ip-172-31-44-100 ec2-user]# yum repolist all | grep mysql | grep enabled
mysql-connectors-community/x86_64         MySQL Connectors C enabled:     183+59
mysql-tools-community/x86_64              MySQL Tools Commun enabled:        104
mysql80-community/x86_64                  MySQL 8.0 Communit enabled:        465

MySQL 5.7 설치
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

