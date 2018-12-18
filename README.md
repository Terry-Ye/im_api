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
