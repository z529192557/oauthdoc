## 第一步 : 唤起App请求临时授权码

 文档待定

## 第二步 : 通过code获取access_token
通过code获取access_token

Method:**POST**

<https://m-home.kaola.com/outLogin/oauth/accessToken.html?appid=${appid}&secret=${secret}&code=${code}&grant_type=authorization_code>

##### 参数说明

参数 | 是否必须 | 说明
- | :-: | :-
appid | 是 | 应用唯一标识，向考拉申请
secret | 是 | 应用密钥，与考拉协商
code | 是 | 填写第一步获取的code参数
grant_type | 是 | 填写authorization_code

##### 注意
secret 需要通过后台云服务器传递，**不要在客户端，前台应用等地方暴露secret值**

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

