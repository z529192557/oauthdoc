## 腾讯视频App唤起考拉App请求accessToken与用户信息

通过私有scheme跳转考拉授权App

* 注意：openurl参数要encode

<kaolaauth://?action=1&openurl=encodeURI(https://m.kaola.com/member/activity/oauth.html&appid=${appid}&scope=kaola-tenvideo-vip)>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
action | 是 | 1
openurl | 是 | webview打开url
appid | 是 | 应用Appid,考拉分配
scope | 是 | 应用授权范围，写死 **kaola-tenvideo-vip**

##### 返回说明

用户允许授权后，将会重定向到腾讯在考拉配置的scheme的地址上，并且带上相关用户参数,例：
```
<tenvideo2://action =10&openurl= + encodeURIComponent('https://film.qq.com/h5/vplus/pay/?channelid=kaola&account=以父之名&openid=92266349cd94352d026ad2cf8dae5577&access_token=token5935272a496b1f348ca689306f8a1493')>
```
返回参数| 说明
- | :-: | :-
account | 昵称
access_token | accessToken值
openid | 用户openId

## 腾讯视频App内唤起考拉H5请求accessToken与用户信息

第三方使用网站应用授权登录前请注意已获取相应授权作用域（scope=kaola-vip），则可以通过在浏览器打开以下链接:

* 注意：redirect_uri参数要encode

<https://m.kaola.com/member/activity/oauth.html?appid=${appid}&scope=${scope}>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
appid | 是 | 应用唯一标识，向考拉申请
scope | 是 | 应用授权范围，写死 **kaola-tenvideo-vip**


##### 调用频率限制
100tps

##### 返回说明

用户允许授权后，将会重定向到腾讯H5的网址上，并且带上相关用户参数，例：
```
https://film.qq.com/h5/vplus/pay/?channelid=kaola&account=酒剑小仙&openid=92266349cd94352d026ad2cf8dae5577&access_token=token5935272a496b1f348ca689306f8a1493
```
返回参数 | 说明
- | :-: | :-
account | 昵称
access_token | accessToken值
openid | 用户openId