---
layout: post
title: linux shell
category: 杂
tags: null
---
{% include JB/setup %}
翻到一年多前写的第一个bash shell， 想想现在的自己，突然有种厌恶，有种鄙夷。  
是对自己的期望过高？ 或是那一切太理想化了。  
脚踏实地最重要，但理想不灭！  
贴上代码，自免  
     #!/bin/bash  
#program:  
#       This program:  
# History  
#2011/  PCD     First release  
PATH=/bin:/sbin:/usr/bin:/usr/local/bin:/usr/local/sbin:~/bin  
export PATH  
read -p "Please enter a number:" num  
declare -i acc  
acc=0  
declare -i test  
for test in $(seq 1 ${num})  
do  
   acc=${acc}+${test}  
  # echo "acc= " $acc  
done  
#print ${acc}  
echo "Resualt = " $acc  
 