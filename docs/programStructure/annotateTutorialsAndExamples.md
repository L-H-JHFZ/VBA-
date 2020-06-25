# VBA 注释教程和实例

VBA 中，注释是对程序作出的说明。VBA 代码运行时，会跳过注释语句，因此注释不影响代码的运行。

* [如何写注释](#如何写注释)
* [注释的用途](#注释的用途)
* [总结](#总结)

## 如何写注释

VBA 中的注释语句是，以英文单引号 `(')`开头，后接需要解释说明的内容。基本语法如下：
```vba
'注释的内容
```
我们看实际的例子。

注释可以写在一行，单引号后的内容均是注释的内容。
```vba
Sub MyCode()

    '定义姓名变量
    Dim name As String

End Sub
```
注释也可以在一行代码的结尾，同样，单引号后的内容均是注释的内容。
```vba
Sub MyCode()

    '定义姓名变量
    Dim name As String
    
    name = Range("A1").Value '从A1单元格读取姓名

End Sub
```
注释内容是多行内容，需要在每一行开头使用单引号。
```vba
'此过程用于读取 A1 单元格的值
'最后更新于 2020-5-13

Sub MyCode()

    '定义姓名变量
    Dim name As String
    
    name = Range("A1").Value '从A1单元格读取姓名

End Sub
```

## 注释的用途

最基本的用途当然是对代码标注说明，例如：

* 提供过程或函数的基本信息、用途；
* 说明变量的用途；
* 解释为什么使用当前的方法；
* 区分开不同代码块

注释另一个常见的用法是，在开发调试过程中，临时注释一段代码，使其不被执行，检查代码其余部分是否有错误。

## 总结

注释是程序编写中最基础也是最重要的一部分。

建议大家养成写注释的习惯。因为实际开发过程中，程序中会有很多变量、语句，如果稍不注意就会搞混代码，需要从头开始对，浪费时间。更不用说过一段时间再查看代码，或者代码给其他人看。
