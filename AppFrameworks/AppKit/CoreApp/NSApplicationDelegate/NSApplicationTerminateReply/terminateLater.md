# NSApplication.TerminateReply.terminateLater

> SDK : macOS 10.0+

---
## 声明

```swift
case terminateLater = 2
```

---
## 说明

稍后可以继续终止。返回此值会导致Cocoa在modalPanel中运行run循环，直到你的app随后使用值`true`或`false`调用[reply(toApplicationShouldTerminate:)]()。delegate的此返回值适用于需要提供文档模式警报（工作表）以决定是否退出的。
