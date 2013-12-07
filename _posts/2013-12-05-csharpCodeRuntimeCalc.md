---
layout: post
title: "Csharp计算代码运行时间"
description: "Csharp计算代码运行时间"
category: 技术 
tags: [CSharp]
---
{% include JB/setup %}
     Stopwatch watch = new StopWatch();
	 watch.Start();
	 RunCode();/* Code run*/
	 watch.Stop();
	 string time = watch.ElapsedMilliseconds.ToString();
	 ----------------------------------------
	 这里用到System.Diagnostics 命名空间。测试自己代码效率和查错的时候很有用。