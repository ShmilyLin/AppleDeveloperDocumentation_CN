# shouldResolveExternalEntities

一个布尔值，它确定解析器是否报告外部实体的声明。

## 定义

```swift
var shouldResolveExternalEntities: Bool { get set }
```

## 说明

如果解析器报告外部实体的声明，则为`true`，否则为`false`。 默认值为`false`。如果将此属性设置为`true`，则可能导致其他基于网络或基于磁盘的I/O操作加载外部DTD。

解析器通过代理方法[parser(_:foundExternalEntityDeclarationWithName:publicID:systemID:)]()来报告外部实体的声明。