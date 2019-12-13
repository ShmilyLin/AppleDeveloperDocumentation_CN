# rowSizeStyle

`表格视图`使用的`行`的大小样式（小，中，大或自定义）。

## 定义

```swift
var rowSizeStyle: NSTableView.RowSizeStyle { get set }
```

## 说明

要逐行设置行大小样式，请将此属性的值设置为[NSTableView.RowSizeStyle.custom]()并在`表格视图`委托对象中实现[tableView(_:heightOfRow:)]()方法。

此属性的默认值为[NSTableView.RowSizeStyle.custom]()，它告诉表格使用表格的[rowHeight]()而不是任何预定的系统值。通常，`rowSizeStyle`应该始终为[NSTableView.RowSizeStyle.custom]()，“源列表”除外。