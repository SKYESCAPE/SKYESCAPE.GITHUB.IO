---
layout: post
title: 仿ChinaTT乒乓球积分计算表Excel版
date: 2017-10-28
categories: blog
tags: [EXCEL,乒乓球]
description: 文章金句。
---

最近和球友打球，每周六一次比赛，前三名有奖品，但是前三名基本位置不变，于是商量打算使用积分制，然而，大家貌似都没有时间也不会对这个积分进行计算。

积分规则：

会员积分差 |分高胜加、分低负减|	分高负减/分低胜加
----|------|----
0-12      |8	            |8
13-37     |7	            |10
38-62     |6              |13
63-87     |5	            |16
88-112	  |4	            |20
113-137	  |3	            |25
138-162	  |2              |30
163-187	  |2              |35
188-212   |1	            |40
213-237   |1            	|45
238以上	   |0             |50


为此，我仿照ChinaTT写了一个可以根据输入自主计算乒乓球比赛积分的excel文档。效果如下：
![alt text](https://github.com/SKYESCAPE/SKYESCAPE.GITHUB.IO/raw/master/article_image/1_1.jpg)

首先介绍一下几个相关EXCEL函数
1. VLOOKUP函数(vertical-lookup,即竖直查找)</br>
基本语法：VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])，即VLOOKUP(查找值，查找范围，查找列数，精确匹配或者近似匹配）。</br>
作用：根据查找值参数，在查找范围的第一列搜索查找值，找到该值后，则返回值为：以第一列为准，往后推数查找列数值的这一列所对应的值。
2. IFS函数
基本语法：IFS([条件1, 值1, [条件2, 值2,],…[条件127, 值127,])</br>
作用：多个if嵌套函数
3. COUNTIF函数</br>
基本语法：COUNTIF（range，criteria）</br>
作用：对指定区域中符合指定条件的单元格计数
4. SUMIF函数</br>
基本语法：sumif(range,criteria,[sum_range])</br>
作用：条件求和
5. AND函数</br>
基本语法：and(logical1,logical2, ...)</br>
作用：检验一组数据是否同时都满足条件

思路：
1. 通过对人名的查找输出对应的积分，求积分差，例：VLOOKUP(G2,B$2:C$98,2)-VLOOKUP(N2,B$2:C$98,2)
2. 判断赢球或输球，查找积分区间，例：AND(H2>L2,0<=VLOOKUP(G2,B$2:C$98,2)-VLOOKUP(N2,B$2:C$98,2),12>=VLOOKUP(G2,B$2:C$98,2)-VLOOKUP(N2,B$2:C$98,2))
3. 返回对应的加减分，例：IFS(AND(H2>L2,0<=VLOOKUP(G2,B$2:C$98,2)-VLOOKUP(N2,B$2:C$98,2),12>=VLOOKUP(G2,B$2:C$98,2)-VLOOKUP(N2,B$2:C$98,2)),8)
4. 计算奖励积分，个人比赛场次计数与个人获胜场次比较，相等则翻倍，例：IF(COUNTIF(G:G,B2)+COUNTIF(N:N,B2)=(SUMIF(G:G,B2,J:J)+SUMIF(N:N,B2,O:O)),(SUMIF(G:G,B2,I:I)+SUMIF(N:N,B2,M:M)),0)
5. 对上次积分进行累加，例：SUMIF(G:G,B2,I:I)+C2+SUMIF(N:N,B2,M:M)+D2












