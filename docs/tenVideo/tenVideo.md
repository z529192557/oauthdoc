## 腾讯视频App唤起考拉App请求accessToken与用户信息

通过私有scheme跳转考拉授权App

* 注意：openurl参数要encode
```
<kaolaauth://?action=1&openurl=encodeURIComponent(https://m.kaola.com/member/activity/oauth.html&appid=${appid}&scope=kaola-tenvideo-vip)>
```
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
<tenvideo2://action=10&openurl= + encodeURIComponent('https://film.qq.com/h5/vplus/pay/?channelid=kaola&account=以父之名&openid=92266349cd94352d026ad2cf8dae5577&access_token=token5935272a496b1f348ca689306f8a1493')>
```
返回参数| 说明
- | :-: | :-
account | 昵称
access_token | accessToken值
openid | 用户openId

## 腾讯视频App内唤起考拉H5请求accessToken与用户信息

第三方使用网站应用授权登录前请注意已获取相应授权作用域（scope=kaola-vip），则可以通过在浏览器打开以下链接:

* 注意：redirect_uri参数要encode
```
<https://m.kaola.com/member/activity/oauth.html?appid=${appid}&scope=&redirect_uri=>
```
##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
appid | 是 | 应用唯一标识，向考拉申请
scope | 是 | 应用授权范围，写死 **kaola-tenvideo-vip**
redirect_uri|否|授权后的重定向目标页


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




## 考拉App唤起腾讯App授权

##### 唤起腾讯App的scheme
```
<tenvideo2://action=10&openurl= + encodeURIComponent('https://film.qq.com/h5/vplus/oauth/index.html?channelid=kaola&actType=1&ru=encodeURIComponent(https://m.kaola.com/member/activity/txRecord.html?recorId=XXXXX)')>
```

##### 提供给腾讯的授权回调协议，用于授权成功重新拉起 app

```
<kaolaauth://?action=1&openurl=encodeURIComponent(https://m.kaola.com/member/activity/txRecord.html?recorId=XXXXX&parma1=${parma1}&parma2=${parma2})>
```

##### 参数说明
recorId ： 由考拉通过ru传给腾讯一侧
param中带中文的，先urlencode 该参数

##### 回调例子
```
<kaolaauth://?action=1&openurl=https%3A%2F%2Fm.kaola.com%2Fmember%2Factivity%2FtxRecord.html%3Ftype%3D0%26accessToken%3Dee26b0dd4af7e749aa1a%26appid%3D101483052%26openid%3DE3EB42D261FD7F031816BA2728A73F5C%26nick%3D%25E9%2585%2592%25E5%2589%2591%25E5%25B0%258F%25E4%25BB%2599%26pic%3Dhttps%253A%252F%252Fthirdqq.qlogo.cn%252Fg%253Fb%253Dsdk%2526k%253Du1mbZcoBjax8DUyeic3RW0g%2526s%253D140%2526t%253D1483327077%26dataSign%3Df323808efe0b6567978312e57f0bc5574ad16b774c59fc1f7aa6068937bee532cd415760f3aac0e0ebd6af070fa0688ee23414cdef810a9650d8d1d099a6069d>
```

## 考拉H5唤起腾讯H5授权

##### 唤起腾讯H5的URL

```
<https://film.qq.com/h5/vplus/oauth/index.html?channelid=kaola&actType=2&ru=encodeURIComponent(https://m.kaola.com/member/activity/txRecord.html?recorId=XXXXX)>
```

## 考拉H5唤起腾讯H5授权后，回调URL
```
<https://m.kaola.com/member/activity/txRecord.html?recorId=XXXXX&parma1=${parma1}&parma2=${parma2}>
```
##### 参数说明
recorId ： 由考拉通过ru传给腾讯一侧
param中带中文的，先urlencode 该参数

##### 回调例子
```
<https://m.kaola.com/member/activity/txRecord.html?recorId=XXXXX&type=0&accessToken=ee26b0dd4af7e749aa1a&appid=101483052&openid=E3EB42D261FD7F031816BA2728A73F5C&nick=%E9%85%92%E5%89%91%E5%B0%8F%E4%BB%99&pic=https%3A%2F%2Fthirdqq.qlogo.cn%2Fg%3Fb%3Dsdk%26k%3Du1mbZcoBjax8DUyeic3RW0g%26s%3D140%26t%3D1483327077&dataSign=f323808efe0b6567978312e57f0bc5574ad16b774c59fc1f7aa6068937bee532cd415760f3aac0e0ebd6af070fa0688ee23414cdef810a9650d8d1d099a6069d>
```

