## 获取用户信息

第三方应用经过用户授权，拿到access_token后方可调用。

##### 接口说明：

此接口用于获取用户个人信息。开发者可通过OpenID来获取用户基本信息。OpenId每一个用户唯一。

##### 请求说明：

http请求方式：**GET**

<https://m-home.kaola.com/outLogin/api/getUserInfo.html?access_token=${token}&openid=${openid}>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
access_token | 是 | access_token
openid | 是 | 用户openId

##### 返回说明
正确的返回s
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


## 开通会员接口

第三方应用经过用户授权，拿到access_token后方可调用。

##### 接口说明：

此接口用于为考拉用户开通会员，为方便第三方应用失败重试逻辑，该接口的access_token有效时间较长(3天)

##### 请求说明：

http请求方式：**POST**

<待定>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
orderid |是| 腾讯视频订单id，幂等控制
vipType |是| 1:红卡月卡，2:红卡年卡
access_token |是| access_token
timestamp |是| 超过15分钟后该链接无效，以服务器时间为准 时间戳是秒，而非毫秒。
signature |是|	签名md5(appid+orderid+vipType+timestamp+secret)，参数检验。appid和secret考拉分配

##### POST Body请求体例子
```
{
    "orderid" : "videoViporderXXXXXX",
    "vipType" : 1
    "access_token" : "token69ee5d1bd23d2e2110ae60b296b2345a"
    "timestamp" : 15000000
    "signature" "codeb1310ff1fc1289714485ba699227eb64"
}
```
##### 返回说明
正确的返回
```
{
  "code":200,
  "msg":"操作成功"
  }
```
参数 | 说明
- | :-
code | 返回码
msg | 详细信息


错误的返回
```
{"code":41009,"msg":"accessToken不存在或已过期"}
```
参数 | 说明
- | :-
code | 返回码
msg | 详细错误信息






