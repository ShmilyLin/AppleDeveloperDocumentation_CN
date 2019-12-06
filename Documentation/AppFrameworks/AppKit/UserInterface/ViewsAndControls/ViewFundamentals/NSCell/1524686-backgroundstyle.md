# backgroundStyle

`Cell`的背景样式。

## 定义

```swift
var backgroundStyle: NSView.BackgroundStyle { get set }
```

## 说明

背景描述了在[draw(withFrame:in:)]()方法中绘制`Cell`的表面。`Control`通常在要求`Cell`绘制之前设置此属性的值。`Cell`可能会基于背景特征进行不同绘制。例如，`Table View`在选定行中绘制`Cell`可能会将值设置为[`Dark`]。`Text Cell`可能因此决定将其文本呈现为白色。`评级样式的级别指示器`可能会将其星星绘制为白色而不是灰色。
