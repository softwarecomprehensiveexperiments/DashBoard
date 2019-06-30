# 1.逻辑架构
逻辑架构由三层模型（表示层、控制层、业务层、持久化层）构成

## 1.1 表示层
- 顾客端使用微信小程序作为表示层，提供用户任务管理子系统、用户任务单子系统、用户管理子系统

## 1.2 控制层

- 服务器包含了控制层 ，接受来自表示层的请求并调用相关服务           

## 1.3 业务层

- 服务器充当业务层的角色，为控制层的各个子系统提供相应的服务模块

## 1.4 持久化层

- MySQL 提供了数据的持久化服务
- Redis 提供了token相关数据的持久化服务
- RabbitMQ 提供了延迟消息相关数据的持久化服务

# 2.框架目录设计
## 2.1. 小程序
```
.
├── utils
│   └── ...
├── icons
│   └── ...
├── pages
│   ├── index
│   │   ├── index.wxml
│   │   └── index.wxss
│   │   ├── index.js
│   │   └── index.json
│   ├── index2
│   │   ├── ...
│   │   ├── ...
│   │  
|   └── ...
├── app.js
├── app.json
├── app.wxss
└── ...
```

## 2.2.后端
```
.
├── java
│   ├── Constant                # 常量类
|   |   ├── TokenConstant 
|   |   └── ...
│   ├── Dao                     # 持久层，与数据库对接
|   |  ├── UserMapper
|   |  └── ...
│   ├── Domain               # 对象模型
|   |   ├── User
|   |   └── ...
│   ├── DTO               # 传输对象模型
|   |   └── ...
│   ├── Exception           # 异常类
|   |   └── ...
│   ├── JWT               # JWT操纵类
|   |   ├── JWT Utils
|   |   └── ...
│   ├── RabbitMQ               # RabbitMQ操纵类
|   |   └── ...
│   ├── Redis             # Redis操纵类
|   |   └── ...
│   ├── Service             # 服务层
|   |   └── ...
│   ├── Utils             # 工具类
|   |   └── ...
│   ├── Web            # 控制层
|   |   └── ...
├── resources
│   ├── mapper            # MyBatis xml表
|   |   └── ...
│   ├── application.properties            # 程序配置
│   ├── mybatis-config.xml   # MyBatis配置
└── └── mytable.xml       # MySQL初始化语句
```

# 3.与 ECB 关系
ECB中：

- Entity：代表系统数据，如：任务单、任务、用户等
- Boundary：与用户的接口，如：界面、请求等
- Controller：在 Boundary 和 Entity 中衔接的媒介，编排来自 Boundary 的命令的执行

在本系统中，Boundary包括：

- 顾客端小程序用户界面

Controller 包含：

- 服务器框架目录设计中，`controller` 目录下定义了所有的相关内容，它们接收来自上述 Boundary 的命令，并编排 `service` 的执行
- 服务器框架目录设计中，`service` 目录下定义了部分相关内容，它们接收也会对来自 Boundary 的命令进行相应的编排

Entity 包含：

- 服务器框架目录设计中，`Domain` 目录下定义了所有服务器与 MySQL 相关的实体，承载系统数据
- 服务器与 Redis 通讯的相关部分
- 服务器与 RabbitMQ通讯的相关部分