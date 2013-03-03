---
layout: post
title: Ubuntu下简单编译Objective-C <一>
category: Linux
tags: null
---
{% include JB/setup %}
当然是用gcc编译咯，首先要有gobjc 的支持。  
     awp@awpc:~$ sudo apt-get install gobjc   
安装完毕后，就可以try try了，  
   /* 建立一个文本*/  
     awp@awpc:~$ touch hello.m   
   /* vi编辑文本*/  
     awp@awpc:~$ vim hello.m    
   /*Hello World 程序 wq保存完毕*/  
       
#import  
  
int main(int argc, const char *argv[])  
{  
printf("Hello World\n");  
return 0;  
}  
   
   /* 编译hello.m文件，并且输出名为hello， */  
   /* -Wall参数是打开警告选项 */  
   /* -lobc参数是链接GNU的objc库，这个参数比较重要，如果不手动加入，可能会导致编译失败*/  
     awp@awpc:~$ gcc -o hello hello.m -Wall -lobjc   
   /*最后执行结果*/  
     awp@awpc:~$ ./hello  
Hello World  
 