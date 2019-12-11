# rowHeight

表格中每一行的高度。

## 定义

```swift
var rowHeight: CGFloat { get set }
```

## 说明

默认行高是`16.0`。仅当表格的[rowSizeStyle]()设置为[NSTableView.RowSizeStyle.custom]()时，才使用此属性中的值。

更改此属性的值时，`表格视图`将调用[tile()]()方法以使用新值重新显示行。