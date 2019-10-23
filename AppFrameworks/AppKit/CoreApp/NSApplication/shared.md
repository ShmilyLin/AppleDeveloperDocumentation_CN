# shared

返回App实例，如果它尚不存在则创建它。

---

## 声明

```swift
class var shared: NSApplication { get }
```

---
## 返回值

　　共享的App对象。

## 说明

　　此方法还连接到窗口服务并完成其他初始化。你的程序应该将此方法作为`main()`中的第一个语句之一调用，如果你使用Xcode创建App，则会为你完成此代码编写。要在创建`NSApplication`实例后获取它，请使用全局变量[NSApp]()或调用此方法。

---
## 其他内容

### 获得共享App对象

#### ● [var NSApp: NSApplication!](./NSApp.md)

　　共享App实例的全局变量。


### 相关文档

#### ● [Mac App Programming Guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010543)

#### ● [func run()]()

　　开始主事件循环。

#### ● [func terminate(Any?)]()

　　终止接收器。