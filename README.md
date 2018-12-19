### 简介
1. im_api 是im中需要的一些简单接口，基于[beego框架 ](https://beego.me/docs/intro/)


### 部署
mysql执行,创建用户表
```
CREATE TABLE `tb_user` (
  `id` varchar(32) NOT NULL,
  `user_name` varchar(16) NOT NULL,
  `password` varchar(32) NOT NULL,
  `create_time` int(10) NOT NULL,
  `update_time` int(10) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 ROW_FORMAT=COMPACT;
```
部署项目
```
cd $GOPATH/src/
go get github.com/beego/bee
git clone https://github.com/Terry-Ye/im_api.git
cd im_api
mv conf/dev/database_example.conf conf/dev/database.conf // 根据自身情况修改配置

$GOPATH/bin/bee run
```




### 部署注意事项
1. 部署服务器注意防火墙是否开放对应的端口(本地不需要，具体需要的端口在各层的配置文件)


### api 文档

#### 注册接口

* http 请求方式：post
* 请求地址：http://localhost:8080/v1/user/register
* 请求参数
```
{
    "UserName":"terry4444",
    "Password":"terry4444"
}
```
* 返回数据格式（示例）
```
{
    "code":0,
    "msg":"success"
}
```


#### 登录接口

* http 请求方式：post
* 请求地址：http://localhost:8080/v1/user/login
* 请求参数
```
{
    "UserName":"terry4444",
    "Password":"terry4444"
}
```
* 返回数据格式（示例）
```
{
    "code":0,
    "msg":"success"
}
```

#### 检查auth接口

* http 请求方式：get
* 请求地址：http://localhost:8080/v1/user/login
* 请求参数
```
{
    "Auth":"8e11412585c38a7d"
}
```
* 返回数据格式（示例）
```
{
  "code": 0,
  "msg": "请求成功",
  "data": {
    "Auth": "5fee48a98f1c78f5",
    "UserId": "863440c38d717354",
    "UserName": "terry4444"
  }
}
```

#### 更新在线人数（由ws推送）

* http 请求方式：get
* 请求地址：http://localhost:6921/api/v1/count?rid=1
* 返回数据格式（示例）
```
{
    "code":0,
    "msg":"success"
}
```