---
layout: post
title: Solved: Unexpected ATTRIBUTE in parse rule PropertyElement ::= . PROPERTYELEMENT Content? ENDTAG..
category: silverlight开发
tags: null
---
{% include JB/setup %}
Solved: Unexpected ATTRIBUTE in parse rule PropertyElement ::= . PROPERTYELEMENT Content? ENDTAG..  
 This error can occur for many different controls (almost any XAML element); DataGrid, Grid, Canvas, Border, Frame, Button.  This error basically means that you have invalid attributes in one of your XAML tags.   
Check the tag that the error reports.  It is likely you have an attribute in there that is not valid.  The error sucks and should report this better.  But apparently even with Visual Studio 2010 and Silverlight 4 this still occurs.  
在silverlight的编码中出现这个错误。最后发现，我是在xaml里改写了视图的继承，而没有在后台代码里改写继承关系引起的错误。  
修改xaml和后台代码，使其保持一致即可