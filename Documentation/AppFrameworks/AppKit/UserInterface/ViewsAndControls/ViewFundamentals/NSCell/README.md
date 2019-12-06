# NSCell

一个用于在一个`View`对象上显示文本或图片的结构，并且不需要一个完整的`NSView`子类的开销。

## 定义

```swift
class NSCell : NSObject
```

## 概述

大多数[NSControl](../NSControl/)类都使用`Cell`来实现其内部工作。

### 指定的初始化方法

子类化`NSCell`时，必须实现所有指定的初始化方法。这些方法包括`init`，[init(coder:)]()，[init(textCell:)]()和[init(imageCell:)]()。

## 主题

### 初始化一个`Cell`

* [init(imageCell: NSImage?)](./1533898-init.md)

    返回使用指定图像初始化并设置为具有`Cell`默认菜单的`NSCell`对象。

* [init(textCell: String)](./1530851-init.md)

    返回使用指定字符串初始化并设置为具有`Cell`默认菜单的`NSCell`对象。

### 管理`Cell`的值

* [var objectValue: Any?]()
The cell’s value as an Objective-C object.

* [var hasValidObjectValue: Bool]()
A Boolean value that indicates whether the cell has a valid object value.

* [var intValue: Int32]()
The cell’s value as an integer.

* [var integerValue: Int]()
The cell’s value as an 
NSInteger
 type.

* [var stringValue: String]()
The cell’s value as a string.

* [var doubleValue: Double]()
The cell’s value as a double-precision floating-point number.

* [var floatValue: Float]()
The cell’s value as a single-precision floating-point number.

### 管理`Cell`属性

* [func setCellAttribute(NSCell.Attribute, to: Int)](./1531257-setcellattribute.md)

    设置指定`Cell`属性的值。

* [func cellAttribute(NSCell.Attribute) -> Int]()
Returns the value for the specified cell attribute.

* [var type: NSCell.CellType](./1524871-type.md)

    `Cell`的类型。

* [var isEnabled: Bool]()
A Boolean value indicating whether the cell is currently enabled.

* [var allowsUndo: Bool]()
A Boolean value indicating whether the cell assumes responsibility for undo operations.

### 管理显示属性

* [var isBezeled: Bool]()
A Boolean value indicating whether the cell has a bezeled border.

* [var isBordered: Bool]()
A Boolean value indicating whether the cell draws itself outlined with a plain border.

* [var isOpaque: Bool]()
A Boolean value indicating whether the cell is completely opaque.

* [var backgroundStyle: NSView.BackgroundStyle](./1524686-backgroundstyle.md)

    `Cell`的背景样式。

* [var interiorBackgroundStyle: NSView.BackgroundStyle](./1526141-interiorbackgroundstyle.md)

    `Cell`的内部背景样式。

* [enum NSView.BackgroundStyle]()

    与[backgroundStyle](./1524686-backgroundstyle.md)和[interiorBackgroundStyle](./1526141-interiorbackgroundstyle.md)属性一起使用的背景样式。

### 管理`Cell`状态

* [var allowsMixedState: Bool]()
A Boolean value indicating whether the cell supports three states instead of two.

* [var nextState: Int](./1531235-nextstate.md)

    `Cell`的下一个状态。

* [func setNextState()](./1533557-setnextstate.md)

    将`Cell`的状态更改为序列中的下一个值。

* [var state: NSControl.StateValue](./1527417-state.md)

    `Cell`的当前状态。

* [struct NSControl.StateValue](./StateValue/)

### 管理字段属性

* [var isEditable: Bool]()
A Boolean value indicating whether the cell is editable.

* [var isSelectable: Bool]()
A Boolean value indicating whether the cell’s text can be selected.

* [var isScrollable: Bool]()
A Boolean value indicating whether excess text scrolls past the cell’s bounds.

* [var alignment: NSTextAlignment]()
The alignment of the cell’s text.

* [var font: NSFont?]()
The font that the cell uses to display text.

* [var lineBreakMode: NSLineBreakMode]()
The line break mode to use when drawing text in the cell.

* [var truncatesLastVisibleLine: Bool]()
A Boolean value indicating whether the cell truncates text that does not fit within the cell’s bounds.

* [var wraps: Bool]()
A Boolean value indicating whether the cell wraps text whose length that exceeds the cell’s frame.

* [var baseWritingDirection: NSWritingDirection]()
The initial writing direction used to determine the actual writing direction for text.

* [var attributedStringValue: NSAttributedString]()
The cell’s value as an attributed string.

* [var allowsEditingTextAttributes: Bool]()
A Boolean value indicating whether the cell allows the editing of its content’s text attributes by the user.

