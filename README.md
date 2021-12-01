### 测试账号

接口路径：192.168.1.43:7001

账号：123456 密码：123456

### 登录接口

1.接口名：'/user/login';

2.类型：'post';

3.入参：

```js
var data = {
    username:[String], //账号
    password:[String], //密码
    captcha: [String]  //验证码
}
```

4.出参：

```js
var res = {
    status  :[Number],   //状态 1：成功  0：失败
    msg :[String],  //返回描述信息
    data    :'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiYXZhdG9yX25hbWUiOiLmtYvor5Xlj7ciLCJhZ2UiOjE4LCJzZXgiOiIxIiwiYXZhdG9yX2ltZyI6IjAiLCJjbGFzc19pZCI6MCwiZGVzY3JpcHRpb24iOiLkuIDkuKrnroDnroDljZXljZXnmoTmtYvor5Xlj7ciLCJwaG9uZSI6IjEyMzQ1Njc4OTExIiwiZW1haWwiOiIxNTAwNjc5NTk4QHFxLmNvbSIsImlhdCI6MTYzNzY1NzM3NywiZXhwIjoxNjM3NjU5MTc3fQ.U4vtTCwUxMH5HzpwmHBNLLPHWlz3QpNc1eJ7E9ODjkM'
}   //该数据是一个Token，在请求接口时，传到请求头中，请求头的字段为authorization;
```

### 获取验证码

1.接口名：'/captcha';

2.类型：'get';

```js
//返回值为图片路径 src
```

### 注册接口

1.接口名：'/user/register';

2.类型：'post';

3.入参：

```js
var data = {
    username:[String], //账号 //必填
    password:[String], //密码 //必填
    age:[Number],//年龄 //非必填
    sex:[char], //0.女,1.男 // 默认为1  //非必填
    email	:[String], //邮箱 //必填
    phone	:[String], //手机号 //必填
```

4.出参：

```js
var res = {
    status  :[Number],   //状态 1：成功  0：失败
    msg 	:[String],  //返回描述信息
    data	: {} 
```



### 查询个人信息

1.接口名：'/user/info';

2.类型：'post';

3.入参：'{}'   //需要将登陆接口(/user/login)返回的token 存放入 请求头中;

4.出参：

```js
var res = {
    status  :[Number],
    msg		:[String],
    data	:{
        id:[Number],//个人id
        avatorName:[String],//个人名称 //非必填
        age:[Number],//年龄 //非必填
        sex:[char], //0.女,1.男 // 默认为1  //非必填
        avatorImg:[String], //头像索引  暂未增加上传头像
        classId:[Number],//班级的ID //非必填
        description:[String],//个人描述 //非必填
        phone:[String],//手机号 
        email:[String],//个人邮箱 
        updatedAt:[timestamp],//用户修改信息时间   timestamp:时间戳
        createdAt:[timestamp],//用户账号创建时间
        loginTime:[timestamp]//用户上次登录时间
    }
}
```

### 获取任务列表

1.接口名：'/task/list';

2.类型：'post';

3.入参：{}

4.出参

```js
var res = {
    status  :[Number],
    msg		:[String],
    data	:{
        taskId :[Number],   	// 该数据的ID
        taskName:[String], 		// 该数据的名字
        pid :[Number],		//作业父级的id  如果为null 那么为最高级的作业  如果不为null 则该任务在task_id 为parent_id 的做作业下挂载
        updatedAt:[timestamp], 	// 修改时间
        createdAt:[timestamp]	// 创建时间
    }
```

