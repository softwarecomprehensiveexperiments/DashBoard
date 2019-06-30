# API设计文档

## 前后端对接API（使用Restful接口）

### 1. 用户注册
A.前端发送请求：
URI(method: POST): /user/register
json格式：
```
{
	string phone,
	string name,
	string password,
	int sex
}
```
说明：
phone：非空。标准手机格式，长度11位  
	正则：`^1(?:(3[0-9])|(4[5-7])|(5[0-9])|(7[0-9])|(8[0-9]))+\\d{8}$`  
name：非空。可使用中文，英文，数字和下划线，不以数字开头，长度6~14个字符   
	正则：先把中文转为两个：`[\\u4e00-\\u9fa5]`  
				然后正则判断：`^[a-zA-Z][a-zA-Z0-9_]{5,13}$`  
password：非空。可使用字母，数字，或特殊符号（包括!@#$%^&*），必须至少包含两种类型，长度8~16个字符  
	正则：`(?=[a-zA-Z0-9!@#$%^&*]{8,16})^.*(?=([0-9](?=[a-zA-Z!@#$%^&*]))|([!@#$%^&*](?=[a-zA-Z0-9]))|([a-zA-Z](?=[0-9!@#$%^&*]))).*$`  
sex：非空。0代表男生，1代表女生  

B.后端发送应答：
json格式：
```
{
	bool success,
	int error_code,
	string description
}
```
说明：   
error_code：错误代码编号  
description：失败时的描述，包括：1用户名已存在 2手机号已被注册 3输入格式非法   

### 2. 登陆(通过用户名/手机号)
A.前端发送请求：
URI(method: PUT): /user/login
json格式：
```
{
	string key,
	string password
}
```
说明：  
key和password格式检查标准同上，key可为手机号或用户名    

B.后端发送应答：
json格式：
```
{
	bool success,
	int error_code,
	string description,
	result {
		int user_id,
		string user_name,
		string user_phone,
		string user_icon,
		int user_properties,
		int user_sex,
		int user_completed_receive_task_count,
		int user_completed_release_task_count,
		int user_doing_receive_task_count,
		int user_doing_release_task_count
	}
}
```
说明：
error_code：错误编码  
description：失败时的描述，包括：用户名不存在，用户名或密码错误，输入格式非法  
result: user信息，此时会生成token（在response的header里的authorization条目）  
user_completed_receive_task_count：用户领取且已完成的任务数   
user_completed_release_task_count：用户发布且已完成的任务数  
user_doing_receive_task_count：用户领取且正在进行的任务数   
user_doing_release_task_count：用户发布且正在进行的任务数  

### 3.当前用户注销
A.
URI:(method: PUT): /user/logout

B.
```
{
	bool success,
	int error_code,
	string description
}
```

### 4.查询当前个人基本信息
A.
URI:(method: GET): /user/current_user

B. 应答：
```
{
	bool success,
	int error_code,
	string description,
	result {
		int user_id,
		string user_name,
		string user_phone,
		string user_icon,
		int user_properties,
		int user_sex,
		int user_completed_receive_task_count,
		int user_completed_release_task_count,
		int user_doing_receive_task_count,
		int user_doing_release_task_count
	}
}
```

### 5.当前用户充值接口
A.
URI:(method: POST): /user/credit
```
{
	int amount（充值金额）
}
```
B.
```
{
	bool success,
	int error_code,
	string description
}
```

### 6.修改当前用户的个人信息
A.
URI:(method: PUT): /user/current_user
```
{
	string user_name,
	string user_phone,
	int user_sex,
	string old_password,
	string new_password
}
```
说明：old_password和new_password字段可以同时为空（表示不修改），但是一旦其中一个字段不为空就必须进行密码格式检查（包括新旧密码不可一致）

B. 应答：
```
{
	bool success,
	int error_code,
	string description,
}
```
可能的错误：用户名/手机重复，格式前端负责  


### 7.进入广场获取任务（状态均为待领取）
A.前端发送请求：
URI(method: GET): /task/public

B. 应答：
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		tasks [
			{
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_release_time,
				string task_deadline,
				int max_receivers_count, 
				int task_price,
				int current_receivers_count,（已被领取的数量）
				bool is_rec
			},
			...
		]
	}
}
```
说明：
total_count：返回的任务条数，即items数组的大小  
task_type：0表示跑腿任务，1表示资源分享任务，2表示调查问卷任务  
max_receivers_count：表示任务设定的最大接受者数量，非调查问卷任务时为0或1  

### 8.当前用户发布任务
A. 前端发送请求：
URI:(method: POST): /task
```
{
	string task_title,
	string task_description,
	int task_type,
	int task_price,
	int max_receivers_count,
	string task_deadline,
	questionnaire [
			{
				int question_id,
				string question_description,
				bool if_multiple_select,
				int options_count,
				string options
			},
			...
	]
}
```

B. 应答：
```
{
	bool success,
	int error_code,
	string description
}
```

### 9.查询任务相关
#### 9.1 查询所有当前用户发布的任务（按时间顺序）
A. 前端发送请求：
URI:(method: GET): /task/short/all

B. 应答：
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		tasks [
			{
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_release_time,
				string task_deadline,
				int max_receivers_count, 
				int publisher_id,
				string publisher_name,
				int task_price,
				int current_receivers_count,
				int current_complete_count,
				int overdue_count,
				string task_state,
				int task_state_code
			},
			...
		]
	}
}
```
#### 9.2 查询<当前用户>发布的"待领取、等待完成、等待确认"任务<简介>（比如问卷不会返回详细信息）
A. 前端发送请求：
URI:(method: GET): /task/short/release_doing

