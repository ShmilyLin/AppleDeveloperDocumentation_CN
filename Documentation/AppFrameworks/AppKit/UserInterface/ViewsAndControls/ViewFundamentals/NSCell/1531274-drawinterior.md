# drawInterior(withFrame:in:)

绘制接收器的内部，其中包括图像或文本部分，但不包括边框。

## 定义

```swift
func drawInterior(withFrame cellFrame: NSRect, 
               in controlView: NSView)
```

## 参数

* **cellFrame**

    接收者的边界矩形，或者边界矩形的一部分。

* **controlView**

    管理`Cell`的`Control`对象。

## 说明

文本类型的`NSCell`对象使用一个全局[NSText]()对象，将其内容显示在从`cellFrame`略有偏移的矩形中。图像类型`NSCell`对象将其内容显示在`cellFrame`中。如果设置了适当的属性，则此方法还会显示虚线矩形以指示`Control`是否是第一响应者，并突出显示该`Cell`。从`NSControl`的[drawCellInside(_:)]()方法调用此方法，以在`Cell`内容更改时直观地更新`Cell`显示的内容。 `NSCell`实现完成的绘图极少，并且在诸如`NSButtonCell`和`NSSliderCell`之类的对象中变得更加复杂。

此方法在当前聚焦的`View`中绘制`Cell`，该`Cell`可以与传入的`controlView`不同。建议不要利用它。

子类通常重写此方法以提供更复杂的`Cell`内容绘制。因为[draw(withFrame:in:)]()在绘制`Cell`的边框后会调用[drawInterior(withFrame:in:)]()，所以请不要在你的重写实现中调用[draw(withFrame:in:)]()。
