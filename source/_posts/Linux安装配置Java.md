---
title: Linux安装配置Java
date: 2020-05-12 11:22:14
tags:
  - Linux
  - Java
---

## 安装 Java

推荐安装 Java8

### openjdk

`sudo apt install openjdk-8-jdk`

`sudo apt install openjdk-8-jre`

### Oracle

[官网](https://www.oracle.com/java/technologies/javase-downloads.html)下载

下载时注意同意许可协议。

下载完解压，建议放到`/usr/local/jdk_version`目录下

编辑`/etc/profile`文件，添加系统变量

```
JAVA_HOME=/usr/local/jdk_version
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
```

更新

`sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/jdk_version/bin/java" 1`

`sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/jdk_version/bin/javac" 1`

`sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/jdk_version/bin/javaws" 1`

设置

`sudo update-alternatives --set java /usr/local/jdk_version/bin/java`

`sudo update-alternatives --set java /usr/local/jdk_version/bin/javac`

`sudo update-alternatives --set java /usr/local/jdk_version/bin/javaws`

## 检测安装版本

`java -version`
