---
title: Linux搭建SSR
date: 2020-04-11 14:21:31
tags:
  - Linux
  - SSR
---

## 购买 VPS

### 选择 VPS 服务商

推荐 [Vultr](https://www.vultr.com/) 可以随时更换主机  
现在主机贵了，能用做 VPS 的起步 \$5/month  
充值最少\$10

### 选择服务器

- 位置

  人在大陆的话选日本的主机比较快，但据说也容易被封  
  查 IP 网址<https://ip.cn/>

- 价格

  价位选最便宜的就好，不过必须支持 IPv4

- 系统

  推荐*CentOS 7 x64*  
  据说更高版本可能失败，我也没试过  
  只为转发数据而已，高版本也没什么意义

## 为 VPS 安装 SSR 服务

### SSH 连接 VPS

`ssh root@server_ip`

能连上就输入服务商给的密码，不能就再部署一个，最后把旧的删除

密码在 manage 中可以找到

测试能否访问到需要访问的网站

`ping google.com`

效果满意则安装 SSR 服务

`wget -N --no-check-certificate https://raw.githubusercontent.com/luvvien/ssr-install-shellscript/master/ssr.sh`

### 开始安装程序

`chmod +x ssr.sh && bash ssr.sh`

开始安装(括号内为我的选择)

- 输入 1 开始安装 SSR
- 输入端口号(10086)
- 输入密码(\*\*\*\*\*\*\*\*\*)
- 选择加密方式(7: aes-256-ctr)
- 选择协议(3: auth_aes128_md5)
- 选择混淆(1: plain)
- 设置客户端数量(默认: 无限)
- 设置单线程限速上限(默认: 无限)
- 设置总速度限速上限(默认: 无限)

- 等待安装完成

中途会有一些确认操作  
安装完成后会给出 SSR 配置信息，配置信息在配置客户端时会用到，可以先保存到一个文本里  
还会给出 SSR 链接和 SSR 二维码，可以方便的配置 windows 和 android 的 SSR 客户端

## 下载 SSR 客户端

### Linux

- 下载 [ssr 安装脚本](/download/ssr)

- 放到到`/usr/local/bin/`下，可以随时通过命令开启

  `sudo mv ssr /usr/local/bin`

- 安装 ssr 客户端

  `sudo ssr install`

- 进行 ssr 配置

  `sudo ssr config`

- 配置信息填安装服务器时的信息，主要有:

  | 字段        | 含义         |
  | :---------- | :----------- |
  | server      | 服务器 IP    |
  | server_port | 服务器端口号 |
  | password    | 密码         |
  | method      | 加密方式     |
  | protocol    | 协议         |
  | obfs        | 混淆         |

- 需要启动时

  `sudo ssr start`

- 需要停止时

  `sudo ssr stop`

- 查看更多指令
  `sudo ssr help`

### windows

- 下载[windows 客户端](https://github.com/shadowsocksr-backup/shadowsocksr-csharp/releases)

- 通过 ssr 链接进行配置

### android

- 下载[android 客户端](https://github.com/shadowsocksr-backup/shadowsocksr-android/releases)
- 通过 ssr 链接或 ssr 二维码进行配置

## 代理白名单

`https://github.com/gfwlist/gfwlist/blob/master/gfwlist.txt`