* [var importsGraphics: Bool]()
A Boolean value indicating whether the cell supports the importation of images into its text.

* [func setUpFieldEditorAttributes(NSText) -> NSText]()
Configures the textual and background attributes of the receiver's field editor.

* [var title: String]()
The cell’s title text.

### 管理`Target`和`Action`

* [var action: Selector?]()
The action performed by the cell.

* [var target: AnyObject?]()
The object that receives the cell’s action messages.

* [var isContinuous: Bool]()
A Boolean value indicating whether the cell sends its action message continuously during mouse tracking.

* [func sendAction(on: NSEvent.EventTypeMask) -> Int]()
Sets the conditions on which the receiver sends action messages to its target.

### 管理图片

* [var image: NSImage?](./1526028-image.md)

    `Cell`中显示的图片（如果有的话）。

### 管理标签

* [var tag: Int]()
A tag for identifying the cell.

### 格式化和验证数据

* [var formatter: Formatter?]()
The cell’s formatter object.

### 管理菜单

* [class var defaultMenu: NSMenu?]()
Returns the default menu for instances of the cell.

* [var menu: NSMenu?]()
The cell’s contextual menu.

* [func menu(for: NSEvent, in: NSRect, of: NSView) -> NSMenu?]()
Returns the menu associated with the cell and related to the specified event and frame.

### 比较`Cell`

* [func compare(Any) -> ComparisonResult]()
Compares the string values of the receiver another cell, disregarding case.

### 响应键盘事件

* [var acceptsFirstResponder: Bool]()
A Boolean value indicating whether the cell accepts first responder status.

* [var showsFirstResponder: Bool]()
A Boolean value indicating whether the cell provides a visual indication that it is the first responder.

* [var refusesFirstResponder: Bool]()
A Boolean value indicating whether the cell refuses the first responder status.

* [func performClick(Any?)]()
Simulates a single mouse click on the receiver.

### 衍生值

* [func takeObjectValueFrom(Any?)]()
Sets the value of the receiver’s cell to the object value obtained from the specified object.

* [func takeIntegerValueFrom(Any?)]()
Sets the value of the receiver’s cell to an integer value obtained from the specified object.

* [func takeIntValueFrom(Any?)]()
Sets the value of the receiver’s cell to an integer value obtained from the specified object.

* [func takeStringValueFrom(Any?)]()
Sets the value of the receiver’s cell to the string value obtained from the specified object.

* [func takeDoubleValueFrom(Any?)]()
Sets the value of the receiver’s cell to a double-precision floating-point value obtained from the specified object.

* [func takeFloatValueFrom(Any?)]()
Sets the value of the receiver’s cell to a single-precision floating-point value obtained from the specified object.

### 表示一个对象

* [var representedObject: Any?]()
The object represented by the cell.

### 追踪鼠标

* [func trackMouse(with: NSEvent, in: NSRect, of: NSView, untilMouseUp: Bool) -> Bool](./1533606-trackmouse.md)

    启动`Cell`中的鼠标跟踪行为。

* [func startTracking(at: NSPoint, in: NSView) -> Bool](./1526663-starttracking.md)

    开始跟踪接收者中的鼠标事件。

* [func continueTracking(last: NSPoint, current: NSPoint, in: NSView) -> Bool]()
Returns a Boolean value that indicates whether mouse tracking should continue in the receiving cell.

* [func stopTracking(last: NSPoint, current: NSPoint, in: NSView, mouseIsUp: Bool)]()
Stops tracking mouse events within the receiver.

* [var mouseDownFlags: Int]()
The modifier flags for the last (left) mouse-down event.

* [class var prefersTrackingUntilMouseUp: Bool]()
Returns a Boolean value that indicates whether tracking stops when the cursor leaves the cell.

* [func getPeriodicDelay(UnsafeMutablePointer<Float>, interval: UnsafeMutablePointer<Float>)]()
Returns the initial delay and repeat values for continuous sending of action messages to target objects.

### 命中测试

* [func hitTest(for: NSEvent, in: NSRect, of: NSView) -> NSCell.HitResult]()
Returns hit testing information for the receiver.

### 管理光标

* [func resetCursorRect(NSRect, in: NSView)]()
Sets the receiver to show the I-beam cursor while it tracks the mouse.

### 处理键盘替代

* [var keyEquivalent: String]()
The key equivalent associated with clicking the cell.

### 拖动`Cell`

* [func draggingImageComponents(withFrame: NSRect, in: NSView) -> [NSDraggingImageComponent]]()
Generates dragging image components with the specified frame in the view.

### 管理对焦环

