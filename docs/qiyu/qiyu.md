## 奇遇跳转考拉H5

通过global.163.com/urs/redirect?target=${url} 同步163.com cookie后跳转考拉授权H5页面

* 注意：url参数要encode

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
target | 是 | 考拉H5目标页面

##### 示例

```
<https://global.163.com/urs/redirect.html?target=https%3a%2f%2fm-user.kaola.com%2fapp%2fsuper-vip%2faccount-bind%3fcallback%3dhttps%253a%252f%252fwww.kaola.com%252fcallback>

```
* 注意：callback的参数 作为m-user.kaola.com域名的参数，其值需要两次URLencode

## 用户确认授权，生成token（考拉关注该接口，奇遇不需要关注）

```
<https://m-home.kaola.com/outLogin/getAuthCodeForQiYu.html>
```
##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-

##### 调用频率限制
100tps

##### 返回说明

正确的返回
```
{"data":"tokene46875849d4ffb1c94d6d1bddb839e1b","retCode":200,"retDesc":"操作成功"}
```
参数 | 说明
- | :-
retCode | 返回码
retDesc | 详细信息
data | token,两小时有效


错误的返回
```
{"retCode":41009,"retDesc":"accessToken不存在或已过期"}
```
参数 | 说明
- | :-
code | 返回码
msg | 详细错误信息


## 考拉H5回调奇遇callback

##### 回调例子

考拉前端拿到token，根据url中的callback拼接新的url，重定向浏览器

```
<https://callback?token=${token}>
```

## 获取用户信息

奇遇经过用户授权，拿到token后方可调用。

##### 接口说明：

此接口用于获取用户个人信息。

##### 请求说明：

http请求方式：**POST**

<https://m-home.kaola.com/outLogin/api/qiyu/getBasicUserInfo.html>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
accessToken | 是 | accessToken
appId | 是 | 奇遇AppId，考拉分配
appSecret | 是 | 奇遇appSecret，考拉分配

##### 返回说明
正确的返回
```
{
	"data": {
		"nickname": "xjjcbkmchh1",
		"headImgUrl": "http:\/\/haitao.nos.netease.com\/2018070220362340b0206012ab43c8a339996d997ccfa4.jpeg",
		"openId": "ce8fa4f345f8d6b1bc9bf6e85148f8da"
	},
	"retCode": 200,
	"retDesc": "操作成功"
}
```
参数 | 说明
- | :-
retCode | 返回码
retDesc | 详细信息
headImgUrl | 头像
nickname | 昵称
openId | 用户openid


错误的返回
```
{"retCode":41009,"retDesc":"accessToken不存在或已过期"}
```
参数 | 说明
- | :-
retCode | 返回码
retDesc | 详细错误信息



## 开通会员

##### 接口说明：

此接口用于奇遇开通考拉黑卡会员。

##### 请求说明：

http请求方式：**POST**

<https://m-home.kaola.com/outLogin/api/qiyu/vipOpen.html>

##### 参数说明

以下参数参考奇遇接口文档

参数 | 是否必须 | 说明
- | :-: | :-
open_id | 是 | 用户openId
expire_date | 是 | 失效时间“20190828"
order_no | 是 | 订单号，长度不超过32
valid_day | 是 | 会员有效天数
rights_day | 是 | 权益天数
secret_id | 是 | 密钥 id(32)，由奇遇分配
timestamp | 是 | 请求当前 UNIX 时间戳，注意服务器时间同步
signature | 是 | 请求签名

##### 返回说明
正确的返回
```
{
	"data": "",
	"state": {
		"code": "200",
		"msg": "接口调用成功"
	}
}
```



错误的返回
```
{
	"data": "",
	"state": {
		"code": "400",
		"msg": "参数错误"
	}
}
```


## 退回会员


##### 接口说明：

此接口用于奇遇退回考拉黑卡会员。

##### 请求说明：

http请求方式：**POST**

<https://m-home.kaola.com/outLogin/api/qiyu/vipRefund.html>

##### 参数说明

以下参数参考奇遇接口文档

参数 | 是否必须 | 说明
- | :-: | :-
open_id | 是 | 用户openId
valid_day | 是 | 回收的有效天数
expire_date | 是 | 原失效时间“20190828"
order_no_list | 是 | 订单号，英文逗号分隔
secret_id | 是 | 密钥 id(32)，由奇遇分配
timestamp | 是 | 请求当前 UNIX 时间戳，注意服务器时间同步
signature | 是 | 请求签名

##### 返回说明
正确的返回
```
{
	"data": "",
	"state": {
		"code": "200",
		"msg": "失效会员成功"
	}
}
```



错误的返回
```
{
	"data": "",
	"state": {
		"code": "400",
		"msg": "参数错误"
	}
}
```
