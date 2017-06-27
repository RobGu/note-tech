title: 微信公众平台
speaker: Ben Li
transition: slide3
theme: moon
usemathjax: yes

[slide]

# 微信平台开发

<small>Ben Li</small>

[slide]

## 微信公众平台是什么?
---
[slide]

## 微信公众平台包含什么?
  * 服务号 {:&.rollIn}
  * 订阅号
  * 企业号
  * 小程序
  * 我们平时说的公众号指的是 `服务号`, `订阅号`.
  * 抱米prod是`服务号`.

[slide]

## 怎么配置?
  * 服务器配置 {:&.rollIn}
  * 回调页面域名;
  * JS接口安全域名
  * 业务域名
  * IP白名单(新增)

[slide]
<h2 style="text-align: start;">服务器配置</h2>

  * 启用并设置服务器配置后，用户发给公众号的消息以及开发者需要的事件推送，将被微信转发到该URL中

<h2 style="text-align: start;">回调页面域名</h2>

  * 用户在网页授权页同意授权给公众号后，微信会将授权数据传给一个回调页面，回调页面需在此域名下，以确保安全可靠。

[slide]

<h2 style="text-align: start;">业务域名</h2>

  * 设置业务域名后, 在微信内访问该域名下的页面时,不会被重新排版. 用户在该域名上进行输入时, 不会出现安全提示.

<h2 style="text-align: start;">JS接口安全域名</h2>

  * 设置JS接口安全域名后，公众号开发者可在该域名下调用微信开放的JS接口

[slide]
<h2 style="text-align: start;">IP白名单</h2>

  * 通过开发者ID及密码调用获取access_token接口时，需要设置访问来源IP为白名单。

<br/>
<br/>

**PS**: 在配置 `回调页面域名`, `JS接口安全域名`, `业务域名`时候, 需要将验证文件上传之服务器根目录.
[slide]
<h2 style="text-align: start;">微信公众号中几个概念?</h2>

  * AppID(开发者ID): 开发者ID是公众号开发识别码，配合开发者密码可调用公众号的接口能力。
  * AppSecret(开发者密码): 开发者密码是校验公众号开发者身份的密码，具有极高的安全性。
  * 原始ID: 微信原始账号是注册微信时系统随机分配给你的一个账号。
[slide]
## 如何将公众号托管至群脉?

  - 正式号:
    * 正式号以授权的方式托管至群脉的.(`管理员扫描二维码`)
    * 取消授权, 在公众号[添加功能插件] -> [授权管理] 中可以取消授权.

  - 测试号:
    * *抱米正式号是以测试号的方式托管至群脉的*
    * 测试号托管, 只需要填写 `AppID`, `AppSecret`, `原始ID`后, 将其生成的URL跟Token填写到公众号后台即可.
[slide]
## 群脉中的几个概念?

  * accountID {:&.fadeIn}
  * channelID
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

[slide]
<h2 style="text-align: start;">微信JS-SDK</h2>
  * 是开发者在网页上通过JavaScript代码使用微信原生功能的工具包. {:&.zoomIn}
  * 开发者可以使用它在网页上录制和播放微信语音、监听微信分享、上传手机本地图片、拍照等许多能力.
<br/>
<br/>
<br/>

[slide]
<h2 style="text-align: start;">WX.Config</h2>
  * 所有需要使用JS-SDK的页面必须先注入配置信息，否则将无法调用. {:&.zoomIn}
  * 使用`https`需引入`jweixin-1.2.0`版本
<br/>
<br/>
<br/>

[slide]
### 授权流程图
 <img src="/img/way.png" />

[slide]
### 常见问题
  * `invalid url domain`: {:&.zoomIn}
    - 大部分情况下是没有正确填写 `JS接口安全域名`.
  * `permission denied`:
    - 未认证;
    - Config失败；
    - 调用的JSAPI没有传入config的jsApiList参数中.

[slide]

### 常见问题
  * `invalid signature`: {:&.zoomIn}
    - 签名算法是由服务端实现, 一般出现这个error, 是因为传给服务端用以生成前面`url`不对.
    - 保证`URL`正确的前提下, 确定 `access_token` 是否正确.
    - `URL` 要动态获取. (JS-SDK 对 SPA 应用不友好, 解决方案: 使用hash location)

[slide]
### H5中遇到的坑
  * 签名 {:&.zoomIn}
    - Android与iOS 获取获取当前URL不一致. 导致Config失败.
  * 分享
    - 分享出去的Icon, Andriod上不可以采用`https`, 不显示.
  * 获取地理位置信息
    - 部分奇葩Android机.
  * WKWebview 与 UIWebview

[slide]
## OAuth鉴权
  * 需要配置 `网页授权域名` {:&.zoomIn}
    - 权回调域名配置规范为全域名，比如需要网页授权的域名为：www.qq.com，配置以后此域名下面的页面http://www.qq.com/music.html, http://www.qq.com/login.html 都可以进行OAuth2.0鉴权。但http://pay.qq.com, http://music.qq.com, http://qq.com无法进行OAuth2.0鉴权

[slide]
### 常见问题
  * redirect_uri参数错误 {:&.zoomIn}
    - Channel ID 绑定是否正确
    - 回调页面域名 填写是否正确
<br/>
<br/>
<br/>
[slide]
<h2 style="text-align: start;"> 微信网页授权 </h2>
  * 静默授权: {:&.zoomIn}
    以snsapi_base为scope发起的网页授权，是用来获取进入页面的用户的openid的，
    并且是静默授权并自动跳转到回调页的。用户感知的就是直接进入了回调页
  * 非静默授权:
    以snsapi_userinfo为scope发起的网页授权，是用来获取用户的基本信息的。
    但这种授权需要用户手动同意，并且由于用户同意过，所以无须关注，就可在授权后获取该用户的基本信息。 (*用户未关注*)
[slide]
<h2 style="text-align: start;">OpenID:</h2>
  * 为了识别用户，每个用户针对每个公众号会产生一个安全的OpenID. {:&.zoomIn}

<h2 style="text-align: start;">UnionID:</h2>
  * 如果需要在多公众号、移动应用之间做用户共通，则需前往微信开放平台， {:&.zoomIn}
  将这些公众号和应用绑定到一个开放平台账号下，绑定后，一个用户虽然对多个公众号和应用有多个不同的OpenID，但他对所有这些同一开放平台账号下的公众号和应用，只有一个UnionID.
[slide]

## 微信开放平台

<img src="/img/open.jpeg" />

[slide]
## 微信开放平台

  * 移动应用开发 {:&.zoomIn}
    - 让你的应用支持微信分享、微信收藏、微信支付
  * 网站应用开发
    - 让你的网站支持使用微信帐号登录
  * 公众帐号开发
    - 接入微信开放平台公众帐号开发,为亿万微信用户提供轻便的服务.
  * 第三方平台开发
    - 成为第三方平台,为广大公众号提供运营服务和行业解决方案

[slide]

<img src="/img/rl.jpg" />

[slide]

  扩展
    * JD公众号 {:&.zoomIn}
    * App 分享
<br/><br/><br/><br/>

[slide]

  谢谢观看～