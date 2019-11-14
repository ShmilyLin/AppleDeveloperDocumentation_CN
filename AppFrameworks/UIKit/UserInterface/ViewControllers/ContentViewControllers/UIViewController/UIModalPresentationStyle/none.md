# UIModalPresentationStyle.none

一种呈现样式，表示不应进行任何修改。

## 定义

```swift
case none = -1
```

## 说明

不要使用此样式来呈现View Controller。相反，当你不希望被呈现的Controller适应已经呈现的View Controller的样式时，可以从自适应（adaptive）委托的[adaptivePresentationStyle(for:)]()方法返回它。