---
title: thrift编译设置
date: 2018-03-18 18:54:59
tags: 编译thrift0.11
---


## thrift编译设置

***

* 附加包含目录
		Z:\libraries\thrift\thrift-0.11.0\lib\cpp\src;
		Z:\libraries\thrift\thrift-0.11.0\lib\cpp\src\thrift\windows;
		Z:\libraries\boost\boost_1_66_0;


* 预处理器定义
    	HAVE_CONFIG_H=1
		WIN32
		_DEBUG
		_CONSOLE

* 代码生成：
		DEBUG  运行库 MTD
		RELEASE 运行库 MT


* 预编译头
		不使用预编译头



* 附加依赖项
		libssl.lib
		libthrift.lib
		libcrypto.lib

* 附加库目录
		Z:\libraries\boost\boost_1_66_0\stage\lib;
		z:\libraries\openssl\OpenSSL-Win32\lib;
		Z:\libraries\thrift\thrift-0.11.0\lib\cpp\Debug-mt;



## 错误处理

使用vs2017编译thrift项目时出现以下错误：objbase.h(230): error C2760错误的解决的解决办法：
~~~cpp
#在stdafx.h中添加
#define WIN32_LEAN_AND_MEAN
~~~



## openssl 编译设置

* 动态编译
		WIN64
		perl Configure VC-WIN64A no-asm --prefix=z:\libraries\openssl\vc-64
		nmake clean
		nmake
		nmake test
		nmake install


* 静态编译
		makefile and configdata 两个文件中的/MD改为/MT
		perl Configure VC-WIN64A no-asm --prefix=z:\libraries\openssl\vc-64_static
		nmake clean
		nmake
		nmake test
		nmake install



## thrift 0.11.0编译问题及解决：

* 一、包含目录要加上openssl的目录引用
* 二、THttpserver.cpp与THttpclient.cpp中的
~~~cpp
//#include <thrift/config.h>此行改为
#include <thrift/thrift.h>
~~~

* 三、添加以下宏定义
~~~cpp
//在<thrift/thrift-config.h>中
#define PACKAGE_VERSION  "${PACKAGE_VERSION}"
~~~




## thrift客户端与服务器编译设置：（release编译设置静态编译WITH VS2017）

* c++常规--附加包含目录：
		Z:\libraries\thrift\thrift-0.11.0\lib\cpp\src
		Z:\libraries\thrift\thrift-0.11.0\lib\cpp\src\thrift\windows
		Z:\libraries\boost\boost_1_66_0
* 链接器--常规--附加库目录
		Z:\libraries\thrift\thrift-0.11.0\lib\cpp\release-mt
		Z:\libraries\boost\boost_1_66_0\stage\lib141
		Z:\libraries\openssl\OpenSSL-Win32\lib
* 链接器--输入--附加依赖项
		libthrift.lib
		libssl.lib
		libcrypto.lib





## 使用odb时自定义生成：

* 在项目中选中类文件如：employee.hxx  右键--属性--配置属性--常规--项类型 设置成：自定义生成工具

* 然后选中：自定义生成工具并设置如下：

	* 命令行：
			odb.exe --std c++11 --database sqlite --generate-query --generate-schema --table-prefix boost_ employee.hxx
    * 说明：
			odb employee.hxx
    * 输出：
			employee-odb.hxx
			employee-odb.ixx
			employee-odb.cxx




## docker使用hexo

* 1.安装Hexo
		docker run --name hexo -it -p 8083:80 -v `pwd`: /usr/share/nginx/html/source simplyintricate/hexo
* 2.发布一篇blog
		docker exec -it hexo hexo new "This is one post"



## ODB项目设置：

* 输入
		db-sqlite.lib;odb.lib
* 包含目录
		z:\libraries\orm\sqlite3\sqlite-amalgamation-3220000;
        z:\libraries\orm\odb2.4\libodb-2.4.0;
        z:\libraries\orm\odb2.4\libodb-sqlite-2.4.0;
* 库目录
    	z:\libraries\orm\sqlite3\;


## odb备注
	使用编译指令#pragma db transient 把字段声明为临时的，也就是该字段不保存与数据库中。


## Error: ENOSPC: no space left on device

查看存储空间

	$df -h

查看i节点

	$df -i

看是那种情况。

不幸的是我哪种都不是，后来在stackflow找到了答案。

问题原因:You may have reached your quota of watches.

解决办法

查看目前的最大值

To find your current limit, type this in your terminal:

	$cat /proc/sys/fs/inotify/max_user_watches


增加最大值

Which is typically 8192 by default.

To increase your limit, type this:

	$sudo sysctl fs.inotify.max_user_watches=16384

永久设置最大值

Then restart django.

To permanently set this limit, type this:

	$echo 16384 | sudo tee -a /proc/sys/fs/inotify/max_user_watches