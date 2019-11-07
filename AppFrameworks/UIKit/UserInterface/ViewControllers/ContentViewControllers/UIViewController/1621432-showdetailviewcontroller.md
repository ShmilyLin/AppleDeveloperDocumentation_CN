# showDetailViewController(_:sender:)

在辅助（或详细信息）上下文中显示View Controller。

## 定义

```swift
func showDetailViewController(_ vc: UIViewController, 
                            sender: Any?)
```

## 参数

* **vc**
    
    当前的View Controller。

* **sender**

    作用的对象。

## 说明

使用此方法可以将显示View Controller的需求与实际在屏幕上呈现该View Controller的过程脱钩。使用此方法，View Controller不需要知道它是嵌入在Navigation Controller还是Split-View controller中。两者调用相同的方法。在常规（Regular）环境中，[UISplitViewController]()类将覆盖此方法，并将`vc`安装为其Detail View Controller；在紧凑（Compact）的环境中，Split-View controller对此方法的实现将调用[show(_:sender:)](./1621377-show.md)。

此方法的默认实现调用[targetViewController(forAction:sender:)]()方法在覆盖此方法的View Controller层次结构中找到一个对象。然后，它在该目标对象上调用方法，以适当的方式显示View Controller。如果`targetViewController(forAction:sender:)`方法返回`nil`，则此方法使用窗口的Root View Controller以模态显示`vc`。

你可以在自定义View Controller中覆盖此方法以自己显示`vc`。使用此方法可在主要上下文中显示`vc`。例如，Container View Controller可能使用此方法替换其辅助子级。你的实现应针对常规（Regular）和紧凑（Compact）环境调整其行为。