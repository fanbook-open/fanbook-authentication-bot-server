# fanbook-authentication-bot-server

该项目基于jdk11开发
用户fanbook服务器与腾讯文档绑定，实现腾讯文档中配置信息与fanbook绑定的手机号匹配并且分配指定角色
## 初始化操作：

1. 录入一个腾讯文档用户用于读取腾讯文档内容（该用户需要有文档读取导出权限） 存入到```t_config```表中
2. 配置fanbook服务器ID和腾讯文档ID进行关联（目前只支持1对1配置，即即fanbook服务器对应一个文档）存入到```t_word```表中

目前未开放管理界面，插入数据需要通过api接口或者数据库操作数据（如果开放外网使用建议把接口关闭）
一般只需要操作```t_config```（腾讯文档开放平台刷新token只能使用1年，1年后需要手动获取）、```t_word```表（用于配置fanbook服务器和腾讯文档关联）

## 手动同步数据
调用该接口可以手动刷新指定服务器对应的文档数据

```/word/sync?guild=xxxxxxxx```

## 数据表

```
t_config 配置读取腾讯文档的用户信息
t_mobile 用户数据表
t_mobile_temp 用户临时表
t_record 用户认证记录表
t_word fanbook服务器与腾讯文档关联表
```
