# 架构设计文档

## 后端架构图
![架构图](/images/04-jiagou.png)  

## Web服务器架构
### 控制层

包括认证系统、任务controller、任务单controller、用户信息controller和登陆注册controller。  
![架构图](/images/04-con.png)  

### 服务层

包括账户管理系统、任务管理系统、用户信息管理系统、任务单管理系统。  
![架构图](/images/04-ser.png)   

### 持久层

使用RabbitMQ处理延迟消息，MySQL作为数据库，Redis作为缓存数据库。  
项目内使用MyBatis与MySQL连接。

### 项目总目录

![架构图](/images/04-mulu1.png)  
![架构图](/images/04-mulu2.png)  
![架构图](/images/04-mulu3.png)  

## 前端
使用微信小程序提供的wxml+wcss+js