* [func drawFocusRingMask(withFrame: NSRect, in: NSView)]()
Draws the focus ring for the control.

* [func focusRingMaskBounds(forFrame: NSRect, in: NSView) -> NSRect]()
Returns the bounds of the focus ring mask.

* [class var defaultFocusRingType: NSFocusRingType]()
Returns the default type of focus ring for the receiver.

* [var focusRingType: NSFocusRingType]()
The type of focus ring to use with the associated view.

### 确定`Cell`大小

* [func calcDrawInfo(NSRect)]()
Recalculates the cell geometry.

* [var cellSize: NSSize]()
The minimum size needed to display the cell.

* [func cellSize(forBounds: NSRect) -> NSSize]()
Returns the minimum size needed to display the receiver, constraining it to the specified rectangle.

* [func drawingRect(forBounds: NSRect) -> NSRect]()
Returns the rectangle within which the receiver draws itself

* [func imageRect(forBounds: NSRect) -> NSRect]()
Returns the rectangle in which the receiver draws its image.

* [func titleRect(forBounds: NSRect) -> NSRect]()
Returns the rectangle in which the receiver draws its title text.

* [var controlSize: NSControl.ControlSize]()
The size of the cell.

### 绘图和高亮显示

* [func draw(withFrame: NSRect, in: NSView)]()
Draws the receiver’s border and then draws the interior of the cell.

* [func highlightColor(withFrame: NSRect, in: NSView) -> NSColor?]()
Returns the color the receiver uses when drawing the selection highlight.

* [func drawInterior(withFrame: NSRect, in: NSView)]()
Draws the interior portion of the receiver, which includes the image or text portion but does not include the border.

* [var controlView: NSView?]()
The view associated with the cell.

* [func highlight(Bool, withFrame: NSRect, in: NSView)]()
Redraws the receiver with the specified highlight setting.

* [var isHighlighted: Bool]()
A Boolean value indicating whether the cell has a highlighted appearance.

### 编辑和选择文本

* [func edit(withFrame: NSRect, in: NSView, editor: NSText, delegate: Any?, event: NSEvent?)]()
Begins editing of the receiver’s text using the specified field editor.

* [func select(withFrame: NSRect, in: NSView, editor: NSText, delegate: Any?, start: Int, length: Int)]()
Selects the specified text range in the cell's field editor.

* [var sendsActionOnEndEditing: Bool]()
A Boolean value indicating whether the cell’s control object sends its action message when the user finishes editing the cell’s text.

* [func endEditing(NSText)]()
Ends the editing of text in the receiver using the specified field editor.

* [var wantsNotificationForMarkedText: Bool]()
A Boolean value indicating whether the cell’s field editor should post text change notifications.

* [func fieldEditor(for: NSView) -> NSTextView?]()
Returns a custom field editor for editing in the view.

* [var usesSingleLineMode: Bool]()
A Boolean value indicating whether the cell restricts layout and rendering of text to a single line.

### 管理扩展框架

* [func expansionFrame(withFrame: NSRect, in: NSView) -> NSRect]()
Returns the expansion cell frame for the receiver.

* [func draw(withExpansionFrame: NSRect, in: NSView)]()
Instructs the receiver to draw in an expansion frame.

### 用户界面布局方向

* [var userInterfaceLayoutDirection: NSUserInterfaceLayoutDirection]()
The layout direction of the user interface.

### 常量

* [enum NSCell.CellType](./CellType/)

    用于指定`Cell`如何表示其数据（作为文本或图像）的常量。

* [enum NSCell.Attribute](./Attribute/)

    用于指定`Button`在按下时的行为方式以及如何显示其状态的常量。

* [enum NSControl.ImagePosition]()
Constants for specifying the position of a button’s image relative to its title.

* [enum NSImageScaling]()
Constants that specify a cell’s image scaling behavior.

* [struct NSCell.StyleMask]()
Constants for specifying what happens when a button is pressed or is displaying its alternate state.

* [enum NSControlTint]()
Constants for specifying a cell’s tint color.

* [enum NSControl.ControlSize]()
Constants for specifying a cell’s size.

* [struct NSCell.HitResult]()
Constants used by the 
hitTest(for:in:of:)
 method to determine the effect of an event.

* [enum NSView.BackgroundStyle]()

    与[backgroundStyle](./1524686-backgroundstyle.md)和[interiorBackgroundStyle](./1526141-interiorbackgroundstyle.md)属性一起使用的背景样式。

* [Deprecated Scaling Constants]()
These are deprecated scaling constants.

* [Data Entry Types]()
These constants specify how a cell formats numeric data.

### 初始化

* [init()]()
* [init(coder: NSCoder)]()