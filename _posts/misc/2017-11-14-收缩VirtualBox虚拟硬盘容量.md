---
   layout: default
   title: 收缩Virtualbox虚拟硬盘容量
   tags: VirtualBox
---


# {{ page.title }}
{{ page.date | date: "%Y-%m-%d" }}

Virtualbox运行一段时间后，虚拟硬盘占用的磁盘空间越占越大，但是虚拟机内部却没有这么多的文件。来看看我的Windows 10虚拟机，内部文件总大小只有16G左右，但是虚拟硬盘已经达到52G之多。现在让我们减少这个文件，回收空余的空间拯救可怜的256G SSD。

### 收缩之前的磁盘容量

![](/assets/misc/收缩Vitualbox虚拟硬盘容量/img/2017-11-14-09-58-04.png)

## 方法
1. 清理磁盘
先下载[Sysinternals Suite](https://docs.microsoft.com/zh-cn/sysinternals/downloads/sysinternals-suite)。在虚拟机中解压以后，使用`SDelete`工具来清空虚拟机已删除的文件空间。

```cmd
sdelete.exe -z c:

SDelete v2.0 - Secure file delete
Copyright (C) 1999-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

SDelete is set for 1 pass.
Free space cleaned on C:\
1 drive cleaned.
```
经过一段时间后磁盘清理完毕，然后关闭虚拟机。

如果你的虚拟硬盘是VirtualBox自己的VDI格式，找到你的虚拟硬盘文件，执行命令：

```
VBoxManage modifyhd Windows 10.vdi --compact
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
```
当当当，等到进度走到100%，完成看看效果。  
虚拟硬盘文件只有21G了，一下缩小了30G。对于256G硬盘的电脑来说增加了11%的剩余空间，成果不错。
![](/assets/misc/收缩Vitualbox虚拟硬盘容量/img/2017-11-14-14-40-23.png)

### 参考资料
* SDelete v2.0  
https://docs.microsoft.com/zh-cn/sysinternals/downloads/sdelete

* 减小VirtualBox虚拟硬盘文件的大小  
http://www.cnblogs.com/findumars/p/3897818.html
