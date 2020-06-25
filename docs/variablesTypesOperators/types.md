# VBA 数据类型基础教程

在介绍 [VBA 变量](./variables.md)的教程中，初步学习了数据类型相关知识。VBA 中虽然不强制指定数据类型，但是正确使用数据类型，可以使程序更易理解，也能提高程序的运行效率。

## 文本类型

文本类型可以说是最常用的数据类型。实际中，几乎所有的数据均是文本类型。因此理解好文本是学习 VBA 的基础。

|类型	|说明	|数据范围
|---|---|---
|String	|文本类型	|0 至 20亿字符

首先，声明一个文本类型变量，String是类型标识符，语法如下：
```vba
Dim name As String
```
VBA 中，文本需使用英文双引号表示。
```vba
name = "Zhang San"
```
如果把数字两端加上双引号，它会变成文本类型，不再表示数字
```vba
name = "101"
```
可以使用单元格内的文本，给文本类型变量赋值。
```vba
name = Range("A1")
```
与 Excel 提供的文本函数一样，VBA 也提供多种文本函数，可直接在程序中使用，包括：

* Format：格式化数据，并以文本类型返回
* InStr：返回指定字符的位置
* InStrRev：反方向返回指定字符位置
* Left：返回左侧指定长度文本
* Len：返回文本长度
* LCase：大写字母转换成小写字母
* LTrim：清除开头的空格
* Mid：返回指定的开始和结束位置之间的文本
* Replace：替换文本中的指定字符
* Right：返回右侧指定长度文本
* RTrim：清除末尾处的空格
* Space：返回指定重复数的空格文本
* StrComp：返回比较两个文本的结果
* StrConv：将文本转换成指定格式
* String：返回指定重复数的文本
* StrReverse：逆转提供的字符串
* Trim：清除开头和结尾处的文本
* UCase：将小写字母转换成大写字母

每个函数的用法，在「内置函数」一章中详细介绍。

## 数字类型

数字类型是第二个基础数据类型。在写 VBA 代码时，应根据具体的数字大小，选择合适的数字类型。

如果小数字使用大范围数字类型存储，会浪费计算机内存；如果大数字使用小范围的数字类型存储，VBA 会自动转换成对应小范围数字，导致数字丢失精度。[VBA 中的数字类型](./variables.md#数字类型)。

与文本相似，声明数字类型，使用如下语句：
```vba
Dim age As Integer
```
以上定义一个岁数变量，使用基本的 Integer 整数类型即可。

数字类型变量可以像数字一样，参与各类算数运算：
```vba
age = 3
age * 2 + 10 ‘-> 16
```

## 逻辑类型

逻辑类型只有两个值，True 和 False，即真与假。

|类型	|说明	|数据范围
|---|---|---
|Boolean	|逻辑值	|True 或 False

逻辑值虽然只有两个，但是在程序中有着广泛的应用。VBA 中判断语句中，经常能用到逻辑值。

首选，声明一个逻辑变量，使用如下语句：
```vba
Dim isPass As Boolean
```
给逻辑变量赋值是，可以直接使用逻辑值，也可以使用返回逻辑值的表达式。
```vba
isPass = False
isPass = 70 >= 60
```

## 日期和时间类型

VBA 中的日期和时间使用数字表示，整数部分代表日期，小数部分代表时间。

* 日期从 100-1-1 开始到 9999-12-31。
* 时间从 00:00:00 到 23:59:59。

声明日期类型变量，使用如下语句：
```vba
Dim birthday As Date
Dim time As Date
```
给日期变量赋值时，可以直接把日期放置在两个 # 之间赋值，也可以使用数字，还可以把日期作为文本赋值：
```vba
birthday = #2018-1-1#
birthday = 43101
birthday = "2018-1-1"

time = #12:00:00#
time = 0.5
time = "12:00:00"
``` 

## Variant 类型

Variant 类型是一种通用类型，可以表示任何一种类型的数据。它也是声明变量未指定数据类型时的默认类型。

> 虽然 Variant 类型方便，但是相应的，占用更大的内存空间，也会影响程序运行效率。因此建议，在明确知道数据时何种类型时，指定数据类型；如果数据类型是可变的或不明确，使用 Variant 类型。

