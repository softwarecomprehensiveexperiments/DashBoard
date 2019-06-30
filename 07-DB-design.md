## 数据库设计文档

- ### 1.系统数据需求  
  + #### 1.1功能数据需求

- ### 2.概念设计
  + #### 2.1ER图

- ### 3.逻辑设计
  + #### 3.1表设计
    - ##### 3.1.1 User表
    - ##### 3.1.1 task表
    - ##### 3.1.1 LoginLog表
    - ##### 3.1.1 Transaction表
    - ##### 3.1.1 questionaire表
    
- ### 1.系统数据需求
  + #### 1.1功能数据需求
   为本小程序“闲钱袋鼠”建立一个管理系统，包括对用户管理，任务管理，订单管理，还有对用户重复登录的管理。主要分为这几个模块，便于管理。
   - （1）用户基本信息的输入，包括用户id，用户电话，用户姓名，用户密码，用户性别，用户头像，用户属性，用户上一次登录的ip，用户最后登录日期。
   - （2）用户基本信息增删改查。
   - （3）任务基本信息的输入，包括任务id，任务标题，任务期望完成日期，任务最大接收者数量，任务内容，任务标价，任务发布者id，任务发布日期，任务类型，任务具体完成日期，任务状态，任务当前接收者数量，任务当前完成者数量，任务结果，任务接收者集合。
   - （4）任务信息的增删改查。
   - （5）用户重复登录信息的输入，包括登录信息的编号，该登录信息的用户id，登录信息的ip地址，该登录信息产生的日期。
   - （6）用户重复登录信息增删改查。
   - （7）订单信息的输入，包括订单编号，该订单的所有者id，该订单对应任务id，订单状态，订单产生日期，订单完成日期，订单评论。
   - （8）订单信息的增删改查。
   - （9）问卷信息的输入，包括问卷编号，问卷对应的任务id，问卷描述，问卷是否有多选，选项数目，选项。
   - （10）问卷信息的增删改查。
 
- ### 2.概念设计
  + #### 2.1ER图
  ![ER-image](/images/ER.png)

- ### 3.逻辑设计
  + #### 3.1表设计  
  
User表  

| 字段名 | 数据类型 | 字段说明 |
| ----- | ----- | ------ |
| user\_id | INTEGER | 用户id |
| user\_phone | VARCHAR | 用户电话 |
| user\_name | VARCHAR | 用户姓名 |
| user\_password | VARCHAR | 用户密码 |
| user\_sex | INTEGER | 用户性别 |
| user\_icon | VARCHAR | 用户头像 |
| user\_properties | INTEGER | 用户属性 |
| user\_lastIp | VARCHAR | 用户上一次登录的ip |
| user\_lastDate | DATE | 用户最后登录日期 |  

 
task表

| 字段名 | 数据类型 | 字段说明 |
| ----- | ----- | ------ |
| task\_id | INTEGER | 任务id |
| task\_title | VARCHAR | 任务标题 |
| task\_deadLineDate | DATETIME | 任务期望最后完成日期 |
| max\_receiversCount | INTEGER | 任务接收者数量 |
| task\_content | TEXT | 任务内容 |
| task\_price | INTEGER | 任务标价 |
| task\_publisherId | INTEGER | 任务发布者id |
| task\_publishDate | DATETIME | 任务发布日期 |
| task\_type | INTEGER | 任务类型 |
| task\_completeDate | DATE | 任务实际完成日期 |
| task\_state  | INTEGER | 任务状态 |
| current\_receiversCount | INTEGER | 任务接收者数目 |
| current\_completeCount | INTEGER | 任务完成者数目 |
| result | VARCHAR | 任务结果 |
| receivers | VARCHAR | 任务接收者集合 |

loginlog表

| 字段名 | 数据类型 | 字段说明 |
| ----- | ----- | ------ |
| loginlog\_id | INTEGER | 登录信息的编号 |
| loginlog\_userId | INTEGER | 该登录信息的用户id |
| loginlog\_ip | VARCHAR | 登录信息的ip地址 |
| loginlog\_date | DATE | 该登录信息产生的日期 |

transaction表

| 字段名 | 数据类型 | 字段说明 |
| ----- | ----- | ------ |
| transaction\_id | INTEGER | 订单编号 |
| user\_id | INTEGER | 该订单的所有者id |
| task\_id | INTEGER | 该订单对应任务id |
| transaction\_state | INTEGER | 订单状态 |
| transaction\_startTime | DATE | 订单产生日期 |
| transaction\_completeTime | DATE | 订单完成日期 |
| committion | VARCHAR | 订单评论 |

questionnaire表

| 字段名 | 数据类型 | 字段说明 |
| ----- | ----- | ------ |
| question\_id | INTEGER | 问卷编号 |
| task\_id | INTEGER | 问卷对应的任务id |
| question\_description | TEXT | 问卷描述 |
| if\_multipleSelect | BOOLEAN | 问卷是否有多选 |
| options\_count | INTEGER | 选项数目 |
| options | VARCHAR | 选项 |
