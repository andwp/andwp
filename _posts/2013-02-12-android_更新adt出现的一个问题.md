---
layout: post
title: android 更新adt出现的一个问题
category: Android开发
tags: null
---
{% include JB/setup %}
项目报错：  
Errors occurred during the build.  
errors running builder 'Android Pre Compiler' on project'项目名称'  
java.lang.NullPointerException.  
  
一直找不到原因。一直报错，没有办法生成R.java 文件。然后我重新建立项目，把以前项目的源码导进去，不报错了。隔了没多久又开始发作。  
实在没有办法了。google了一个人同样的错误，他说是svn的问题。但是我没有用过svn，只用git。而新建的项目也没有来得及用git托管。。。  
保证小心求证的态度，搜索了下项目所在目录       find -name .svn    
竟然出现了7个结果。。。（估计是以前的项目用svn托管过。然后这个项目用到了以前项目的一些包，全是整包copy过来的。）  
新版的adt加强了对项目文件中的异常类型文件的识别，所以在遇到.svn时报了空指针的错误。。  
解决问方法：删除掉项目文件夹下所有的.svn目录，重启eclipse并重新编译。  
如果想保留svn的文件，估计可以通过排除编译路径解决。-》打开Eclipse中的Project->Properties->JavaBuildPath菜单，在右侧面板中的"Source"选项卡，在Excluded中加入  "**/.svn/**"。