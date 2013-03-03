---
layout: post
title: android string.xml定义字符常用到的
category: Android开发
tags: null
---
{% include JB/setup %}
<strong></strong>加粗字体  
  
<em></em> 斜体字体  
  
给字体加下划线  
  
\n 换行  
  
\u0020表示空格  
  
\u2026 表示省略号  
  
&amp;#169; CopyRight的符号 ©  
  
使用&lt;b&gt;和&lt;b&gt;来打印出<strong></strong>这样的文字；“&lt;”表示“  
  
使用textView.setText(Html.fromHtml("Hello <strong>World</strong>,<span>AnalysisXmlActivty!</span>"));设置类似于html那样的效果  
  
如果你需要使用 String.format(String, Object...) 来格式化你的字符串，你可以把格式化参数放在你的字符串中，参见下面的例子：  
  
Hello, %1$s! You have %2$d new messages.  
  
在这个例子中，这个格式化的字符串有2个参数， %1$s是个字符串 %2$d 是个浮点数，你可以在你的程序中按照下面的方法来根据参数来格式化字符串：  
  
Resources res = getResources();  
  
String text = String.format(res.getString(R.string.welcome_messages), username, mailCount);  
  
那么根据例子上说的我需要把%s换成%1$s才行了，修改后编译通过，程序成功启动。  
  
问题补充：如何在中使用%号  
  
有两个办法可供选择  
1.用%%来表示1个%，和转意符号 \ 的用法相同  
  
2.如果你的字符串不需要格式化，可以在你的% test %即可  
  
就这么多吧，发现新的再加上！