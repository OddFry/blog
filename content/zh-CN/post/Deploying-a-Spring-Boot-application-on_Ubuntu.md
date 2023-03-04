---
title: "Deploying a Spring Boot Application On_Ubuntu"
date: 2023-03-04T16:54:08+08:00
draft: false
---

## 1. 部署环境说明
数据库：MySQL 5.7
服务器环境：Ubuntu 18.04 64bit
Spring Boot 应用已打包为 JAR 包
Java Version：Java(TM) SE Runtime Environment (build 1.8.0_261-b12)
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
•	安装 MySQL
```shell
yum install mysql-server
```

•	启动MySQL服务
```shell
# 启动 MySQL 服务
service mysqld start
# 查看 MySQL 服务状态
service mysqld status
```

•	查看初始密码
```shell
grep "password" /var/log/mysqld.log
```

•	登陆MySQL
```shell
# 登录 MySQL
mysql -u root -p
# 输入刚才查询的初始密码
```

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

•	修改字符编码
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

•	开启 MySQL 远程访问权限，允许远程连接
```sql
grant all on *.* to admin@'%' identified by 'password' with grant option;
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
•	开发端将项目打包为 JAR 包，命名：<PROJECT>.jar
•	上传至服务器 /usr/local/<PROJECT> 下
### 4.2 部署项目
•	利用 nohup 不挂断运行命令,当账户退出或终端关闭时,仍然运行项目
```shell
nohup java -jar <PROJECT>.jar >output 2>&1 &
```

> 2>&1 作用
把标准错误（2）重定向到标准输出中（1），而标准输出又导入进文件output里，最终将标准错误和标准输出都导入文件 /usr/local/<PROJECT>/output 里面。 