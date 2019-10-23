# NSWindow.OcclusionState

指定窗口遮挡状态。

## 定义

```swift
struct OcclusionState
```

## 主题

### 常量

* [static var visible: NSWindow.OcclusionState]()

    如果设置，则至少部分窗口可见。如果未设置，则整个窗口都被遮挡。具有非矩形形状的窗口可以在屏幕上完全闭塞，但是如果其边界框落入可见区域，则该窗口被视为可见。注意，完全透明的窗口也可能被视为可见。

### 初始化

* [init(rawValue: UInt)]()