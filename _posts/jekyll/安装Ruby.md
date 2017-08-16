# 环境
* macOS

## 安装ruby
ruby 版本必须大于2.1，我的系统环境是2.0的安装失败。
1. 安装 RVM

```
$ curl -L get.rvm.io | bash -s stable 
$ source ~/.bashrc  
$ source ~/.bash_profile  
```
2. 测试是否安装成功
```
$ rvm -v 
```
3. 用RVM升级Ruby
```sh
#查看当前ruby版本  
$ ruby -v  
ruby 2.0.0p648 (2015-12-16 revision 53162) [universal.x86_64-darwin16] 
#列出已知的ruby版本  
$ rvm list known  
#安装ruby 最新版
$ rvm install 2.4.1
#设置为默认版本
$ rvm use 2.1.4 --default
```

4. 设置Shell环境

安装好ruby 2.4.1以后，关闭控制台再进入ruby -v显示还是旧版，而且也找不到rvm命令，就需要修改Shell环境配置。打开`/Users/YOUR_NAME/.bash_profile`文件，请将`YOUR_NAME`替换成你的系统账号名称。

```sh
sudo vim /Users/YOUR_NAME/.bash_profile 
```
加入这一行后保存退出
```
source ~/.profile
```
再进入控制台rvm命令就可以正常使用了。

5. 更换源

查看已有的源
```
gem sources
```

显示会如下：
```
*** CURRENT SOURCES ***

https://rubygems.org/
```
然后我们需要来修改更换源（由于国内被墙）所以要把源切换至Ruby China镜像服务器。yRubyGems建议 2.6.x 以上，所以先更新它。
在终端执行以下命令
```sh
# update --system这步需要翻墙
$ gem update --system
$ gem uninstall rubygems-update
#更换源
$ gem sources -r https://rubygems.org/
$ gem sources -a https://gems.ruby-china.org
$ gem sources
```
确保显示一下信息。
```
*** CURRENT SOURCES ***

https://gems.ruby-china.org
```
