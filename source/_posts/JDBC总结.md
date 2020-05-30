---
title: JDBC总结
date: 2020-05-30 16:37:14
tags:
- Java
- MySql
---

## 导入驱动包
```
// 导入驱动包
Class.forName("com.mysql.cj.jdbc.Driver");
```
## 与数据库建立链接
```
// 与数据库建立链接
connection = DriverManager.getConnection(dbURL, userName, userPassword);
```
## 获取操作数据库对象
```
// 获取操作数据库对象
PreparedStatement pStatement = connection.prepareStatement(sqlString);
// 增删改
pStatement.executeUpdate();
// 查询
pStatement.executeQuery();
```
