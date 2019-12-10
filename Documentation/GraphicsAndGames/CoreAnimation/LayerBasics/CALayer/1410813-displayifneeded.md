# displayIfNeeded()

如果`Layer`当前被标记为需要更新，则启动该`Layer`的更新过程。

## 定义

```swift
func displayIfNeeded()
```

## 说明

你可以根据需要调用此方法，以在正常更新周期之外强制对`Layer`内容进行更新。但是，通常不需要这样做。更新`Layer`的首选方法是调用[setNeedsDisplay()]()并让系统在下一个循环中更新`Layer`。

