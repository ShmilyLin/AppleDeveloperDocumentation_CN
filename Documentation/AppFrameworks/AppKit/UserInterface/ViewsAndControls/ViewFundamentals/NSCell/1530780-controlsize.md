# controlSize

`Cell`的大小

## 定义

```swift
var controlSize: NSControl.ControlSize { get set }
```

## 说明

使用此属性可以更改`Cell`及其`Control`的渲染大小。有关可能的值的列表，请参见[NSControl.ControlSize]()。

更改`Cell`的`Control`大小不会更改该`Cell`使用的字体。使用[NSFont]()的[systemFontSize(for:)]()类方法可基于新的`Control`大小获取适当的字体。