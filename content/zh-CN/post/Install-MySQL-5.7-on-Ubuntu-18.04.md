---
title: "Ubuntu 18.04 安装 MySQL 5.7"
subtitle: "以安装 MySQL 5.7.31 为例"
date: 2020-12-27T11:30:58+08:00
tags: ["MySQL", "Ubuntu"]
draft: false
---

## 下载
创建下载文件夹并进入
```shell
mkdir mysql ; cd $_
```
下载 [MySQL DEB Bundle 安装包](https://downloads.mysql.com/archives/community/)
```shell
wget https://downloads.mysql.com/archives/get/p/23/file/mysql-server_5.7.31-1ubuntu18.04_amd64.deb-bundle.tar
```
解压安装包
```shell
tar -xvf mysql-server_5.7.31-1ubuntu18.04_amd64.deb-bundle.tar
```

## 安装
更新软件源列表
```shell
sudo apt-get update
```
根据依赖关系逐个安装，参考 [MySQL 数据库的下载、安装和测试](https://www.cnblogs.com/librarookie/p/14001729.html)
```shell
# libmysqlclient20_5.7.31和libmysqlclient-dev_5.7.31 依赖common
sudo dpkg -i mysql-common_5.7.31-1ubuntu18.04_amd64.deb

sudo dpkg -i libmysqlclient20_5.7.31-1ubuntu18.04_amd64.deb

sudo dpkg -i libmysqlclient-dev_5.7.31-1ubuntu18.04_amd64.deb

# libmysqld-dev_5.7.31依赖libmysqlclient20_5.7.31和libmysqlclient-dev_5.7.31
sudo dpkg -i libmysqld-dev_5.7.31-1ubuntu18.04_amd64.deb

sudo dpkg -i mysql-community-source_5.7.31-1ubuntu18.04_amd64.deb 

# community-client依赖libaio1，community-server依赖libmecab2
sudo apt-get install libaio1 libmecab2

# 如果上面依赖包安装后还不行就执行，该命令是解决系统全局所有依赖包问题
sudo apt-get install -f

# ubuntu 18.04 安装mysql-community-server时，除了上面依赖，还依赖mysql-client（sudo dpkg -i mysql-client_5.7.31-1ubuntu18.04_amd64.deb）
sudo dpkg -i mysql-community-client_5.7.31-1ubuntu18.04_amd64.deb 

# 安装时这个包时，会让输入两次MySQL密码，装完这步 MySQL就就可以登录了
sudo dpkg -i mysql-community-server_5.7.31-1ubuntu18.04_amd64.deb

# mysql-server依赖community-server
sudo dpkg -i mysql-server_5.7.31-1ubuntu18.04_amd64.deb
```

启动 MySQL 服务
```shell
# 查看 MySQL 服务状态，输入 q 退出
service mysqld status
# 启动 MySQL 服务
service mysqld start
# 停止 MySQL 服务
service mysql stop
```

查看初始密码
```shell
grep "password" /var/log/mysqld.log
```

登陆 MySQL
```shell
# 登录 MySQL
mysql -u root -p
# 输入刚才查询的初始密码
```