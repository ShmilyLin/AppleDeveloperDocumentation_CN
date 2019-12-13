# gridStyleMask

`表格视图`绘制的网格线。

## 定义

```swift
var gridStyleMask: NSTableView.GridLineStyle { get set }
```

## 说明

使用此属性可以指定是否应在行和列之间绘制线条。设置此属性时，可以通过将相应的常数加在一起来一次指定多种样式。此属性的默认值为[gridNone]()。