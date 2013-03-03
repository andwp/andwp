---
layout: post
title: winForm实现Tabpage隐藏
category: Windows
tags: [c# winForm ]
---
{% include JB/setup %}
尝试用tabpage.Hide() 发现是没有用的。  
其实tabpage都对应有一哥tabControl父控件，把tabpage的父控件设置成null就可实现tabpage的隐藏。tabpage.Parent = null;  
恢复只需要设置回去就可以了  
tabpage.Parent = tabControl1