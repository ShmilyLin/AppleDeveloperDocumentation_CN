# NSControl

`Control`的基本行为的定义，这些`Control`是一种特殊的`View`，可通过使用`Target-Action`设计模式将相关事件通知给你的App。

## 定义

```swift
class NSControl : NSView
```

## 概述

`NSControl`类是抽象的，必须被子类化才能使用。尽管你可以自己对它进行子类化，但更推荐的是，你应该使用`AppKit`已经定义的子类。`Control`在屏幕上绘制内容，自动处理与该内容的用户交互，并针对任何重要的用户交互调用其`Target`对象的[action]()方法。

### 关于协议方法

`NSControl`类为其子类提供了几种`Delegate`方法，这些方法允许进行文本编辑，例如[NSTextField]()和[NSMatrix]()。其中包括：[controlTextDidBeginEditing(_:)]()，[controlTextDidChange(_:)]()和[controlTextDidEndEditing(_:)]()。

请注意，尽管`NSControl`定义了`Delegate`方法，但它本身没有`Delegate`。使用这些方法的任何子类都必须具有一个`Delegate`以及获取和设置它的方法。此外，正式的`Delegate`协议[NSControlTextEditingDelegate]()还定义了`控件Delegate`使用的`Delegate`方法。

## 主题

### 创建一个`Control`

* [init(frame: NSRect)]()
Returns an NSControl object initialized with the specified frame rectangle.

* [init?(coder: NSCoder)]()

### 启用和禁用`Control`

* [var isEnabled: Bool]()
A Boolean value that indicates whether the receiver reacts to mouse events.

### 获取`Control`的值

* [var doubleValue: Double]()
The value of the receiver’s cell as a double-precision floating-point number.

* [var floatValue: Float]()
The value of the receiver’s cell as a single-precision floating-point number.

* [var intValue: Int32]()
The value of the receiver’s cell as an integer.

* [var integerValue: Int]()
The value of the receiver’s cell as an 
NSInteger
 value.

* [var objectValue: Any?]()
The value of the receiver’s cell as an Objective-C object.

* [var stringValue: String]()
The value of the receiver’s cell as an NSString object.

* [var attributedStringValue: NSAttributedString]()
The value of the receiver’s cell as an attributed string.

### 与其他`Control`进行交互

* [func takeDoubleValueFrom(Any?)]()
Sets the value of the receiver’s cell to a double-precision floating-point value obtained from the specified object.

* [func takeFloatValueFrom(Any?)]()
Sets the value of the receiver’s cell to a single-precision floating-point value obtained from the specified object.

* [func takeIntValueFrom(Any?)]()
Sets the value of the receiver’s cell to an integer value obtained from the specified object.

* [func takeIntegerValueFrom(Any?)]()
Sets the value of the receiver’s cell to an 
NSInteger
 value obtained from the specified object.

* [func takeObjectValueFrom(Any?)]()
Sets the value of the receiver’s cell to the object value obtained from the specified object.

* [func takeStringValueFrom(Any?)]()
Sets the value of the receiver’s cell to the string value obtained from the specified object.

### 格式化文本

* [var alignment: NSTextAlignment]()
The alignment mode of the text in the receiver’s cell.

* [var font: NSFont?]()
The font used to draw text in the receiver’s cell.

* [var lineBreakMode: NSLineBreakMode]()
The line break mode to use for text in the control’s cell.

* [var usesSingleLineMode: Bool]()
A Boolean value that indicates whether the text in the control’s cell uses single line mode.

* [var formatter: Formatter?]()
The receiver’s formatter.

* [var baseWritingDirection: NSWritingDirection]()
The initial writing direction used to determine the actual writing direction for text.

### 管理扩展工具提示

* [func draw(withExpansionFrame: NSRect, in: NSView)]()
Performs custom expansion tool tip drawing.

* [var allowsExpansionToolTips: Bool]()
A Boolean value that indicates whether expansion tool tips are shown when the control is hovered over.

* [func expansionFrame(withFrame: NSRect) -> NSRect]()
The frame in which a tool tip can be displayed, if needed.

### 管理字段编辑器

* [func abortEditing() -> Bool]()
Terminates the current editing operation and discards any edited text.

* [func currentEditor() -> NSText?]()
Returns the current field editor for the control.

* [func validateEditing()]()
Validates changes to any user-typed text.

* [func edit(withFrame: NSRect, editor: NSText, delegate: Any?, event: NSEvent)]()
Begins editing of the receiver’s text using the specified field editor.

* [func endEditing(NSText)]()
Ends the editing of text in the receiver using the specified field editor.

* [func select(withFrame: NSRect, editor: NSText, delegate: Any?, start: Int, length: Int)]()
Selects the specified text range in the receiver's field editor.

### 调整`Control`大小

* [var controlSize: NSControl.ControlSize](./1428871-controlsize.md)

    `Control`的大小。

* [enum NSControl.ControlSize](./controlsize.md)

    用于指定`Cell`大小的常量。

* [func sizeThatFits(NSSize) -> NSSize](./1428902-sizethatfits.md)

    要求`Control`计算并返回最适合指定尺寸的大小。

* [func sizeToFit()](./1428877-sizetofit.md)

    调整接收器框架的大小，使其成为容纳其`Cell`所需的最小尺寸。

### 显示`Cell`

* [var isHighlighted: Bool](./1428927-ishighlighted.md)

    一个布尔值，指示是否高亮显示`Cell`。

### 触发`Target/Action`机制

* [var action: Selector?]()
The default action-message selector associated with the control.

* [var target: AnyObject?]()
The target object that receives action messages from the cell.

* [var isContinuous: Bool]()
A Boolean value indicating whether the receiver’s cell sends its action message continuously to its target during mouse tracking.

* [func sendAction(Selector?, to: Any?) -> Bool]()
Causes the specified action to be sent the target.

* [func sendAction(on: NSEvent.EventTypeMask) -> Int]()
Sets the conditions on which the receiver sends action messages to its target.

### 访问标签

* [var tag: Int]()
The tag identifying the receiver (not the tag of the receiver’s cell).

### 从键盘激活

* [func performClick(Any?)]()
Simulates a single mouse click on the receiver.

* [var refusesFirstResponder: Bool]()
A Boolean value indicating whether the receiver refuses the first responder role.

### 追踪鼠标

* [func mouseDown(with: NSEvent)]()
Informs the receiver that the user has pressed the left mouse button.

* [var ignoresMultiClick: Bool]()
A Boolean value indicating whether the receiver ignores multiple clicks made in rapid succession.

### 支持基于约束的布局

* [func invalidateIntrinsicContentSize(for: NSCell)](./1526876-invalidateintrinsiccontentsize.md)

    通知控件其`Cell`的固有内容大小不再有效。

### 通知

An NSControl object posts the following notifications to interested observers and its delegate. Note that although the NSControl class defines delegate methods, it does not itself have a delegate. Any subclass that uses these methods must have a delegate and the methods to get and set it.

* [class let textDidBeginEditingNotification: NSNotification.Name]()
Sent when a control with editable cells begins an edit session.

* [class let textDidChangeNotification: NSNotification.Name]()
Sent when the text in the receiving control changes.

* [class let textDidEndEditingNotification: NSNotification.Name]()
Sent when a control with editable cells ends an editing session.

### 类型别名

* [struct NSControl.StateValue]()

### 枚举

* [enum NSControl.ImagePosition]()
Constants for specifying the position of a button’s image relative to its title.