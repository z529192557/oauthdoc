## 奇遇跳转考拉H5

通过global.163.com/urs/redirect?target=${url} 同步163.com cookie后跳转考拉授权H5页面

* 注意：url参数要encode

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
target | 是 | 考拉H5目标页面

##### 示例

```
<https://global.163.com/urs/redirect?target=https%3a%2f%2fm-user.kaola.com%2foutLogin%2fqiyuAuth.html%3fcallback%3dhttps%253a%252f%252fxxx.xxx.com%252fcallback>

```
* 注意：callback的参数 作为m-user.kaola.com域名的参数，其值需要两次URLencode

##用户确认授权，生成token

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

此接口用于获取用户个人信息。开发者可通过OpenID来获取用户基本信息。OpenId每一个用户唯一。

##### 请求说明：

http请求方式：**POST**

<https://m-home.kaola.com/outLogin/api/getBasicUserInfo.html>

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
