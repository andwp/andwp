---
layout: post
title: sql中left join、right join的简单说明(转载)
category: SQL
tags: null
---
{% include JB/setup %}
<div>  
  
<span style="font-family: Verdana;">[本文未找到原始出处]  
数据库常见的join方式有三种：inner join, left outter join, right outter join(还有一种full join，因不常用，本文不讨论)。这三种连接方式都是将两个以上的表通过on条件语句，拼成一个大表。以下是它们的共同点：</span>  
  
<span style="font-family: Verdana;">1. 关于左右表的概念。左表指的是在SQL语句中排在left join左边的表，右表指的是排在left join右边的表。 2. 在拼成的大表中，左表排在左边，右表排在右边。 3. on条件语句最好用=号对两表相应的主外键进行连接。当然，也可以用其他操作符，如&gt;, &lt;, 来连接两表的任一字段，此时的关系将非常复杂，连接后的记录数也随之而变得不确定。如果在一些特殊的场合中需要用到这种方式，必须通过简单的实例加以确认，否则，连接结果很可能不是我们所想要的！ 4. on条件语句不能省略。 5. 可以连锁使用join，每次使用join都令另一表与当前的表或连接的结果相连接。</span>  
  
<span style="font-family: Verdana;">在下文中，用到了两个表，"部门"表与"组织"表，其中，"部门"表有一名为"组织编号"的外键，指向"组织"表中的主键"编号"。</span>  
  
<span style="font-family: Verdana;"><strong>inner join</strong></span>  
  
<span style="font-family: Verdana;">格式：select * from 部门 inner join 组织 on 部门.组织编号 = 组织.编号</span>  
  
<span style="font-family: Verdana;">目的：将两表中符合on条件的所有记录都找出来。</span>  
  
<span style="font-family: Verdana;">规律：</span>  
  
<span style="font-family: Verdana;">1. 拼出的大表记录不会增加。 2. 如果左边与右表的关系是一对多的关系，在选出的任一记录中，假若右表有多个记录与其对应，那么，连接后的左表，主键将不再唯一。</span>  
  
<span style="font-family: Verdana;">典型应用：将存在多关系的引用表放在左表，将存在一关系的被引用表放在右表，通过=号将主外键进行连接，通过对右表设定过滤条件，选出相应的且主键唯一的左表记录。</span>  
  
<span style="font-family: Verdana;">备注：inner join 是默认的连接方式，可缩写为join。</span>  
  
<span style="font-family: Verdana;">转化为where子句：</span>  
  
<span style="font-family: Verdana;">select * from 部门, 组织 where 部门.组织编号 = 组织.编号</span>  
  
<span style="font-family: Verdana;"><strong>left outter join</strong></span>  
  
<span style="font-family: Verdana;">格式: select * from 部门 left join 组织 on 部门.组织编号 = 组织.编号</span>  
  
<span style="font-family: Verdana;">格式: select * from 组织 left join 部门 on 组织.编号 = 部门.组织编号</span>  
  
<span style="font-family: Verdana;">目的：将左表的所有记录列出，右表中只要符合on条件的，与左表记录相拼合，不符合条件的，填以null值。</span>  
  
<span style="font-family: Verdana;">规律：</span>  
  
<span style="font-family: Verdana;">1. 选出所有符合条件的左表，如果左边与右表的关系是一对一的关系，则拼成的大表记录不会改变。 如果左边与右表的关系是多对一的关系，则拼成的大表记录也不会改变。 如果左边与右表的关系是一对多的关系，则拼成的大表记录会增加。对于每一具有一对多关系的左表记录，如果左表1：N与右表对应，那么会多出N-1条记录。例如，如果左表第一条记录1：3对应于右表，多出2条记录。如果左表第二条记录1：2对应于右表，则再多出1条记录。这样，总共多出3条记录。其他类推。 2. 如果左边与右表的关系是一对多的关系，在选出的任一记录中，假若右表有多个记录与其对应，那么，连接后的左表，主键将不再唯一。 3. 如果左边与右表的关系是一对多的关系，对于左表任一记录，如果右表没有记录与其相对应，则全部填以null值。</span>  
  
<span style="font-family: Verdana;">典型应用：将存在多关系的引用表放在左表，将存在一关系的被引用表放在右表，通过对右表设定过滤条件，选出相应的且主键唯一的左表记录。</span>  
  
<span style="font-family: Verdana;">备注：left outter join可用left join代替。在有些数据库中，如HSqlDb, 只能使用left join而不能使用left outter join。</span>  
  
<span style="font-family: Verdana;">转化为where子句：</span>  
  
<span style="font-family: Verdana;">select * from 部门, 组织 where 部门.组织编号 = 组织.编号</span>  
  
