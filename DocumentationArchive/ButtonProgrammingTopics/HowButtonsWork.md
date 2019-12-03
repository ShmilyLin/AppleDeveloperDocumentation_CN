# `Button`的工作方式

`Button`遵循`Target-Action`设计模式。`Button`是一个用户界面对象，单击该`Button`即可将操作消息发送到目标。有关此设计模式的更多信息，请参见[Objective-C编程中的概念]()中的[Target-Action]()。

`Button`的大部分工作都是由`NSButtonCell`类处理的。如果单击了`NSButtonCell`实例的`View`并获得了`Mouse-Down`事件，则该`NSButtonCell`实例会将其操作消息发送到其目标一次，但是只要将鼠标保持在`Button Cell`内的同时一直按着鼠标，`NSButtonCell`实例也可以连续发送该操作消息。该`Button Cell`可以通过多种方式突出显示来表示已被按下——例如，带边框的`Button Cell`可能会被压入屏幕，或者在按下`Button Cell`时图像或标题可以更改为其他形式。

`NSButtonCell`对象必须与`NSControl`子类的实例一起使用。如果需要一个`Button`（例如`Push Button`），请使用包含单个`NSButtonCell`实例的`NSButton`对象。如果需要一组相关的`Button`，例如一组`开关`或`单选按钮`，请使用包含多个`NSButtonCell`实例的`NSMatrix`对象。

`NSButton`和`NSMatrix`均提供控件视图。虽然`NSMatrix`要求你直接访问`NSButtonCell`对象，但是大多数`NSButton`的方法都是`NSButtonCell`中相同声明的方法的“覆盖”。（换句话说，`NSButton`方法的实现为你自动调用了相应的`NSButtonCell`方法，使你不必考虑`NSButtonCell`对象的存在。）唯一没有被覆盖的`NSButtonCell`方法与用于显示等效键（快捷键）的字体有关的方法，以及用于突出显示或显示`NSButton`状态的特定方法（这些方法通常与`NSButton`的[setButtonType:]()方法一起设置）。