# interiorBackgroundStyle

`Cell`的内部背景样式。

## 定义

```swift
var interiorBackgroundStyle: NSView.BackgroundStyle { get }
```

## 说明

内部背景样式描述在[drawInterior(withFrame:in:)]()方法中绘制到的表面。这通常与[backgroundStyle](./1524686-backgroundstyle.md)相同，但是绘制边框的`Button`将为此属性使用不同的值。

在带有自定义边框的自定义`Button`中，你可以覆盖此属性并返回不同的值来描述该表面。具有自定义内部图形的`Cell`可以使用此属性的值来选择在`Cell`上看起来不错的图像。