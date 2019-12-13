# setIndicatorImage(_:in:)

设置指定`列`的指示符图像。

## 定义

```swift
func setIndicatorImage(_ image: NSImage?, 
                    in tableColumn: NSTableColumn)
```

## 参数

* **anImage**

    `列`的指示符图像。

* **aTableColumn**

    表格的`列`。

## 说明

默认的排序顺序指示符可作为命名的`NSImage`对象使用。 使用`[NSImage imageNamed:]`通过`@"NSAscendingSortIndicator"`（“`^`”图标）和`@"NSDescendingSortIndicator"`（“`v`”图标）访问这些图像。

