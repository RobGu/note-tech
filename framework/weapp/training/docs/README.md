# 小程序分享

## 基础篇

### 申请小程序

- 注册小程序
- 注册范围
- 注册页面
- 填写小程序信息
- 查看小程序设置

### Hello Word

- 添加开发者，测试者
- 账号限制
- 安装开发工具
- 第一个小程序
- 项目配置
- 小程序配置
- 小程序页面

### 发布小程序

- 预览/上传小程序
- 选为体验版
- 提交审核
- 填写审核信息
- 发布小程序
- 小程序入口

## 开发篇

分享的目的更多的带领大家一起过一下小程序开发者文档，可以快速了解小程序支持哪些特性。开发时有哪些注意点。如果大家想真正熟悉小程序，需要花时间去把文档都过一遍

- 小程序介绍 https://developers.weixin.qq.com/miniprogram/introduction/index.html?t=19040221
- 小程序开发 https://developers.weixin.qq.com/miniprogram/dev/index.html?t=19040212
- 小程序开发指南 https://developers.weixin.qq.com/ebook?action=get_post_info&docid=0008aeea9a8978ab0086a685851c0a

### UI 设计

<!-- 参照知识库讲一下，考虑一下是否需要更新知识库 -->
- 支持 ipad
- 支持横竖屏
- 支持沉浸式布局

### 理解小程序宿主环境
- 渲染层和逻辑层
https://developers.weixin.qq.com/ebook?action=get_post_info&docid=0000286f908988db00866b85f5640a

- 事件
https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000846df9a03909b0086a50025180a

### 开发

- Scripts 语言
  - [首选 EcmaScript 6](https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000a8806958588cb00862bd5851c0a)
  - [TypeScript](https://developers.weixin.qq.com/miniprogram/dev/devtools/edit.html#typescript-%E6%94%AF%E6%8C%81)
- wxml
https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000ee2c29d4f805b0086a37a254c0a

- wxss
https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000c44c49141887b00864fbba5100a

- wxss 和 css 区别
  - rpx
  - 选择器
  - 继承
- flex https://developers.weixin.qq.com/ebook?action=get_post_info&docid=00080e799303986b0086e605f5680a

- 组件简介
https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000eec0b998e80bb0086f092b5100a

- 官方组件
https://developers.weixin.qq.com/miniprogram/dev/component/

着重讲一下 button https://developers.weixin.qq.com/miniprogram/dev/component/button.html

- 官方组件 - 原生组件
  https://developers.weixin.qq.com/miniprogram/dev/component/native-component.html

- 着重讲一下 web-view https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html

- 自定义组件
https://developers.weixin.qq.com/miniprogram/dev/framework/custom-component/

- 网络 https://developers.weixin.qq.com/miniprogram/dev/framework/ability/network.html
  - 域名配置
  - 限制
  -  referer 很有用，查日志 https://servicewechat.com/{appid}/{version}/page-frame.html

- 系统对接(限制比较多，多举例子)
  - h5
  - 小程序
  - 公众号图文
  - 小程序码
  - 公众号组件
  - 客服会话
  - 打开原生应用

- 其它使用较少功能
  - WXS https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxs/
  - plugin https://developers.weixin.qq.com/miniprogram/dev/framework/plugin/
  - template https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/template.html

### 兼容

- UI 兼容
  - 单位使用 rpx，少量使用 vh（撑满全屏）。px 除了特定组件比如 canvas 上会使用，使用很少。其它单位几乎不使用
<!-- 其它地方如果这种实践经验类的东西可以多写 -->

- js 兼容
    https://developers.weixin.qq.com/miniprogram/dev/guide/runtime/js-support.html?pass_ticket=YbkYf5Qm49woKz0UoNqlbpzsDNw5WxtDMseKBVs4Kx5y1ENYGtjR1hNK2PUflYS9

### 测试
<!-- 参照知识库讲一下 -->
- 系统
- 机型
- 小程序版本
https://developers.weixin.qq.com/miniprogram/dev/framework/client-lib/version.html

## 群脉篇

主要介绍代开发，群脉能力，maijs 能力

### 代小程序开发简介

- 第三方平台概述 https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&id=open1419318292&token=&lang=zh_CN
- 代小程序实现业务 https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&id=open1489144594_DhNoV&token=&lang=zh_CN

### 托管小程序

- 演示一下第三方平台后台
- 在群脉上演示一下完整的 托管->配置->添加体验者->发布预览版->提交审核->发布-> 暂停服务 (没有的就比划一下)

### 群脉小程序开发
- 介绍一下 maijs
- 结合第三方平台后台，小程序 project.config.json ext.json 解释清楚什么是开发小程序，什么是托管小程序
- 解释清楚群脉这边是如何授权的，base 和 member 的区。理解 isActivated isSocialAuthorized
- 注册 bindPhone（会激活会员，和注册类似，不推荐单独写注册 api，可以用这个 api 代替）
- 上报事件
- 模板消息
  - 解释一下模板消息的限制
  - 上报 formId
- 小程序二维码 （解释清楚这里是公用产品，但是没有标准化）
- 上报营销活动（需要结合小程序二维码一起使用）
- 打 tag （使用较少）
- 上传图片
- 微信支付
- 客服

<!-- 其它的可以继续补充 -->

### 群脉小程序模板简介
- 把文档结构介绍一下

## 群脉小程序模板
