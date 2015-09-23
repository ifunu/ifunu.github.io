---
layout: post
title: "liunx下sublime text3配置"
date: 2015-07-13
---

Sublime Text 3的下载安装

安装Package Control

源码地址：

https://github.com/wbond/package_control_channel

安装非常方便，使用git将该代码先克隆下来即可。

拷贝到~/.config/sublime-text-3/Packages/目录下并命名为Package Control即可。

也可以直接在github上打包下载，然后解压复制到~/.config/sublime-text-3/Packages/目录下并命名为Package Control.


```
cd ~/.config/sublime-text-3/Packages/
git clone https://github.com/wbond/package_control_channel.git Package\
 Control
```


重新启动SublimeText 3，然后使用快捷键Ctrl + Shift + p.

弹出的输入框中输入Package Control则可以看到Install Package的选项。

会弹出插件查询及安装窗口，输入想用的插件，选中回车即可。
