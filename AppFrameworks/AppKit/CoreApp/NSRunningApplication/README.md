# NSRunningApplication

一个可以操作并为应用程序的单个实例提供信息的对象。

## 定义

```swift
class NSRunningApplication : NSObject
```

## 概述

应用程序的某些属性是固定的，例如捆绑包标识符。其他属性可能会随时间而变化，例如应用程序是否被隐藏。可以通过键值观察来观察变化的属性，在这种情况下，该方法的描述注释将说明此功能。

随时间变化的属性本质上是易于变化的。例如，隐藏的应用可以随时取消隐藏。为了改善这一点，属性会一直保持到共模下主运行循环的下一轮。例如，如果你重复轮询未隐藏的应用程序的隐藏属性而不允许运行循环运行，则即使该应用程序隐藏了，它也将继续返回false，直到下一轮运行循环为止。

`NSRunningApplication`是线程安全的，因为它的属性是原子性返回的。但是，它仍然受上述主运行循环策略的约束。如果从后台线程访问`NSRunningApplication`的实例，请注意，随着主运行循环的运行（或不运行），其时变属性可能会随之而改变。

应用退出后，`NSRunningApplication`实例仍然有效。但是，大多数属性失去了其意义，并且某些属性可能在终止的应用程序上不可用。

要访问所有正在运行的应用程序的列表，请使用[NSWorkspace]()中的[runningApplications]()方法。

## 主题

### 获取正在运行的应用程序实例

* [init?(processIdentifier: pid_t)]()

    返回具有给定进程标识符的正在运行的应用程序；如果没有应用程序具有该`pid`，则返回`nil`。

* [class func runningApplications(withBundleIdentifier: String) -> [NSRunningApplication]]()

    返回具有指定包标识符的当前正在运行的应用程序的数组。

* [class var current: NSRunningApplication]()

    返回表示此应用程序的`NSRunningApplication`。

### 激活应用程序

* [var isActive: Bool]()

    指示应用程序当前是否在最前面。

* [func activate(options: NSApplication.ActivationOptions) -> Bool]()

    尝试使用指定的选项激活应用程序。

* [struct NSApplication.ActivationOptions]()

    用于[activate(options:)]()的标识。

* [var activationPolicy: NSApplication.ActivationPolicy]()

    指示应用程序的激活策略。

* [enum NSApplication.ActivationPolicy]()

    激活策略（由[activationPolicy]()使用），用于控制是否以及如何激活应用程序。

### 隐藏和取消隐藏应用程序

* [func hide() -> Bool]()

    尝试隐藏应用程序。

* [func unhide() -> Bool]()

    尝试取消隐藏应用程序。

* [var isHidden: Bool]()

    指示该应用程序当前是否处于隐藏状态。

### 应用程序的信息

* [var localizedName: String?]()

    指示应用程序的本地化名称。

* [var icon: NSImage?]()

    返回接收者的应用程序的图标。

* [var bundleIdentifier: String?]()

    指示应用程序的`CFBundleIdentifier`。

* [var bundleURL: URL?]()

    指示应用程序bundle的URL。

* [var executableArchitecture: Int]()

    指示应用程序的执行处理器体系结构。

* [var executableURL: URL?]()

    指示应用程序可执行文件的URL。

* [var launchDate: Date?]()

    指示启动应用程序的日期。

* [var isFinishedLaunching: Bool]()

    指示接收方的进程是否已完成启动。

* [var processIdentifier: pid_t]()

    指示应用程序的进程标识符（`pid`）。

* [var ownsMenuBar: Bool]()

    返回应用程序是否拥有当前菜单栏。

### 终止应用程序

* [func forceTerminate() -> Bool]()

    尝试强制退出接收器。

* [func terminate() -> Bool]()

    尝试正常退出接收器。

* [var isTerminated: Bool]()

    表示接收器的应用程序已终止。

* [class func terminateAutomaticallyTerminableApplications()]()

    终止后台运行的应用程序，就像由系统内存压力触发一样。