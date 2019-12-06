# sizeToFit()

调整接收器框架的大小，使其成为容纳其`Cell`所需的最小尺寸。

## 定义

```swift
func sizeToFit()
```

## 说明

如果要让`NSControl`的多`Cell`自定义子类调整自身大小以适合其`Cell`，则必须重写此方法。此方法既不会重新显示接收器，也不会将其标记为需要显示。你必须自己使用[display()]()或[setNeedsDisplay()]()方法来执行此操作。

