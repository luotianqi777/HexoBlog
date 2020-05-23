---
title: Linux安装配置MySQL
date: 2020-05-23 10:33:11
tags:
- Linux
- MySQL
---

## 本文特指MySQL8

## 安装MySQL
`sudo apt install mysql-server mysql-client`

## 配置MySQL

> 通过管理员权限进入MySQL终端

### 修改密码安全等级
> 密码安全度(0,1,2)由低至高

`set global validate_password.policy=0;`

### 添加用户

`CREATE user 'user'@'host' IDENTIFIED BY 'password';`

### 更改密码

`ALTER user 'user'@'host' IDENTIFIED WITH mysql_native_password BY 'password';`

### 添加所有权限

`GRANT ALL ON *.* TO 'user'@'host' WITH GRANT OPTION;`

### 刷新权限

`FLUSH PRIVILEGES;`
