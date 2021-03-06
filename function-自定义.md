# Lambda
简单的、匿名的函数。

以“:”操作符定义，之前的是参数、之后的事返回值。

感谢柯里化也可以定义多参数Lambda，需要做的就是返回另一个Lambda（x: y: x + y）。

	id = x: x
	const = x: y: x
	myLambda = x: y: z: (x + y) * z

简单Lambda通常用“_”成语（idiom）缩得更短，即在柯里化一节头一次看到的那样。

所有带括号的表达式内“_”的地方（occurrence）被连续的Lambda参数代替。

这可以简化某些构造：

	_.succ # 同(x: x.succ)
	_.toText + _.toText # 同(x: y: x.toText + y.toText)

注意每组括号创建一个新的Lambda上下文，因此“(_ + 2) + _”被解释为“x: (y: y + 2) + x”，而不是“x: y: (x + 2) + y”。

# 模块视图
截至目前，大家总是关心给定函数的内部，一个模块有包含所有函数的视图。

需要它来构建更复杂的逻辑片段。

访问该视图，简单地双击工作空间背景（空白）或在可视化编辑器的左上角选择breadcrumb控件。

该视图下，可以看到一个文件中定义的全部函数，以节点显示如下：

![][0]

双击节点进入任意函数。

若存在名为main的函数，打开文件时可视化编辑器将自动进入该函数。

# 函数定义
定义包级或复杂函数最好用def关键字来完成。

包级任何用这种方式定义的函数对别的包可见、可被别的包引入（当然是通过定义该函数的包本身）。

在可视化编辑器定义名为foo的函数，只需要在探测器中键入“def foo”然后敲击<kbd>Enter</kbd>键。

这回创建一个空函数，可以输入并完成逻辑定义。

参数是左侧工具条的端口，返回至连接在右端。

![][1]

还有一种方法在已存在的逻辑片段之外定义函数，选择任意数量的节点、敲击<kbd>f</kbd>键。

节点会折叠进一个函数，任何外部输入连接成为参数，任何外部输出连接成为该函数的返回值。

这个工作流在“原型解决方案”和“以不同方式解决给定问题（头脑风暴）”时很方便。

![][2]

把选定的节点折叠起来：

![][3]

新创建的“func1”函数在内部看起来如下：

![][4]

---
[0]:./images/module-view-toplevel.png
[1]:./images/function-define.png
[2]:./images/before-collapse.png
[3]:./images/after-collapse.png
[4]:./images/collapsed-inside.png