---
layout: post
title: android jar引用java.lang.NoClassDefFoundError 
category: Android开发
tags: [android , jar , 包引用 , class not found ]
---
{% include JB/setup %}
  android开发环境升级ADT18版本后，编译以前的项目，提示“java.lang.NoClassDefFoundError: ****”  后面跟的class是引用的jar包中的一个类  
   
 解决办法：  
     把jar包放到项目下的libs里才可以找到，否则apk不会包含该jar包--！所以会有类型引用异常的错误。之前是放在lib中不是libs 修改后正常