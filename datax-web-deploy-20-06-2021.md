## System requirements

- Language：Java8（jdk版本建议1.8.201以上）
- Python2.7（支持Python3需要替换datax-home/bin/datax.py文件，替换文件在doc/datax-web/datax-python3下）
- Environment：MacOS，Windows，Linux
- MySQL5.7

## 环境准备

### 安装基础软件

#### JDK

```shell
ubuntu@ip-172-24-31-9:~$ sudo apt-get install openjdk-8-jdk
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package openjdk-8-jdk
ubuntu@ip-172-24-31-9:~$
```

```shell
ubuntu@ip-172-24-31-9:~$ sudo add-apt-repository ppa:webupd8team/java
ubuntu@ip-172-24-31-9:~$ sudo apt-get update -y
ubuntu@ip-172-24-31-9:~$ sudo apt install openjdk-8-jdk -y
```



#### MySQL

必须安装，建议安装5.5+版本，对应客户端可以选装，若安装MySQL客户端可以通过部署脚本快速初始化数据库。

```shell
ubuntu@ip-172-24-31-9:~$ sudo apt-get update
ubuntu@ip-172-24-31-9:~$ sudo apt-get install mysql-server
ubuntu@ip-172-24-31-9:~$ sudo service mysql start
ubuntu@ip-172-24-31-9:~$ sudo cat /etc/mysql/debian.cnf
# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = iRNb2YUeIG2UeeWy
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = iRNb2YUeIG2UeeWy
socket   = /var/run/mysqld/mysqld.sock
ubuntu@ip-172-24-31-9:~$ sudo mysql -udebian-sys-maint -piRNb2YUeIG2UeeWy
mysql>use mysql;
mysql>update user set authentication_string=PASSWORD("123456") where user='root';
mysql>update user set plugin="mysql_native_password";
mysql>GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '123456' WITH GRANT OPTION;
mysql>flush privileges;
mysql>exit;
ubuntu@ip-172-24-31-9:~$ sudo service mysql restart
ubuntu@ip-172-24-31-9:~$ sudo mysql -uroot -p123456
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 5.7.34-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

