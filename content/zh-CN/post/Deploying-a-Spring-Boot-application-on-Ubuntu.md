---
title: "Ubuntu 服务器部署 Spring Boot 应用"
date: 2021-01-05T20:26:08+08:00
tags: ["Spring Boot", "Java", "MySQL", "Ubuntu"]
draft: false
---

## 1. 部署环境说明
* 数据库：MySQL 5.7.31
* 服务器环境：Ubuntu 18.04 (x86, 64-bit)
* Spring Boot 应用已打包为 JAR 包
* Java Version：Java(TM) SE Runtime Environment (build 1.8.0_261-b12)

## 2. Java环境安装
### 2.1 Ubuntu 安装 Java环境（JDK 1.8）
[Java SE Development Kit 8u261 Download](https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html#:~:text=linux%2Dx64.rpm-,Linux%20x64%20Compressed%20Archive,-85.55%20MB)

•	创建安装目录
```shell
mkdir /usr/local/java/
```

•	将 jdk 文件解压至安装目录
```shell
tar -zxvf jdk-8u261-linux-x64.tar.gz -C /usr/local/java/
```

### 2.2 设置环境变量
•  打开文件
```shell
vi /etc/profile
```

•	在末尾添加
```shell
export JAVA_HOME=/usr/local/java/jdk1.8.0_261
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```

•	刷新环境变量使其生效
```shell
source /etc/profile
```

•	检查 Java  版本
```shell
java -version
```

•	成功安装显示版本信息
```shell
java version "1.8.0_261"
Java(TM) SE Runtime Environment (build 1.8.0_261-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.261-b12, mixed mode)
```

## 3. MySQL 数据库安装
### 3.1 下载安装
参考 [Ubuntu 18.04 安装 MySQL 5.7](https://oddfry.github.io/blog/zh-cn/post/install-mysql-5.7-on-ubuntu-18.04/)

### 3.2 配置数据库
•	修改登陆密码
```shell
# 使用数据库
use mysql;
# 修改密码
ALTER USER USER() IDENTIFIED BY 'NEW PASSWORD';
```

•	检查默认字符编码
```sql
mysql> show variables like 'character_set_%';
```
•	结果如下
```sql
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | latin1                     |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | latin1                     |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.00 sec)
```

•	修改字符编码，防止中文写入数据库错误
```shell
vi /etc/mysql/mysql.conf.d/mysqld.cnf
# 在文件最后添加一行
character-set-server=utf8
# 重启 MySQL
service mysql restart
```

•	再次查看字符编码
```sql
mysql> show variables like 'character_set_%';
```
•	结果如下
```sql
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       |
| character_set_connection | utf8                       |
| character_set_database   | utf8                       |
| character_set_filesystem | binary                     |
| character_set_results    | utf8                       |
| character_set_server     | utf8                       |
| character_set_system     | utf8                       |
| character_sets_dir       | /usr/share/mysql/charsets/ |
+--------------------------+----------------------------+
8 rows in set (0.01 sec)
```

•	启用远程连接，修改配置文件
```shell
vi /etc/mysql/mysql.conf.d/mysqld.cnf
# 接受所有服务器主机 IPv4 接口上的 TCP/IP 连接
bind-address = 0.0.0.0
# 重启 MySQL
service mysql restart
```

•	开启 MySQL 远程访问权限，允许远程连接
```sql
grant all on *.* to admin@'%' identified by 'PASSWORD' with grant option;
```

•	刷新服务
```sql
flush privileges;
```

### 3.3 创建项目所需数据表
```sql
CREATE TABLE IF NOT EXISTS `PROJECT_TABLE`(
   ...
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

## 4. 项目上线部署
### 4.1 上传项目
•	开发端将项目打包为 JAR 包，命名为：`<PROJECT>.jar`，上传至服务器 `/usr/local/<PROJECT>/` 目录下
### 4.2 部署项目
•	利用 `nohup` (no hang up) 不挂断运行命令，当会话关闭时，仍然运行程序
```shell
nohup java -jar <PROJECT>.jar >output.log 2>&1 &
```
> 将标准错误 2 重定向到标准输出 1 中，而标准输出又重定向到文件 output.log 中，最终将标准错误和标准输出都写入至文件 output.log 中

| 命令 | 作用 |
| ------ | ------ |
| & | 让程序在后台运行，会话关闭时运行终止 |
| nohup java -jar \<PROJECT>.jar & | 会话关闭后程序仍在后台运行 |
| 2>&1 | 将标准错误 2 重定向到标准输出 1 中 |