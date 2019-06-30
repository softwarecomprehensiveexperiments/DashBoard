# 安装包与前后端部署说明

## 服务器部署说明
后端已部署在云服务器中

* 服务器系统：CentOS 7
* IP地址：118.89.117.52
* 部署工具：Docker
* 容器：共四个容器，分别部署：Spring Boot（Web服务器），Redis（缓存数据库），MySQL（数据库），RabbitMQ（消息队列）
* 容器端口映射：
  + Spring Boot：80:8080（主机端口:容器端口）
  * Redis：6379:6379
  * MySQL：3306:3306
  * RabbitMQ：15672:15672，5672:5672，25672:25672，61613:61613，1883:1883
* 容器间通信：container模式，所有容器共享Redis容器的network
  
## 部署步骤

### Redis
1. 安装latest版本
2. 配置文件
    ```
    # redis默认不是以守护进程的方式运行，可以通过该配置项修改，使用yes启用守护进程
    deamonize yes
    # 你可以绑定单一接口，如果没有绑定，所有接口都会监听到来的连接
    #  bind 127.0.0.1
    # 因为redis本身同步数据文件是按上面save条件来同步的，所以有的数据会在一段时间内只存在于内存中。默认为no
    appendonly yes
    # 设置Redis连接密码，如果配置了连接密码，客户端在连接Redis时需要通过
    # requirepass 123456
    rename-command CONFIG someverylongandveryunguessablestring1234
    ```
3. 运行
```
docker run -p 6379:6379 -p 15672:15672 -p 5672:5672 -p 25672:25672 -p 61613:61613 -p 1883:1883 -p 80:8080 -p 3306:3306 -v $PWD/redis.conf:/etc/redis/redis.conf -v $PWD/data:/data -d redis redis-server /etc/redis/redis.conf --appendonly yes
```

### Spring boot

* 生成镜像： 

1. 使用maven生成jar包  

2. 编写dockerfile   

    ```
    #指定基础镜像，在其上进行定制
    FROM java:8
    #这里的 /tmp 目录就会在运行时自动挂载为匿名卷，任何向 /tmp 中写入的信息都不会记录进容器存储层
    VOLUME /tmp
    
    ADD target/backup-1.0.jar backup-1.0.jar
    
    #bash方式执行，使demo-1.0.0.jar可访问
    #RUN新建立一层，在其上执行这些命令，执行结束后， commit 这一层的修改，构成新的镜像。
    RUN bash -c "touch /backup-1.0.jar"
    
    #声明运行时容器提供服务端口，这只是一个声明，在运行时并不会因为这个声明应用就会开启这个端口的服务
    EXPOSE 8080
    
    #指定容器启动程序及参数   <ENTRYPOINT> "<CMD>"
    ENTRYPOINT ["java","-jar","backup-1.0.jar"]
    ```
3. IDEA连接到Docker服务器并配置  
   ![配置图](/images/01-sdoc.png)  
4. 在服务端生成镜像  
   ![配置图](/images/01-serdoc.png)   

* 部署：
运行代码  
```
docker run -d --name backup-server --network container:736 kangaroo-backup:2.52
```

### MySQL
1. 安装latest版本  
2. 配置文件  
![配置图](/images/01-sp.png)  
3. 运行代码  
```
docker run --name mysql --network container:736 -e MYSQL_ROOT_PASSWORD=chen -d mysql
```

### RabbitMQ
1. 安装latest版本  
2. 运行代码  
```
docker run -d --network container:736 --name rabbit -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=admin rabbitmq:management
```

## 前端部署说明

### 安装包
本项目是基于微信小程序平台开发的web小程序，不需要通过安装包进行安装。  

**由于小程序无法完成微信小程序的审核，需要使用可联系小组组长(微信/QQ：1004920224)，加入测试人员名单即可正常使用**

### 源代码
后端Github仓库：[链接](https://github.com/softwarecomprehensiveexperiments/pocket-kangaroo-backup)  

前端Github仓库：[链接](https://github.com/softwarecomprehensiveexperiments/pocket-kangaroo-frontend)  

### 安装部署

添加开发项目    
![配置图](/images/01-kaifa.png)  

注册导入  
![配置图](/images/01-daoru.png)  

绑定成员信息并发布  
![配置图](/images/01-fabu.png)  