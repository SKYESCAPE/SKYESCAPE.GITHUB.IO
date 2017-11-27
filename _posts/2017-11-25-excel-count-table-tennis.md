---
layout: post
title: 仿ChinaTT乒乓球积分计算表Excel版
date: 2017-10-28
categories: blog
tags: [EXCEL,乒乓球]
description: 文章金句。
---

最近和球友打球，每周六一次比赛，前三名有奖品，但是前三名基本位置不变，于是商量打算使用积分制，然而，大家貌似都没有时间也不会对这个积分进行计算。

积分规则：</br>
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

作者：简书
链接：http://www.jianshu.com/p/q81RER
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

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

思路：</br>
1. 加分减分计算：












