---
   layout: default
   title: 使用Visual Studio Code调试
   tags: ReactNative
---

# Visual Studio Code简介
Visual Studio Code 是微软推出的一个轻量级的开源 Web 集成开发环境，支持超过 30 种语言的开发，同时支持 Windows、Mac OS X、Linux 三大桌面平台。对于开发 React Native 而言，微软提供了专门的插件：React Native Tools，按照官网的说明进行插件的安装即可。这个插件使得开发者可以在 VS Code 中调试 React Native 代码，快速执行 react-native 命令，以及对 React Native 的 API 具备智能提醒功能，如下所示：

![](/assets/react-native/react-features.gif)

# 开始使用
首先你要按[React Native开发环境搭建]({% post_url /react-native/2017-08-23-React Native开发环境搭建%})这篇文章搭建好开发环境。

* 安装 VS Code [https://code.visualstudio.com/]().
* 运行VS Code安装插件:
    1. 左侧边栏点击"扩展"按钮，
    2. 搜索框中输入“react-native”找到“React Native Tools”，点击“安装”按钮。

# 调试
## 安装调试环境
点击左侧边栏调试按钮进入调试面板，点击齿轮图标按钮VS Code会自动创建并打开`.vscode/launch.json`配置文件，文件中会有一些默认数据。我们删除`configurations`中的数据，现在配置文件内容如下：
```json
{
    "version": "0.2.0",
    "configurations": [
    ]
}
```
在点击`添加配置`按钮，添加“React Native Debug iOS”

![](/assets/react-native/04.png)

现在的配置文件内容如下：
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug iOS",
            "program": "${workspaceRoot}/.vscode/launchReactNative.js",
            "type": "reactnative",
            "request": "launch",
            "platform": "ios",
            "sourceMaps": true,
            "target": "iPhone 5s",
            "outDir": "${workspaceRoot}/.vscode/.react"
        }
    ]
}
```
好了，现在在VS Code中按下`F5`稍后就可以看到app在iOS模拟器中运行起来，你可以修改`target`成所需的iOS模拟器。

## 调试iOS设备
调试iOS设备你需要手动完成以下步骤：

1. 安装[ideviceinstaller](https://github.com/libimobiledevice/ideviceinstaller)，`brew install ideviceinstaller`
2. 从调试配置下拉框选择**Debug iOS**并且按F5按键运行
3. 摇一摇设备，打开开发者菜单，并且选择"Debug JS Remotely"

![](/assets/react-native/45.png)

现在可以在VS Code中设置断点调试你的代码了。