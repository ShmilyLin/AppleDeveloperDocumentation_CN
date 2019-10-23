# shouldReportNamespacePrefixes

一个布尔值，它确定解析器是否报告表示名称空间声明范围的前缀。

## 定义

```swift
var shouldReportNamespacePrefixes: Bool { get set }
```

## 说明

如果解析器报告名称空间声明的范围，则为`true`，否则为`false`。 默认值为`false`。

解析器通过代理方法[parser(_:didStartMappingPrefix:toURI:)]()和[parser(_:didEndMappingPrefix:)]()来报告词首。