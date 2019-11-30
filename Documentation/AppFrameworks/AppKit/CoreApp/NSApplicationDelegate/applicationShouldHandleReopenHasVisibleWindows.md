# applicationShouldHandleReopen(_:hasVisibleWindows:)

在默认行为之前由App发送给delegate以重新打开（rapp）AppleEvents。

> SDK : macOS 10.0+

---
## 声明

```swift
optional func applicationShouldHandleReopen(_ sender: NSApplication, 
                              hasVisibleWindows flag: Bool) -> Bool
```

---
## 参数

* **theApplication**

  App对象

* **flag**

  表示[NSApplication]()对象是否在应用程序中找到任何可见窗口。如果你返回`true`，则可以使用此值作为应用程序是否执行任何操作的指示。

---
## 返回值

如果希望应用程序执行其正常任务，则为`true`，如果你希望应用程序不执行任何操作，则为`false`。

---
## 说明

因为有人再次双击App或使用Dock激活App，就会使Finder重新激活已在运行的App，就会发送该事件，。

默认情况下，Application Kit将通过检查是否有任何可见的[NSWindow]()（而不是[NSPanel]()）对象来处理此事件，如果没有，则会通过标准的无标题文档创建（与在没有任何App的情况下启动App时相同）要打开的文件。对于大多数基于文档的App，将创建无标题文档。

App的delegate还将有机会响应正常的无标题文档的delegate方法。如果在App的delegate中实现此方法，则会在发生任何默认行为之前调用它。如果返回`true`，则[NSApplication]()将正常进行。如果返回`false`，则[NSApplication]()将不执行任何操作。因此，你可以使用不执行任何操作的版本实现此方法，如果你根本不希望发生任何事情，则返回`false`（不推荐），或者你可以实现此方法，以某种自定义方式自行处理事件并且返回`false`。

通过此方法认为Dock中的窗口和最小化窗口都是可见的，并且会使得`flag`返回`true`，尽管最小化窗口在发送[isVisible]()消息时返回`false`。

---
## 其他内容

### 管理窗口

#### ● [func applicationWillUpdate(Notification)](./applicationWillUpdate.md)

在App对象更新其窗口之前，由默认通知中心（default notification center）发送。

#### ● [func applicationDidUpdate(Notification)](./applicationDidUpdate.md)

在App对象更新其窗口之后，由默认通知中心（default notification center）发送。


