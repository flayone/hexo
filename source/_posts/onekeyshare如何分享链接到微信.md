title: onekeyshare如何分享链接到微信
tags:
- android
---
## 分享经验共同进步 ##

还不了解一键分享的可以去[官网mob.com](http://www.mob.com)了解一下第三方分享相关内容。此文是把我的经验分享一下，希望可以帮助一部分人能少走弯路！[git上源码地址](https://github.com/flayone/ShareDemo)

一般下载完官方ShareSDK，运行示例代码，会发现微信分享的不是链接，而是文字或者图片。经过翻看文档，反复修改代码运行终于实现了分享链接，不仅仅是分享链接，图片、音乐、视频、网页、应用、文件等都可以实现，[文档地址](http://wiki.mob.com/%E4%B8%8D%E5%90%8C%E5%B9%B3%E5%8F%B0%E5%88%86%E4%BA%AB%E5%86%85%E5%AE%B9%E7%9A%84%E8%AF%A6%E7%BB%86%E8%AF%B4%E6%98%8E/);下面看我是怎么一步一步实现分享链接到微信。

### 打开源码目录

红框内为需要的修改的地方

![](http://i.imgur.com/d0LfFw0.png)

### 修改ShareSDK.xml

确保BypassApproval=false,BypassApproval是绕过微信审核，直接打开微信对应界面，所以设置true会导致无法分享链接！

![](http://i.imgur.com/FSvK05O.png)

### 修改AndroidManifest.xml

添加微信分享回调，否则会出现崩溃或无法打开微信界面。

![](http://i.imgur.com/cCGs6hD.png)

### 修改MainActivity

红框内为修改地方，代码中注释的比较详细了

![](http://i.imgur.com/LtjDf2W.png)

### 打包apk

由于微信需要二次审核包名以及签名，需要先对应用签名打包，测试时可以用ShareSDk提供的demokey.keystore（keystore在sample项目中，密码123456）来进行签名；但如果项目中用到需要先去[微信开放平台](https://open.weixin.qq.com/cgi-bin/index?t=home/index&lang=zh_CN)申请个账号并创建应用，获取对应appid，然后替代ShareSDK.xml中对应的appid，打包安装即可。

### 最后，看运行效果图，perfect

朋友圈

![](http://i.imgur.com/d62KNue.jpg)

微信好友，嘿嘿

![](http://i.imgur.com/mdepkFH.png)