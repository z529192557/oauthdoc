## App内/浏览器 跳转 考拉H5请求accessToken与用户信息
 
第三方使用网站应用授权登录前请注意已获取相应授权作用域（scope=kaola-vip），则可以通过在浏览器打开以下链接:

* 注意：redirect参数要encode
```
<https://m-user.kaola.com/app/account/simple/auth?appid=${appid}&scope=${scope}&redirect=${redirect}>
```
##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
appid | 是 | 应用唯一标识，向考拉申请
scope | 是 | 应用授权范围，写死 **kaola-vip**
redirect|否|授权后的重定向目标页,需要encode


##### 调用频率限制
100tps

##### 返回说明

用户允许授权后，将会重定向到redirect指定网址上，并且带上相关用户参数，例：
```
https://${redirect}?account=酒剑小仙&openid=92266349cd94352d026ad2cf8dae5577&access_token=token5935272a496b1f348ca689306f8a1493
```
返回参数 | 说明
- | :-: | :-
account | 昵称
access_token | accessToken值
openid | 用户openId