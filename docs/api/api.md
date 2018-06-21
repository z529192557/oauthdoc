## 获取用户信息

##### 接口说明：

此接口用于获取用户个人信息。开发者可通过OpenID来获取用户基本信息。OpenId每一个用户唯一。

##### 请求说明：

http请求方式：GET
<http://m-home.kaola.com/outLogin/api/getUserInfo.html?access_token=${token}&openid=${openid}>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
access_token | 是 | access_token
openid | 是 | 用户openId

##### 返回说明
正确的返回
```
{
  "code":200,
  "msg":"操作成功",
  "headImgUrl":"http://haitao.nos.netease.com/ecb77c8578f44fffa4ea9cea62ef40b6.png",
  "nickname":"156****8356@163.com",
  "openId":"4a9027e191f1e407cc636457195bc1d8"
  }
```
参数 | 说明
- | :-
code | 返回码
msg | 详细信息
headImgUrl | 头像
nickname | 昵称
openId | 用户openid


错误的返回
```
{"code":41009,"msg":"accessToken不存在或已过期"}
```
参数 | 说明
- | :-
code | 返回码
msg | 详细错误信息



