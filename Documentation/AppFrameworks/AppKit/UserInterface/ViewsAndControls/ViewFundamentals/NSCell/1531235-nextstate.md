# nextState

`Cell`的下一个状态。

## 定义

```swift
var nextState: Int { get }
```

## 说明

如果一个`Cell`具有三个状态，则将按以下顺序循环：打开，关闭，混合，打开，关闭等等。如果`Cell`只有两个状态，它将在它们之间切换。

有关代表可能的`Cell`状态的常量列表，请参见[NSCell.StateValue](./StateValue/)。