---
   layout: default
   title: React Native 在真机上运行
   tags: ReactNative
---
项目在模拟器中运行成功以后就可以进行下一步操作，在真机上运行了。

# 开始
在真机上调试iOS软件必须要有一台Mac，把你的iPhone用数据线连接到Mac上，并接入同一WiFi。

# 配置项目
React Native生成的模板项目中包含了Android和iOS两部分，iOS项目在根目录的`ios`目录下，用Xcode打开`*.xcodeproj`项目文件。

Xcode在真机上调试需要Apple ID账号，React Native生成的项目没有配置好这些内容。所以编译编译时会出现类似下图的失败信息。
![](/assets/drafts/run-on-device/img/2017-09-29-17-47-17.png)
 
点击`Add Account`按钮，使用你的Apple ID登陆。  
![](/assets/drafts/run-on-device/img/2017-09-29-15-46-22.png)

添加账号以后显示信息如下，勾上”Automatically manage signing“。
![](/assets/drafts/run-on-device/img/2017-09-29-15-48-34.png)

 再次运行编译通过，APP部署到iPhone上运行时提示正式不受信任。
![](/assets/drafts/run-on-device/img/2017-09-29-16-16-47.png)

在iPhone的`设置`->`通用`->`设备管理`中信任你的证书即可运行。
![](/assets/drafts/run-on-device/img/2017-09-29-18-13-07.png)

如果还有其它异常情况，后面的两篇参考资料中都详细写有，本文就不在重复了。

# 调试
## 设置服务器IP
编辑`AppDelegate.m`文件。

```m
  NSURL *jsCodeLocation;

#if DEBUG
  [[RCTBundleURLProvider sharedSettings] setJsLocation:@"192.168.11.222"];
#endif
  
  jsCodeLocation = [[RCTBundleURLProvider sharedSettings] jsBundleURLForBundleRoot:@"index.ios" fallbackResource:nil ];

```

# 参考资料
* [如何配置React Native真机调试-iOS](http://www.cnblogs.com/yingsmirk/p/5224985.html)
* [Code signing is required for product type 'Application' in SDK 'iOS 10.0' - StickerPackExtension requires a development team error](https://stackoverflow.com/questions/37806538/code-signing-is-required-for-product-type-application-in-sdk-ios-10-0-stic)


