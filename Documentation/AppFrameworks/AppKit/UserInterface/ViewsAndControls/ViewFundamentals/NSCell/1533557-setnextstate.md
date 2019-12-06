# setNextState()

将`Cell`的状态更改为序列中的下一个值。

## 定义

```swift
func setNextState()
```

## 说明

如果一个`Cell`具有三个状态，则将按以下顺序循环：打开，关闭，混合，打开，关闭等等。如果`Cell`只有两个状态，它将在它们之间切换。