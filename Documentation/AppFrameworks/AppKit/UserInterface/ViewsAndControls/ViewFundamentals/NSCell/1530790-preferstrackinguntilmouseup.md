# prefersTrackingUntilMouseUp

返回一个布尔值，该值指示当光标离开`Cell`时跟踪是否停止。

## 定义

```swift
class var prefersTrackingUntilMouseUp: Bool { get }
```

## 返回值

如果在光标离开`Cell`时停止跟踪，则为`true`，否则为`false`。

## 说明

默认实现返回`false`。子类可以重写此方法以返回不同的值。