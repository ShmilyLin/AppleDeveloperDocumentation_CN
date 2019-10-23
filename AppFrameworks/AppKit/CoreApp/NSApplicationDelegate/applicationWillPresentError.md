# application(_:willPresentError:)

在指定的App向用户显示错误消息之前发送给delegate。

> SDK : macOS 10.4+

---
## 声明

```swift
optional func application(_ application: NSApplication, 
                 willPresentError error: Error) -> Error
```

---
## 参数

* **application**

  与delegate关联的App对象。

* **error**

  用于构造错误消息的错误对象。你对此方法的实现可以返回一个新的[NSError]()对象或此参数中的相同对象。

---
##  返回值

要显示的错误对象。

---
## 说明

你可以实现此delegate方法来自定义App提供的任何错误的表示，只要App中的代码不会覆盖任何一种防止错误从响应者链传递到App对象的[NSResponder]()方法：`presentError:modalForWindow:delegate:didPresentSelector:contextInfo:`或`presentError:`。

你对此delegate方法的实现可以检查错误，如果其本地化描述或恢复信息不符合你的要求，则可以返回具有你指定的本地化文本的错误对象，该文本更适合在警报表和对话框中显示。如果这样做，请始终使用[NSError]()对象的`domain`和`error code`来区分要自定义的表示方式和非自定义的表示方式的错误。不要根据本地化描述、恢复建议或恢复选项做出决策，因为解析本地化文本是有问题的。如果你决定不自定义错误显示文本，只需返回传入的参数中的`error`对象。
