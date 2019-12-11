# usesStaticContents

一个布尔值，指示表格是否使用静态数据。

## 定义

```swift
var usesStaticContents: Bool { get set }
```

## 说明

静态表格不依赖数据源来提供行数。静态表格视图的内容是在设计时设置的，可以根据需要通过编程方式进行更改。通常，在设置静态表格视图后，你不会更改它们的内容。

在Xcode中，添加到静态表格中的所有行均保存在相应的`nib`或`Storyboard`文件中，并在运行时与表格的其余部分一起加载。你可以使用[insertRows(at:withAnimation:)]()方法以编程方式将表格行添加到静态表格视图中。以编程方式添加行时，表格视图的委托必须实现[tableView(_:viewFor:row:)]()方法以为任何新行提供相应的视图。你还可以随时使用[removeRows(at:withAnimation:)]()方法删除行。

> **注意**
> 
> 只有基于`NSView`的表格视图才可以使用静态数据。