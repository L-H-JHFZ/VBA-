# VBA 变量的声明和赋值

[TOC]

## 什么是声明变量
在《[VBA 变量](../variablesTypesOperators/variables.md)》一文中介绍，变量是一个存储数据的 VBA 代码结构。在代码中，通过变量名获取变量所代表的的值。而声明变量，就是告诉 VBA，变量的名字和它所存储的值的数据类型。

VBA 中声明变量，有 4 种变量，它们是：

* **基本类型变量**。基本类型变量是那些存储单个数据的变量，例如数字、文本、日期等。
* **通用变量**。通用变量，即 Variant 类型变量。该变量的类型在程序运行过程中，根据赋值的数据自动指定。
* **数组**。数组包含多个变量的集合。
* **对象**。对象包含一些列属性和方法。

## 声明语句的基本语法

4 种类型的变量的声明方法基本一致。

### 1.基本类型变量
```vba
'语法
Dim [变量名] As [数据类型]

'实例
Dim name As String
Dim age As Integer
Dim height As Double
Dim birthday As Date
```
### 2.通用变量

声明 Variant 类型变量时，如果忽略数据类型，默认情况是 Variant 类型，因此下方两种方式是相同的。
```vba
'语法
Dim [变量名] As Variant
Dim [变量名]

'实例
Dim message As Variant
Dim message
```
### 3.数组
```vba
'语法
'固定长度数组声明
Dim [变量名](开始序号 to 结束序号) As [数据类型]
'动态数组声明
Dim [变量名]() As [数据类型]

'实例
'声明包含10个文本类型元素的数组
Dim names(1 to 10) As String
'声明长度未知的文本类型数组
Dim names() As String
```
### 4.对象

声明对象时，一般有两种方式。一种是前期绑定，即一开始就指定对象的类型；一种是后期绑定，即声明时不指定对象类型，后期指定。
```vba
'语法
'前期绑定声明语法
Dim [变量名] As [对象类型]
'后期绑定声明语法
Dim [变量名] As Object

'实例
Dim sh As Worksheet
Dim car As Object
```

## 在哪里写声明语句
声明变量，意思是在使用变量前，告诉 VBA，变量的名字和数据类型。因此，声明变量的语句，必须写在使用它的语句前。

### 错误写法
```vba
name = "Zhang San"
Dim name As String
```
> 如果先于声明语句前使用变量，VBA 会报「变量未定义」错误。

### 正确写法
```vba
Dim name As String
name = "Zhang San"
```

## 如何声明多个同类型变量

通过以上部分的学习，在写多个同类型变量的声明语句时，有人可能会按以下方式写：
```vba
'声明两个整数类型的 i、j 变量
Dim i,j As Integer
```
首先，以上写法，语法上没问题，不会出现错误。但是，这种方式声明变量，Integer 类型只作为第二个 j 变量的数据类型。第一个变量，即 i 变量，它的数据类型时 Variant，并不是 Integer 类型。

因此，VBA 中不能合并声明语句。正确的声明方法如下：
```vba
'第一种，按两行写
Dim i As Integer
Dim j As Integer

'第二种，使用 : 符号，在一行写
Dim i As Integer : Dim j As Integer
```
## 声明变量是必须的吗

准确来讲，VBA 中声明变量不是必须的。也就是说，没有声明变量，而直接开始用，也没有错误。

> 但是，不声明变量，是一种不好的习惯，也常常会带来很多错误。这也是为什么之前的教程中都没有提到这点的原因。

不声明变量典型弊端包括：

* 数据类型自动设置为 Variant 类型，效率低。
* 变量名写错，不会提示错误。
* 无法使用 VBA 代码自动补全。
* 数据类型不匹配时，不会提示错误。

**基于以上原因，强烈建议，每次使用变量，都要声明其变量名和数据类型。**

VBA 提供一个选项，可以强制变量声明，即在模块头部写上以下语句：
```vba
Option Explicit
```

模块中有以上语句时，如果未声明变量而直接使用变量，VBA 会提示「**变量未定义**」错误，方便检查代码。

