# NSButton

定义屏幕上可用于触发动作的区域的控件。

## 定义

```swift
class NSButton : NSControl
```

## 概述

`按钮`是用于在你的App内启动操作的标准控件。你可以将`按钮`配置为多种不同的视觉样式，但是它们行为是相同的。单击后，`按钮`将调用其关联目标对象的操作方法。（如果将`按钮`配置为连续按钮，它将在一定时间间隔内调用其操作方法，直到用户释放鼠标或光标离开`按钮`边界为止。）你可以使用操作方法来执行特定于App的任务。

`按钮`有多种类型，每种`按钮`具有不同的用户界面和行为。`按钮`类型在[NSButtonCell]()类中定义，并通过调用[setButtonType(_:)]()方法进行配置。

如果将其配置为`加速器按钮`（类型为`NSAcceleratorButton`或`NSMultiLevelAcceleratorButton`），则可以将`按钮`设置为在用户单击`按钮`过程中发生压力变化时发送操作消息。

`按钮`可以具有两个状态（打开和关闭）或三个状态（打开，关闭和混合）。你可以通过调用[allowMixedState]()方法来启用第三种状态。开启和关闭状态（也称为交替和正常）表示`按钮`被单击还是未被单击。混合状态通常用于`复选框`或`单选按钮`，以允许使用其他中间状态。例如，假设`复选框`的状态表示文本字段是否包含粗体文本。如果文本字段中的所有文本均为粗体，则该`复选框`处于启用状态。如果所有文本都不为粗体，则该`复选框`处于关闭状态。如果某些文本为粗体，则复选框为混合状态。

对于大多数类型的`按钮`，`按钮`的值与其状态相匹配——值为`1`（表示打开），`0`（表示关闭）或`-1`（表示混合）。对于`压敏按钮`，该`按钮`的值改为指示压力水平。

`NSButton`和[NSMatrix]()都提供了一个控件视图，该视图显示了一个`NSButtonCell`对象。但是，尽管`Matrix`要求你直接访问`Button Cell`对象，但是大多数`Button`类的方法替代了相同声明的`Button Cell`方法。换句话说，`Button`方法的实现为你调用了相应的`Button Cell`的方法，从而使你不必考虑`Button Cell`的存在。唯一没有覆盖的`Button Cell`的方法是与用于显示等效键的字体以及用于突出显示或显示`Button`状态的特定方法有关。

## 主题

### 创建标准按钮

* [init(checkboxWithTitle: String, target: Any?, action: Selector?)]()
* [init(image: NSImage, target: Any?, action: Selector?)]()
* [init(radioButtonWithTitle: String, target: Any?, action: Selector?)]()
* [init(title: String, image: NSImage, target: Any?, action: Selector?)]()
* [init(title: String, target: Any?, action: Selector?)]()

### 配置Cell

* [class NSButtonCell]()

定义用户界面的`Button`或`View`的其他可单击区域的对象。

### 配置`Button`

* [func setButtonType(NSButton.ButtonType)]()

设置`Button`的类型，该类型会影响`Button`的用户界面和单击行为。

* [func getPeriodicDelay(UnsafeMutablePointer<Float>, interval: UnsafeMutablePointer<Float>)]()
Returns by reference the delay and interval periods for a continuous button.

* [func setPeriodicDelay(Float, interval: Float)]()
Sets the message delay and interval periods for a continuous button.

* [var alternateTitle: String]()
The title that the button displays when the button is in an on state.

* [var attributedTitle: NSAttributedString]()
The title that the button displays in an off state, as an attributed string.

* [var attributedAlternateTitle: NSAttributedString]()
The title that the button displays as an attributed string when the button is in an on state.

* [var title: String]()
The title displayed on the button when it’s in an off state.

* [var sound: NSSound?]()
The sound that plays when the user clicks the button.

* [var isSpringLoaded: Bool]()
A Boolean value that indicates whether spring loading is enabled for the button.

* [var maxAcceleratorLevel: Int]()
An integer value indicating the maximum pressure level for a button of type 
NSMultiLevelAcceleratorButton
.