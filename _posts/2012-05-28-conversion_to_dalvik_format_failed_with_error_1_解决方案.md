---
layout: post
title: conversion to dalvik format failed with error 1 解决方案
category: Android开发
tags: null
---
{% include JB/setup %}
     conversion to dalvik format failed with error 1        
被这个莫名奇妙的错误吓到了，google了下，发现error 1这个错误主要是包冲突引起的。这个project刚刚就引用了一个gson的包。  
试着取消gson包就没有问题了。还以为是gson包有问题。  结果是在创建项目那个libs目录的时候，在eclipse选择的是new->source folder。  
自己手动重建文件夹就解决了。  
   突破口在jar包冲突。找到这个原因，应该很快就能解决这个错误。 