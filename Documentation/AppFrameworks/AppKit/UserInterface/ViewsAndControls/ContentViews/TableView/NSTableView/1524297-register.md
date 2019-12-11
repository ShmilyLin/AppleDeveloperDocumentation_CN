# register(_:forIdentifier:)

为指定的标识符注册`NIB`，以便基于视图的表格视图可以使用它来实例化视图。

## 定义

```swift
func register(_ nib: NSNib?, 
forIdentifier identifier: NSUserInterfaceItemIdentifier)
```

## 参数

* **nib**

    包含视图的`nib`。

* **identifier**

    创建视图用的标识符。

## 说明

使用此方法可以将一个`NIB`的单元格视图与`identifier`相关联，以便该表格可以在被请求时实例化该视图。在调用[makeView(withIdentifier:owner:)]()时使用此方法，并且在设计时没有为指定的标识符创建`NIB`。这允许动态加载可以与表格关联的`NIB`。

由于`NIB`可以包含多个视图，因此可以将同一`NIB`与多个标识符关联。要删除先前与`identifier`相关联的`NIB`，请将`nib`的值设置为`nil`。