---
layout: default
title: 关于项目
---

# 关于项目
{:.no_toc}

* 目录
{:toc}

| 版本 |   日期    | 描述 |   作者    |
| :--: | :-------: | :--: | :-------: |
| v2.0 | 2019-6-29 | 完成 | chenjifan |

## 1、项目简介
**闲钱袋鼠**是一个微信小程序，主营学生之间日常生活中一些小任务的发布和完成。

* 功能：
它以微信作为入口，用户既可以作为发布者在上面发布任务寻求帮助，也可浏览他人的任务并完成来获取一定报酬。

* 产品特点：
1. 任务多样，包括：实际生活中的事项，填写调查问卷，信息等资源有偿分享。
2. 支持代币免费提现到微信，赚取报酬看得见。
3. 操作简单，任务迅速发布，无需审核，效率至上。
4. 只支持在校学生使用，使用学号、姓名、手机信息就可以快速注册成为新用户，界面、任务种类等设计紧密贴合大学生群体。

## 2、界面展示

![](/images/zs1.png)

![](/images/zs2.png)

## 3、重要分析设计文档

* [需求规格说明书（暂无）](06-requirements)
* [软件设计说明书（暂无）](07-designs)
* [产品演示视频（暂无）]()

## 4、项目结构
* 微信小程序前端：
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
* 服务器端
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

## 5、敏捷开发迭代管理

#### Iteration 1
* goals:
    - makes tech prototype for something
    - builds a proto system to demostrate core scene
    - collects 50% requirments scene stories

#### Inceptions（week6~7）
* goal: 完成产品设计
* 前期工作：
    - 产品调查
    - 团队组织
    - 需求分析
    - 架构等设计
* 项目启动会议：所有人
* 项目愿景等文档

#### Iteration 2
* goals:
    - 完成大部分代码

#### Inceptions（week7~12）
* goal: 完成产品大体模型，前后端独立完成
* 工作：
    - 团队组织
    - 技术学习
    - 代码实现
* 项目启动会议：所有人
* 技术文档：产品经理，工程师

#### Iteration 3
* goals:
    - 对接测试等
    - 文档

#### Inceptions（week13~16）
* goal: 前后段对接完成，完成测试，完成文档
* 工作：
    - 团队组织
    - 技术学习
    - 代码实现
* 项目启动会议：所有人
* 技术文档：产品经理，工程师