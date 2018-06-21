## 准备工作

考拉授权登录基于OAuth2.0协议标准在进行OAuth2.0授权登录接入之前，向考拉申请并获得相应的**AppID**和**AppSecret**后可开始接入流程。

## 授权流程说明

 1. 第三方发起考拉授权登录请求，考拉用户允许授权第三方应用后，考拉会拉起应用或重定向到第三方网站，并且带上授权临时票据code参数;

 2. 通过code参数加上AppID和AppSecret等，通过API换取access_token;

 3. 通过access_token进行接口调用，获取用户基本数据;

## 授权流程时序图

 ![][avatar]

 [avatar]: img1.png