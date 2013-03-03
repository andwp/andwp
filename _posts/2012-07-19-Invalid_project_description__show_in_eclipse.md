---
layout: post
title: Invalid project description  show in eclipse
category: Android开发
tags: [eclipse android ]
---
{% include JB/setup %}
描述：Import -&gt; android - &gt; Exsiting Android Code Into Workspace  
弹出如下错误：  
     Invalid project description   
------&gt;detail: -&gt;&gt;&gt; xxxx(project path) overlaps the location of another project: 'xxxx'   
然后Import项目失败.  
产生原因： 具体原因不详细，也许是以前创建的workspace里面包含了Project的信息，现在引入project发生了冲突。  
  
解决方案: 解决办法很简单，Import -&gt; General - &gt; Exsiting Projects Into Workspace成功引入  
然后在project上右键-&gt;properties-&gt;Android-&gt;选择Project Build Target