B. 应答：
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		tasks [
			{
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_release_time,
				string task_deadline,
				int max_receivers_count, 
				int publisher_id,
				string publisher_name,
				int task_price,
				int current_receivers_count,
				int current_complete_count,
				int overdue_count,
				string task_state,
				int task_state_code
			},
			...
		]
	}
}
```

#### 9.3 查询当前用户发布的"已完成"的任务简介
A. 前端发送请求：
URI:(method: GET): /task/short/release_completed

B. 应答：
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		tasks [
			{
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_release_time,
				string task_deadline,
				int max_receivers_count,
				int publisher_id,
				string publisher_name,.
				int task_price,
				int current_receivers_count,
				int current_complete_count,
				int overdue_count,（逾期数，领取并且未完成的）
				string task_state,
				int task_state_code
			},
			...
		]
	}
}
```

### 10.查询任务单（即交易单）相关
#### 10.1 查询当前用户所有的交易单（任务单）
A. 前端发送请求：
URI:(method: GET): /transaction/short/all

B.
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		transactions [
			{
				int transaction_id,
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_deadline,
				int task_price,
				string transaction_complete_time,
				string transaction_start_time,
				string state,
				int transaction_state_code
			},
			...
		]
	}
}
```

#### 10.2 查询当前用户"进行中、等待发布者确认"的进行中任务单
A. 前端发送请求：
URI:(method: GET): /transaction/short/receive_doing

B.
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		transactions [
			{
				int transaction_id,
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_deadline,
				int task_price
				string transaction_complete_time,
				string transaction_start_time,）
				string state,
				int transaction_state_code
			},
			...
		]
	}
}
```

#### 10.3 查询当前用户接受的"已完成"的任务单
A. 前端发送请求：
URI:(method: GET): /transaction/short/receive_completed

B.
```
{
	bool success,
	int error_code,
	string description,
	result {
		int total_count,
		transactions [
			{
				int transaction_id,
				int task_id,  
				string task_title,
				string task_short_description,
				int task_type,
				string task_deadline,
				int task_price
				string transaction_complete_time,
				string transaction_start_time,
				string state,
				int transaction_state_code
			},
			...
		]
	}
}
```

### 11.查询一个任务的详情(分为admin和非admin）
A.
URI:(method: GET):/task/detail/{taskId}

B.
```
{
	bool success,
	int error_code,
	string description,
	result {
		int task_id,  
		string task_title,
		string task_description,
		int task_type,
		string task_release_time,
		string task_deadline,
		int max_receivers_count,
		int task_price,
		string publisher_id,
		string publisher_name,
		string complete_date,(和状态有关：当任务为"已完成"时为完成时间，为"已取消"时为取消时间)
		int current_receivers_count,
		int current_complete_count,
		string state,(任务当前状态，包括："待领取", "等待完成", "等待确认", "已完成", "已取消")
		int task_state_code
		questionnaire [
				{
					int question_id,
					string question_description,
					bool if_multiple_select,
					int options_count,
					string options
				},
				...
		]
		string task_result,
		string receiver_names
	}
}
```

### 12.查询一个任务单的详情
A.
URI:(method: GET):/transaction/detail/{transactionId}

B.
```
{
	bool success,
	int error_code,
	string description,
	result {
	int transaction_id,
		int task_id,  
		int publisher_id,
		string publisher_name,
		string task_title,
		string task_description,
		int task_type,
		string task_deadline,
		int task_price,
		string transaction_complete_time,
		string transaction_start_time,（领取时间）
		string state,
		int transaction_state_code
		questionnaire [
			{
				int question_id,
				string question_description,
				bool if_multiple_select,
				int options_count,
				string options（同上）
			},
				...
	]
	string committion（问卷形式：答案与答案间使用@@隔开）
	}
}
```

### 13.当前用户领取任务
A.
URI:(method: POST):/transaction?task_id=

B.
```
{
	 bool success,
	 int error_code,
	 string description,
}
```


### 14.接受者（当前用户）选择完成任务单
A.
URI:(method: PUT):transaction/{transaction_id}
```
{
	string committion
}
```

B.
```
{
	bool success,
	int error_code,
	string description,
}
```

### 15.发布者（当前用户）确认完成任务
A.
URI:(method: PUT):task/{taskId}

B.
```
{
	bool success,
	int error_code,
	string description,
}
```

### 16.接受者（当前用户）取消任务单
A.
URI:(method: DELETE):transaction/{transaction_id}

B.
```
{
	bool success,
	int error_code,
	string description,
}
```

### 17.发布者（当前用户）取消任务
A.
URI:(method: DELETE):task/{taskId}

B.
```
{
	bool success,
	int error_code,
	string description,
}
```



