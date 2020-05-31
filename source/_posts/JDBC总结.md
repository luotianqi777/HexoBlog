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
```
## 执行语句
```
// 增删改
pStatement.executeUpdate();
// 查询
pStatement.executeQuery();
```
## 处理查询结果
```
result = pStatement.executeQuery();
while(result.next()){
    result.getXxx(...);
    ...
}
```
## 关闭链接
```
// 先打开的链接后关闭 类似堆栈
if(result!=null){
    result.close();
}
if(pstatement!=null){
    pstatement.close();
}
if(connection!=null){
    connection.close();
}
```