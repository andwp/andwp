---
layout: post
title: Android导入第三方jar包，proguard混淆脚本(屏蔽警告，不混淆第三方包)
category: Android开发
tags: null
---
{% include JB/setup %}
警告会导致build不能通过。  
  
-ignorewarnings //这1句是屏蔽警告，脚本中把这行注释去掉