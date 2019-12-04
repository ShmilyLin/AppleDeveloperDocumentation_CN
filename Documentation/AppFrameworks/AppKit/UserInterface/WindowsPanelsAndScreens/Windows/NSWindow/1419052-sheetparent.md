# sheetParent

`Sheet`连接到的`窗口`。

## 定义

```swift
var sheetParent: NSWindow? { get }
```

## 说明

如果接收者不是`Sheet`或没有`Sheet`父项，则此属性的值为`nil`。

此属性中的`窗口`对象指的是逻辑上连接了`Sheet`的`窗口`，与外观无关。`父窗口`与`Sheet`之间的关系从`Sheet`的开头（例如，通过[beginSheet(_:completionHandler:)](./1419653-beginsheet.md)）开始，到`Sheet`被销毁（例如，通过[endSheet(_:)](./1419318-endsheet.md)）结束。