---
   layout: default
   title: React Native 开发环境搭建
   tags: ReactNative
---

# {{ page.title }}
{{ page.date | date: "%Y-%m-%d" }}

# 目标
今天我要在Macbook上搭建React Native开发环境，实现使用Visual Studio Code编辑和调试iOS APP的目的。

最后完成的环境如下：
1. macOS Sierra 10.12.6
1. Xcode 8.3.3
2. Nodejs v8.4.0
3. Visual Studio Code 1.15.1
4. react-native-cli 2.0.1
5. react-native 0.47.2

# 安装
## 必需的软件
你必须安装Node、Watchman、React Native cli和Xcode。

## Node,Watchman
推荐使用[Homebrew](http://brew.sh)安装Node和Watchman。在终端中运行一下命令安装：
```
brew install node
brew install watchman
```
[Watchman](https://facebook.github.io/watchman/)是由Facebook提供的监视文件系统变更的工具。安装此工具可以提高开发时的性能（packager可以快速捕捉文件的变化从而实现实时刷新）。

> 我在使用homebrew在安装软件Node时遇到/usr/local目录不可写的权限问题。可以使用下面的命令修复：
```
sudo chown -R `whoami` /usr/local
```

安装完node后建议设置npm镜像以加速后面的过程（或使用科学上网工具）。这里设置为淘宝的镜像。
```
npm config set registry https://registry.npm.taobao.org --global
npm config set disturl https://npm.taobao.org/dist --global
```

## React Native CLI
React Native的命令行工具用于执行创建、初始化、更新项目、运行打包服务（packager）等任务。  
在终端中运行以下命令安装：
```
npm install -g react-native-cli
```
> If you get an error like Cannot find module 'npmlog', try installing npm directly: curl -0 -L https://npmjs.org/install.sh | sudo sh.
## Xcode
React Native目前需要Xcode 8.0 或更高版本。这个比较简单在App Store下载即可。这一步骤会同时安装Xcode IDE和Xcode的命令行工具。

> 虽然一般来说命令行工具都是默认安装了，但你最好还是启动Xcode，并在Xcode | Preferences | Locations菜单中检查一下是否装有某个版本的Command Line Tools。Xcode的命令行工具中也包含一些必须的工具，比如git等。

# 创建APP
使用React Native命令行工具创建一个名为“AwesomeProject”的React Native新项目。
```
react-native init AwesomeProject
```
# 运行APP
在项目目录中执行`react-native run-ios`命令启动app:
```
cd AwesomeProject
react-native run-ios
```
稍后会看到你的新app在iOS模拟器中运行。

![](images/2017-08-24-08-31-01.png)

## 在真机上运行
默认情况下上述命令会自动打开iOS模拟器运行你的app，如果你希望在真机上运行请参考 
[在真机上运行]({% post_url /react-native/2017-08-24-React Native在真机上运行%})。

## 修改你的APP
现在你的app已经成功的运行起来，修改一下试试。
1. 使用文本编辑器打开`index.ios.js`文件，试试修改里面的文本后保存。
2. 在iOS模拟器窗口使用`⌘R`键重新加载app后可以看到你修改后的内容

> 文本编辑器我使用的是Visual Studio Code，可以在[https://code.visualstudio.com/]()下载安装。