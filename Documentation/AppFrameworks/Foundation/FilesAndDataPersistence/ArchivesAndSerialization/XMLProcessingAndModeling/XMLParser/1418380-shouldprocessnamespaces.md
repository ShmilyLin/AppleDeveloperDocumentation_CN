# shouldProcessNamespaces

一个布尔值，它确定解析器是否报告元素的名称空间和合格名称。

## 定义

```swift
var shouldProcessNamespaces: Bool { get set }
```

## 说明

如果解析器报告名称空间和合格名称，则为`true`，否则为`false`。

解析器通过代理方法[parser(_:didStartElement:namespaceURI:qualifiedName:attributes:)]()和[parser(_:didEndElement:namespaceURI:qualifiedName:)]()来报告元素名称。