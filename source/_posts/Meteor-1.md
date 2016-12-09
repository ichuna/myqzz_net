---
title: Meteor入门
date: 2016-09-29 16:40:45
tags: 你的第一个Meteor应用
---



### 命令行

* 在Mac OS X系统中, 命令行是 Terminal.
* 在Windows系统中, 命令行的名字是“命令提示符”。（或开始，运行 CMD）
* 在Linux系统中, 例如ubuntu ，命令行应用也是Terminal。

### 安装

Meteor支持的平台：
• Mac: OS X 10.7 及以上
• Windows:
– Windows 7
– Windows 8.1
– Windows Server 2008
– Windows Server 2012
• Linux: x86 and x86_64 

在Windows上安装Meteor最简单，直接从官网www.meteor.com下载安装文件并运行就可以了。（不过由于网站在国外，所以，您需要点面耐心。）如果您使用 Mac OS X 或 Linux ,请将下列命令复制到命令行中，回车运行。

```
 curl https://install.meteor.com/ | sh

```

这行命令会执行以下操作:
1. 连接到 “install.meteor.com”.
2. 下载最新版本的 Meteor.
3. 安装Meteor.

在linux或mac os系统上，如果向您询问密码，请输入并回车，这是校验您是否有安装Meteor到您的计算机上的权限。

### 创建项目

尽管项目各不相同，但我们的Meteor项目通常包含如下内容：
• HTML 文件, 用以创建页面.
• CSS 文件, 用以应用样式到页面.
• JavaScript 文件, 用以定义应用程序逻辑.
• Folders, 用以组织不同类型文件.

项目可以包含其它类型的文件, 如图片等, 但我们现在尽量保持我们的项目尽可能简单，只包含我们需要的东西。这里我们要创建的项目名为 Leaderboard，在创建项目之前，我们先为我们的Meteor项目创建一个目录。

在命令行中输入：

```
mkdir Meteor

```
并回车。

```
cd Meteor

```

进入新创建的目录。在此目录下创建项目，运行以下命令：

```
meteor create leaderboard

```

该命令包含三个部分：
• meteor 定义这是一个 Meteor 命令.
• create 表示我们要创建一个 Meteor 项目.
• leaderboard 是我们要创建的项目的名字.

命令运行完成后，会在当前目录下生成一个 “leaderboard” 目录,默认情况下此目录下会包含以下三个文件：

• leaderboard.html
• leaderboard.css
• leaderboard.js

另外它还包含一个名为  .meteor 的隐藏目录，这个我们不要管它，它提供了Meteor的功能支持。

### 运行

要想运行我们刚才建立的应用程序，请在命令行中输入以下命令：

```
cd leaderboard
```

然后，输入:

```
meteor 
```

输入回车后，命令行中将会显示以下内容:

```
=> Started proxy.
=> Started MongoDB.
=> Started your app.
=> App running at: http://localhost:4000/
```

我们新创建的Meteor应用已经成功运行，请打开浏览器，访问地址  http://localhost:4000。


至此，我们的第一个Meteor应用已经成功运行。