# setNeedsDisplay()

将`Layer`的内容标记为需要更新。

## 定义

```swift
func setNeedsDisplay()
```

## 说明

调用此方法将导致`Layer`重新缓存其内容。这导致该`Layer`可能调用其`Delegate`的[display(_:)]()或[draw(_:in:)]方法。`Layer`的[contents]()属性中的现有内容将被删除，以便为新内容腾出空间。