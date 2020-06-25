# Excel VBA 中的一些基本概念

## Excel VBA 基本原理

说到 Excel VBA 的基本原理，自然的出现两种基本概念，一是 VBA 语法层面，一是 Excel 层面。Excel 是一个对象，这个对象包含很多属性和子对象，而 VBA 是可以操作这些对象的工具，实现各种各样的效果。例如，Excel 包括 Range 对象，即单元格对象，使用 VBA 可以改变单元格对象的填充颜色属性。用代码表示如下。

```vba
'A1 单元格的填充颜色设置为颜色号为 49407 的颜色
Range("A1").Interior.Color = 49407
```

* Range(“A1”)、Interior、Color 等是 Excel 具备的对象和属性；
* 对象和属性的操作，是通过 VBA 语言实现的，即上面是一行 VBA 代码。中间的等号(=)是 VBA 语言的赋值符号，也是能改变单元格填充颜色的关键所在。

## VBA 语言中基本概念
### 注释
注释是代码中不会被执行的一段代码。注释是几乎所有编程语言具备的功能，VBA 也不例外。

VBA 中的注释以英文单引号 (‘) 开头，后面接注释的内容。从单引号开始的部分不会被执行。

```vba
'我是一行注释
```
注释，正如字面意思，用来对代码进行解释。在写代码过程中，对代码进行注释是好的习惯，有助于自己或别人，更好的理解已经存在的一段代码。


### 变量
变量是存储数据的一种表达方式。在程序开始，可以声明一个变量，指定变量的类型（数字、文本、逻辑值等），并给变量赋值。在程序其他地方，就可以用该变量，使其存储的值参与运算。

以下方代码为例，
```vba
'声明一个文本类型的变量
Dim val As String
'给 val 变量赋值，即 "Hello World"
val = "Hello World"
'在 A1 单元格写入 val 变量存储的数据
Range("A1").Value = val
```
可以看到，val 变量存储 “Hello World”文本，该文本在程序中就可以用 val 变量表示。这部分内容在下一章「变量、类型和运算符」中详细介绍。

### 程序结构
程序结构表示程序的运行方式。VBA 正是因为存在多种代码结构，才能实现各类复杂的数据计算。常用的代码结构以下三种：

* 顺序结构
* 条件结构
* 循环结构

**顺序结构**，顾名思义，程序按照顺序执行。在 VBA 中就是从上到下，一行一行地执行。

**条件结构**，代码中的指定部分，按照某个条件，选择性地执行。即，条件为真时，执行指定代码；否则跳过该部分代码，不执行。

**循环结构**，代码中的指定部分，按指定次数，循环执行。这是为什么 VBA 的效率高的一个原因，因为它能将相同的操作，自动按任意数量重复执行。

关于程序结构的内容，在「程序结构」一章中详细介绍。

### 过程和函数
过程或函数包含多行代码，是组织代码的两种方式。一般情况下，一个过程或函数只包含实现一个功能的相关代码。如果一个过程或函数实现多个功能，建议将代码分成多个过程或函数。

过程和函数都可以执行一段代码，主要区别是，执行完代码后，函数能返回一个值，而过程不能返回。更多内容将在「过程和函数」章节介绍。

### 数组
数组表示一组同类型的数据的集合，是 VBA 中最重要的概念之一。以下面的代码为例：
```vba
'创建数组
Dim Val(1 to 4) As String
'给数组的元素赋值
Val(1) = "Excel"
Val(2) = "Word"
Val(3) = "PowerPoint"
Val(4) = "Outlook"
```
上述代码创建了一个长度为4个、类型为文本的一个数组。对数组，使用编号给相应位置进行赋值。

在 VBA 的实际应用中，经常需要将单元格的数据转换为数组进行处理。更多内容在「数组」章节介绍。

### 对象
对象是一个物，它可以是一个事、一个物体、一个概念、一个名词。对象包含描述静态信息的属性和对对象可以操作的方法。

以生活中的对象为例子，汽车是一个对象。汽车的车牌号、油量、里程等是汽车的属性；开车、加油、换车牌等是汽车的方法。

在 VBA 中也是类似。工作表(Worksheet)是一个对象，它具有名称、标签颜色等属性，有添加、删除等方法。Excel VBA 中对象将在「Excel VBA 对象模型」一章中详细介绍。

## Excel VBA 中的基本概念

在上面对象一段中，说到了工作表(Worksheet)对象。其实 Excel 本身是就是一个对象，是 Excel 中的最大的对象，使用 Application 表示。Application 对象又包含工作簿(Workbook)对象，工作簿(Workbook)对象又包含工作表(Worksheet)对象，而工作表(Worksheet)对象又包含其他的子对象。

上面一段基本描述了 Excel VBA 对象模型，即是一种树状结构，多个对象通过有逻辑的层次结构组织在一起。

### 常用 Excel 对象
* Application 对象，表示 Excel 应用程序。
* Workbook 对象，表示工作簿对象。
* Worksheet 对象，表示工作表对象
* Range 对象，表示单元格区域对象。
### 模块
模块是包含一个或多个过程或函数的内部组件。一个工作簿内包含的模块数量没有限制，一个模块内包含的过程或函数数量也没有限制。模块用来作为保存过程或函数的容器，这些过程和函数通常应用于整个工作簿。

通过把多个过程和函数，合理的放置在不同的模块，可以使整个 VBA 代码逻辑更清晰、更易于阅读和理解。

### 用户窗体
用户窗体是 VBA 代码与使用者交互的用户界面。Excel VBA 提供很多基本的窗体控件，可以制作复杂的用户界面。最典型的，Excel 中设置单元格格式的窗口界面，就是一个用户窗体。

最基本的窗体控件包括：

* 文本控件
* 按钮控件
* 列表控件
* 输入控件

## 其他基本概念

### VBA 编辑器
VBA 编辑器正 Excel 中写 VBA 代码的地方。编辑器中可以进行下列操作：

* 编写代码
* 修改已有的代码
* 插入新的模块，编辑模块中的代码
* 插入用户窗体，设计窗体界面
* 运行代码
* 调试代码