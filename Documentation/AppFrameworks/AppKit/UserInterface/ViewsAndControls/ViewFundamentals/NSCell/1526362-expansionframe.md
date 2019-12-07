# expansionFrame(withFrame:in:)

返回接收器的扩展`Cell`框架。

## 定义

```swift
func expansionFrame(withFrame cellFrame: NSRect, 
                 in view: NSView) -> NSRect
```

## 参数

* **cellFrame**

    接收器的框架。

* **view**

    `View`，将在其中绘制接收器。

## 返回值

接收器的扩展`Cell`框架。如果框架不是太小，请返回一个空的矩形（[NSRect.zero]()），并且不会显示扩展工具提示视图。

## 说明

如果`cellFrame`对于`View`中的整个内容而言太小，则此方法允许`Cell`返回扩展`Cell`框架。当鼠标悬停在某些`Control`上的`Cell`上方时，完整的`Cell`内容将显示在特殊的浮动工具提示视图中。默认情况下，`NSCell`返回`NSRect.zero`，而某些子类（例如`NSTextFieldCell`）将在需要时返回正确的框架。