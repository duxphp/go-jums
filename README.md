go-jums
====================

# 概述
jums为极光ums推送的go语言api封装，http请求使用fiber web 框架的内置方法，适用于fiber web 框架使用

官方 REST API 文档： [https://docs.jiguang.cn/jums/guideline/intro](https://docs.jiguang.cn/jums/guideline/intro)

# 安装

使用 go get 安装，无任何第三方依赖：

```sh
go get github.com/duxphp/go-jums
```

# 使用方法

## 1. 创建 Jums

```go
import "github.com/duxphp/go-jums"

client := jums.New(jums.Config{
	Key: ""
	Secret: ""
})
```

## 2. 消息发送 (目前不支持模板消息)

可自行调用 `jums.Toxx` 方法进行使用
```go
client.Message().To(jums.ToSms("sms", []string{"18000000000"})).Content(jums.MsgSms("1", 1, map[string]any{"code": "1234"})).Send()
```

### 3. 用户管理
可自行调用 `jums.UserXXX` 方法进行使用
```go
client.User().SetId(123).Add(UserTag("channelKey", "标签一", "标签二")).Send()
```

### 4 用户删除

```go
client.User().SetId(123).UserDel(1,,2,,3)
```
