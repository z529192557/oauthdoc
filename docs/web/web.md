## 第一步 : 请求临时授权码

第三方使用网站应用授权登录前请注意已获取相应授权作用域（scope=kaola-vip），则可以通过在浏览器打开以下链接:

<https://m.kaola.com/outLogin/oauth.html?appid=${appid}&scope=${scope}&redirect_uri=${redirect_uri}>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
appid | 是 | 应用唯一标识，向考拉申请
scope | 是 | 应用授权作用域，目前仅支持**kaola-vip**
redirect_uri | 否 | 授权后重定向地址

##### 调用频率限制
100tps

##### 返回说明

用户允许授权后，将会重定向到redirect_uri的网址上，并且带上code参数
```
redirect_uri?code=CODE
```
用户允许授权后，将会重定向到redirect_uri的网址上,不带任何参数
```
redirect_uri?code=CODE
```
若需要回跳App，redirect_uri 参数可以不传，则用户允许授权后，将会重定向到appid在考拉配置的scheme的地址上，并且带上code参数
```
<thirdparty://?code={code}>
```
若需要回跳App，redirect_uri 参数可以不传，用户拒绝允许授权后，将会重定向到appid在考拉配置的scheme的地址上,不带任何参数
```
<thirdparty://?>
```

## 第二步 : 通过code获取access_token
通过code获取access_token

http请求方式：**POST**

<https://m-home.kaola.com/outLogin/oauth/accessToken.html?appid=${appid}&secret=${secret}&code=${code}&grant_type=authorization_code>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
appid | 是 | 应用唯一标识，向考拉申请
secret | 是 | 应用密钥，与考拉协商
code | 是 | 填写第一步获取的code参数
grant_type | 是 | 填写authorization_code

##### 注意
secret 需要通过后台云服务器传递，不要在客户端，前台应用等地方暴露secret值,code需要在5分钟内使用，且仅能使用一次

##### 调用频率限制
100tps

##### 返回说明

正确的返回:
```
{"code":200,"msg":"操作成功","expires_in":7200,"scope":"kaola-vip","accessToken":"tokenbfa06f2e0a857b5c8120773188f3b4f4","openId":"4a9027e191f1e407cc636457195bc1d8"}
```
参数 | 说明
- | :-
code | 返回码
msg | 附加信息
expires_in | accessToke凭证超时时间，单位(秒)
scope | 用户授权的作用域
accessToken | accessToke文本值
openId | 授权用户唯一标识

错误的返回:

```
{"code":41014,"msg":"应用密钥错误"}
```

参数 | 说明
- | :-
code | 返回码
msg | 详细错误信息

