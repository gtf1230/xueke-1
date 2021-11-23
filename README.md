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

5.出参：

```js
var res = {
    status  :[Number],   //状态 1：成功  0：失败
    message :[String],  //返回描述信息
    data    :'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MiwiYXZhdG9yX25hbWUiOiLmtYvor5Xlj7ciLCJhZ2UiOjE4LCJzZXgiOiIxIiwiYXZhdG9yX2ltZyI6IjAiLCJjbGFzc19pZCI6MCwiZGVzY3JpcHRpb24iOiLkuIDkuKrnroDnroDljZXljZXnmoTmtYvor5Xlj7ciLCJwaG9uZSI6IjEyMzQ1Njc4OTExIiwiZW1haWwiOiIxNTAwNjc5NTk4QHFxLmNvbSIsImlhdCI6MTYzNzY1NzM3NywiZXhwIjoxNjM3NjU5MTc3fQ.U4vtTCwUxMH5HzpwmHBNLLPHWlz3QpNc1eJ7E9ODjkM'
}   //该数据是一个Token，在请求接口时，传到请求头中，请求头的字段为authorization;
```

### 获取验证码

1.接口名：'/captcha';

2.类型：'get';

```js
//返回值为图片路径 src
```







