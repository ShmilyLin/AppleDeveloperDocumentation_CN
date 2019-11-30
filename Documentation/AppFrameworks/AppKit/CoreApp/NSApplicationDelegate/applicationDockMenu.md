# applicationDockMenu(_:)

允许delegate动态地为App提供程序坞菜单。

> SDK : macOS 10.1+

---
## 声明

```swift
optional func applicationDockMenu(_ sender: NSApplication) -> NSMenu?
```

---
## 参数

* **sender**

  与delegate关联的App对象。

---
## 返回值

在程序坞（Dock）中显示的菜单。

---
## 说明

你还可以将`Interface Builder`中的菜单连接到`dockMenu`接口中。App指定程序坞（Dock）菜单的第三种方法是在`nib`中提供[NSMenu]()。

如果此方法返回菜单，则此菜单优先于`nib`中的`dockMenu`。

每个菜单项的目标和操作都将传递到程序坞（Dock）中。在选择菜单项时，程序坞（Dock）会向你的App发送消息，该App应调用`[NSApp sendAction:selector to:target from:nil]`。

要在`nib`中指定[NSMenu]()，请使用密钥`AppleDockMenu`将`nib`名称添加到`info.plist`，指定的`nib`名称不需要填写后缀名。然后，你可以从文件的所有者对象（默认情况下为[NSApplication]()）创建到菜单的连接。将菜单连接到[NSApplication]()的`dockMenu`接口中。菜单位于自己的`nib`文件中，因此可以在请求`dockMenu`时延迟加载，而不是在启动时加载。