<span style="font-family: Verdana;"> <strong>right outter join</strong></span>  
  
<span style="font-family: Verdana;">格式: select * from 部门 right join 组织 on 部门.组织编号 = 组织.编号</span>  
  
<span style="font-family: Verdana;">格式: select * from 组织 right join 部门 on 部门.组织编号 = 组织.编号</span>  
  
<span style="font-family: Verdana;">目的：将右表的所有记录列出，左表中只要符合on条件的，与右表记录相拼合，不符合条件的，填以null值。</span>  
  
<span style="font-family: Verdana;">规律：(与left outter join相反)</span>  
  
<span style="font-family: Verdana;">典型应用：可转化成left outter join。例如</span>  
  
<span style="font-family: Verdana;">select * from 组织 right join 部门 on 部门.组织编号 = 组织.编号 与 select * from 部门 left join 组织 on 部门.组织编号 = 组织.编号 的效果一样</span>  
  
&nbsp;  
  
&nbsp;  
  
&nbsp;  
  
假设有A，B两个表。  
表A记录如下：  aID　　　　　aNum  1　　　　　a20050111  
2　　　　　a20050112  3　　　　　a20050113  4　　　　　a20050114  
5　　　　　a20050115  
表B记录如下:  bID　　　　　bName  1　　　　　2006032401  
2　　　　　2006032402  3　　　　　2006032403  4　　　　　2006032404  
8　　　　　2006032408  
--------------------------------------------  
1.left join  sql语句如下:   select * from A  left join B  
on A.aID = B.bID  
结果如下:  aID　　　　　aNum　　　　　bID　　　　　bName  
1　　　　　a20050111　　　　1　　　　　2006032401  
2　　　　　a20050112　　　　2　　　　　2006032402  
3　　　　　a20050113　　　　3　　　　　2006032403  
4　　　　　a20050114　　　　4　　　　　2006032404  5　　　　　a20050115　　　　NULL　　　　　NULL  
（所影响的行数为 5 行）  结果说明:  
left join是以A表的记录为基础的,A可以看成左表,B可以看成右表,left join是以左表为准的.  
换句话说,左表(A)的记录将会全部表示出来,而右表(B)只会显示符合搜索条件的记录(例子中为: A.aID = B.bID).  
B表记录不足的地方均为NULL.  --------------------------------------------  
2.right join  sql语句如下:   select * from A  right join B  
on A.aID = B.bID  
结果如下:  aID　　　　　aNum　　　　　bID　　　　　bName  
1　　　　　a20050111　　　　1　　　　　2006032401  
2　　　　　a20050112　　　　2　　　　　2006032402  
3　　　　　a20050113　　　　3　　　　　2006032403  
4　　　　　a20050114　　　　4　　　　　2006032404  NULL　　　　　NULL　　　　　8　　　　　2006032408  
<div>软件开发网 www.mscto.com</div>  
（所影响的行数为 5 行）  结果说明:  
仔细观察一下,就会发现,和left join的结果刚好相反,这次是以右表(B)为基础的,A表不足的地方用NULL填充.  
--------------------------------------------  3.inner join  
sql语句如下:   select * from A  innerjoin B   on A.aID = B.bID  
结果如下:  aID　　　　　aNum　　　　　bID　　　　　bName  
1　　　　　a20050111　　　　1　　　　　2006032401  
2　　　　　a20050112　　　　2　　　　　2006032402  
3　　　　　a20050113　　　　3　　　　　2006032403  
4　　　　　a20050114　　　　4　　　　　2006032404  
结果说明:  
很明显,这里只显示出了 A.aID = B.bID的记录.这说明inner join并不以谁为基础,它只显示符合条件的记录.  
--------------------------------------------  PS:  
LEFT JOIN操作用于在任何的 FROM 子句中，组合来源表的记录。使用 LEFT JOIN 运算来创建一个左边外部联接。左边外部联接将包含了从第一个（左边）开始的两个表中的全部记录，即使在第二个（右边）表中并没有相符值的记录。  
语法：FROM table1 LEFT JOIN table2 ON table1.field1 compopr table2.field2  
说明：table1, table2参数用于指定要将记录组合的表的名称。  
field1, field2参数指定被联接的字段的名称。且这些字段必须有相同的数据类型及包含相同类型的数据，但它们不需要有相同的名称。  
compopr参数指定关系比较运算符："="， "&lt;"， "&gt;"， "&lt;="， "&gt;=" 或 "&lt;&gt;"。  
如果在INNER JOIN操作中要联接包含Memo 数据类型或 OLE Object 数据类型数据的字段，将会发生错误  
注：left和right是外连接，Inner是内连接。</div>