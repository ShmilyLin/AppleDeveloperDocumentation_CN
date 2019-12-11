# registeredNibsByIdentifier

获取基于视图的表格视图的所有已注册的标识符对应的`nib`文件的字典。

## 定义

```swift
var registeredNibsByIdentifier: [NSUserInterfaceItemIdentifier : NSNib]? { get }
```

## 说明

字典中的每个键都是标识符字符串（由[NSUserInterfaceItemIdentifier]()提供），用于将`nib`文件注册到[register(_:forIdentifier:)]()方法中。每个键的值是相应的[NSNib]()对象。

> **注意**
>
> 这个方法只在基于`NSView`的表格视图中有效。