设置 VBA 编辑器变量声明选项时，可以自动为每个模块插入`Option Explicit`语句，不需要手动书写。设置方法如下：

设置 Option Explicit: 
> 打开编程窗口 -> 工具栏点击「工具」-> 「选项」-> 「编辑器」tab -> 「代码设置」-> 勾选「要求变量声明」

## 基本类型变量的赋值

基本类型变量是存储单个值的变量，例如数字、文本、日期等。

VBA 中，给基本类型变量赋值，以 `Let`关键词开头。赋值操作是给`=`左侧的变量，用`=`右边的数据，指定其代表的值。在后续的代码中，该变量就代表指定的数据。

> 在实际开发中，给基本类型变量赋值时，`Let`关键词可以忽略不写，直接以变量开头写赋值语句。

给基本类型变量赋值语法如下：
```vba
'语法，两种写法相同
Let [变量名] = [数据]
[变量名] = [数据]

'实例
Dim name As String
Let name = "Zhang San"

Dim age As Integer
Let age = 30

Dim birthday As Date
Let birthday = #2000-1-1#
```
赋值语句中，`=`右侧可以是包含其他变量、函数、复杂计算的表达式。该表达式返回的值的类型，与变量类型一致就可以正常赋值。
```vba
Dim birthday As Date
Dim age As Integer

birthday = #2000-1-1#
age = Year(Now) - Year(birthday)
```
一种特殊情况是，`=`右侧可以是变量本身。这种方式多用于循环结构中。
```vba
Dim i As Integer

Do While i < 10
    
    Msgbox i
	i = i + 1
    
Loop

'返回 => 0,1,2,3,4,5,6,7,8,9
```
## Variant 类型变量的赋值

我们知道 Variant 类型时通用类型，因此赋值很直接，没有类型强制要求。Variant 类型变量第一次赋值后，可以继续赋值其他类型数据。
```vba
'声明变量（两者相同）
Dim message As Variant
Dim message

'赋值
message = "Hello World"
message = 1234567890
message = #2018-12-1#
```
**这里依然强调**，虽然 Variant 类型变量比较灵活，但是也有很多弊端，所以在实际开发中，不建议使用该类型，使用确切类型变量。

## 数组类型变量的赋值
数组是可以存储多个同类型元素的数据类型。声明时一般指定其数据长度。给数组赋值时，一般使用每个元素的序号。

数组赋值基本语法如下：
```vba
[数组名](元素序号) = [数据]
```
下面看一下实际的实例。
```vba
'声明数组
Dim arr(1 to 5) As String
'数组赋值
arr(1) = "Zhang San"
arr(2) = "Li Si"
arr(3) = "Wang Wu"
```

## 对象类型变量的赋值

VBA 中，对象是程序的一个元素，不同于基本类型数据，它包括多个属性和多个方法。例如，Excel 中[工作簿]、[工作表]、[单元格]、[图表]等都是对象。

对象类型变量赋值时，不同于基本类型变量使用`Let`（可以忽略）关键词，对象使用 `Set` 关键词，**并且Set关键词不能省略**。

如下是对象类型变量基本的赋值方法：
```vba
Set [变量名] = [对象类型数据]
```
下面看一下实际的用法。
```vba
'声明工作表类型的对象
Dim sheet As Worksheet
'将名称为“绩效表”的工作表，赋到 sheet 变量
Set sheet = Worksheets("绩效表")
```
由于对象可以包含多个属性，因此 VBA 提供一种同时给多个属性赋值的简单方法。具体方法是对象多个属性赋值语句，放置在 `With`+`对象`和`End With`关键词中间。
```vba
Dim sheet As Worksheet
Set sheet = Worksheets("绩效表")

With sheet
    .Name = "旧绩效"
    .Visible = False
End With
```

## 总结

以上是 VBA 中最基本的变量声明和赋值方法。声明和赋值变量，是代码的开始部分，需要熟练掌握。

不同类型变量，声明和赋值方法做了简单的介绍，除了以上介绍的，不同类型的变量有自己特点。