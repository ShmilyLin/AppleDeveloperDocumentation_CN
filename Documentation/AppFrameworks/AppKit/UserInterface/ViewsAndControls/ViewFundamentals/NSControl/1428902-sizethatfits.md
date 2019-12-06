# sizeThatFits(_:)

要求`Control`计算并返回最适合指定尺寸的大小。

## 定义

```swift
func sizeThatFits(_ size: NSSize) -> NSSize
```

## 参数

* **size**

    `Control`应为其计算最合适尺寸的大小。

## 返回值

适合接收者`子视图`的新尺寸。

## 说明

默认情况下，此方法返回接收者的[intrinsicContentSize]()。