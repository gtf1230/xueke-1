### 测试账号

接口路径：192.168.1.43:7001

账号：123456 密码：123456

### 1.登录接口定义

1. 接口名 ：/user/login;

2. 类型 ：  'POST'

3. 描述：此接口用来进行登录

4. 入参: 

   ```
   var data = {
       username: [String],     //用户名
       password: [String],    //密码
       captcha：[String]
   }
   ```

5. 出参：  

   ```
   var res = {
       status  : [Number],     //状态   1：成功    0：失败
       msg : [ String]       //返回描述信息
       data   : token  //需存起来；通过请求头带给服务端进行验证
   }
   ```

   

### 2.验证码接口

//获取验证码

1. 接口名 ：/captcha;

2. 类型 ：  'GET'

3. 描述：此接口用来获取验证码

```
    //接口返回数据：
    let res  =  '图片'    //res是img标签的src
```

### 3.注册接口

1. 接口名 ：/user/register;

2. 类型 ：  'POST'

3. 描述：此接口用来进行注册

4. 入参: 

   ```
   var data = {
       username: [String],     //用户名      必填
       password: [String],    //密码        必填
       captcha：[String],      // 验证码      必填
       sex：0 || 1  0：女  1：男,
       age: number,              //年龄 10~120
       email : [String],      //邮箱       必填
       phone:[String],        //手机号     11位
   }
   ```
   
   5. 出参：  

   ```
   var res = {
       status  : [Number],     //状态   1：成功    0：失败
       msg : [ String]       //返回描述信息
       data    : []
   }
   ```
   
### 4.查询个人信息

1.接口名：'/user/info';

2.类型：'post';

3.入参：{}

4.出参：
```
var res = {
    status  :[Number],
    msg		:[String],
    data	:{
        id:[Number],//个人id
        avatorName:[String],//个人名称 //非必填
        age:[Number],//年龄 
        sex:[Number], //0.女,1.男 // 默认为1  
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
   
   
###  5.task接口
   
1. 接口名 ：/task/list;

2. 类型 ：  'POST'

3. 描述：此接口用来获取任务列表

4. 入参: 

```
{}
```

5. 出参：

```
taskId:  作业的id
taskName: 作业的名字 
pid: 作业父级的id  如果为null 那么为最高级的作业  如果不为null 则该任务在task_id 为parent_id 的做作业下挂载
updataAt: 更新时间
createdAt: 创建时间
```

   
###  6.领任务接口
   
1. 接口名 ：/lead/task;

2. 类型 ：  'POST'

3. 描述：此接口用来进行领取任务

4. 入参: 

```
      taskId:[number] //作业的id
```

5. 出参：

```
   var res = {
       status  : [Number],     //状态   1：成功    0：失败
       msg : [ String]       //返回描述信息
       data    : []
   }
```

####  7.查询所有的领取的任务列表

1. 接口名 ：/user/task/list;

2. 类型 ：  'POST'

3. 描述：此接口用来查询所有的领取的任务列表

4. 入参: 

```
     {
            pageSize: [number]  //一页有多少条  默认为10
            pageNum: [number]  //第几页  默认为1
        }
```

5. 出参：

```js
   var res = {
   	status  : [Number],     //状态   1：成功    0：失败
         msg : [ String]       //返回描述信息
       	data:{
               count: [Number]        //有多少条
               pageCount: [Number]     //有多少页
               rows: [{
                  id:[Number], 
                  taskStatus:[String], //该任务目前的状态  0 未开始  1 已开始  2进行中 3已完成 4已超时
                  score:[Number],  // 任务的评分 1:优 2：良 3：中 4：差
                  progress:[Number],//任务的完成度 返回的数字  渲染时自己在后面拼接上% 
                  updatedAt:[timestamp], 	// 修改时间
                  createdAt:[timestamp]	// 创建时间
                  taskId: [Number]        //任务的taskId
                  userId: [Number]        //用户的userId
           }]
           }
       }
   ```

### 8.查询我的任务列表


1.接口名:'/mine/task/list'

2. 类型 ：  'POST'

3. 描述：此接口用来查询我的任务列表

4. 入参: 
 ```
     {
            pageSize: [number]  //一页有多少条  默认为10
            pageNum: [number]  //第几页  默认为1
        }
        //该接口需要登录   需要用到请求头中的token
```

5. 出参：

   ```js
   var res = {
   	status  : [Number],     //状态   1：成功    0：失败
         msg : [ String]       //返回描述信息
       	data:{
               count: [Number]        //有多少条
               pageCount: [Number]     //有多少页
               rows: [{
                  id:[Number], 
                  taskStatus:[String], //该任务目前的状态  0 未开始  1 已开始  2进行中 3已完成 4已超时
                  score:[Number],  // 任务的评分 1:优 2：良 3：中 4：差
                  progress:[Number],//任务的完成度 返回的数字  渲染时自己在后面拼接上% 
                  updatedAt:[timestamp], 	// 修改时间
                  createdAt:[timestamp]	// 创建时间
                  taskId: [Number]        //任务的id
                  userId: [Number]        //用户的userId
           }]
           }
       }
   ```

### 9.修改用户信息接口

1.接口名:'/update/user/info'

2.类型 ：'POST'

3.描述：此接口用来修改用户的信息

4.入参:
```js
{
      avatorName:[String],   //用户昵称
      age :[number] , //用户年龄
      sex:[number] , //用户性别  //1男 0女
      avatorImg:[number] , //用户头像 
      classId:[number], //班级的id
      description:[String],//个性签名 最多150个字符
      phone:[String]//手机号码       
      以上都是选填
} 	
```
5. 出参
```js
var res = {
	status  :[Number],
    	msg		:[String],
    	data	:[]
    }
```

### 10.批改任务

1.接口名:'/correct/task'

2.类型 ：'POST'

3.描述：此接口用来修改任务的完成度还有评分

4.入参:
```js
{
      score:[Number],  // 任务的评分 1:优 2：良 3：中 4：差
      progress:[Number],//任务的完成度 
      taskId: [Number]        //任务的id
      userId: [Number]        //用户的userId
} 	
```
5. 出参
```js
var res = {
	status  :[Number],
    	msg	:[String],
    	data	:[]
    }
```

### 11.任务详情

1.接口名:'/task/detail'

2.类型 ：'POST'

3.描述：此接口用来查询此任务有多少人领取

4.入参:
```js
{
      taskId: [Number]        //任务的id
} 	
```
5. 出参
```js
var res = {
	status  :[Number],
    	msg	:[String],
    	data	:[{
		  id
		  taskStatus:[String], //该任务目前的状态  0 未开始  1 已开始  2进行中 3已完成 4已超时
                  score:[Number],  // 任务的评分 1:优 2：良 3：中 4：差
                  progress:[Number],//任务的完成度 返回的数字  渲染时自己在后面拼接上% 
                  updatedAt:[timestamp], // 修改时间
                  createdAt:[timestamp],// 创建时间
                  taskId: [Number],      //任务的id
                  userId: [Number],      //用户的userId
	}]
	data.length  // 有多少人接受了这个任务
    }
```
