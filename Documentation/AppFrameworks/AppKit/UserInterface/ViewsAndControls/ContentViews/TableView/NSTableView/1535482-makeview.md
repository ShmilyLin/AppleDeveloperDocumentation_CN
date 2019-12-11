# makeView(withIdentifier:owner:)

返回具有指定标识符的新视图或现有视图。

## 定义

```swift
func makeView(withIdentifier identifier: NSUserInterfaceItemIdentifier, 
        owner: Any?) -> NSView?
```

## 参数

* **identifier**

    视图标识符。不能为`nil`。

* **owner**

    `NIB`的所有者可以被加载和实例化以创建具有指定标识符的新视图。

## 返回值

一个行视图

## 说明

通常，`identifier`与表格的[Nib文件]()中包含的单元格视图相关联。调用此方法后，表格视图会自动实例化具有指定所有者的单元格视图，该所有者通常是表格视图的委托。 （所有者在从视图中设置出口和`Target/Action`时很有用。）请注意，单元格视图的标识符必须与其表格列的标识符相同，绑定才能起作用。如果使用绑定，建议你使用`Interface Builder`中的“自动标识符”设置。

此方法还可能返回具有相同`identifier`的重用视图，该标识符在屏幕上不再可用。如果无法从`nib`文件实例化或在重用队列中找不到具有指定标识符的视图，则此方法返回`nil`。

该方法通常由委托[tableView(_:viewFor:row:)]()中调用，但也可以重写以提供`identifier`的自定义视图。请注意，每次调用此方法时都会调用[awakeFromNib()]()，这意味着即使所有者已经醒着，也将在所有者上调用`awakeFromNib`。