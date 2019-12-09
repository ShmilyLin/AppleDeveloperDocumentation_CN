# 关于`Cell`和`Control`

本主题提供有关`NSCell`和`NSControl`的基本信息。

## 关于`NSCell`

`NSCell`类提供了一种在`NSView`中显示文本或图像的机制，而没有完整的`NSView`子类的开销。特别是，它通过对App中所有`NSCell`实例所使用的共享`NSText`对象的访问，提供了`NSText`类的许多功能。`NSCell`对于在`NSView`的自定义子类中的各个位置放置文本或图像也非常有用。

大多数`NSControl`类都大量使用`NSCell`来实现其内部工作。例如，`NSSlider`使用`NSSliderCell`，`NSTextField`使用`NSTextFieldCell`，`NSBrowser`使用`NSBrowserCell`。向`NSControl`发送消息通常比直接处理相应的`NSCell`更简单。例如，`NSControls`通常在更改`Cell`属性后调用`updateCell:`（使`Cell`显示）。相反，如果直接调用`NSCell`的相应方法，则`NSCell`可能不会再次自动显示自身。

`NSControl`的某些子类（尤其是`NSMatri`x）将`NSCell`按某种协作方式组合在一起。因此，使用`NSMatrix`，你可以实现大小统一的`单选按钮`组，而无需每个`按钮`都具有`NSView`（并且不需要`NSText`对象作为每个`按钮`上的文本的字段编辑器）。

`NSCell`类提供了用于显示文本或图像，编辑文本，设置和获取对象值，维护状态，突出显示和跟踪鼠标的原始方法。`NSCell`的方法`trackMouse:inRect:ofView:untilMouseUp:`实现了将动作消息发送到`Target`对象的机制。但是，`NSCell`只是抽象地实现了`Target/Action`功能，它将实现的细节放到了`NSActionCell`及其子类。

## 关于`NSControl`

`NSControl`是一个抽象超类，提供了用于实现用户界面设备的三个基本功能。首先，作为`NSView`的子类，`NSControl`绘制或协调绘制设备的屏幕表示。其次，它通过覆盖`NSResponder`的`mouseDown:`方法并在响应者链中提供位置来接收并响应用户生成的事件。第三，它实现了`sendAction:to:`方法，以向`NSControl`的`Target`对象发送操作消息。在Application Kit中定义的`NSControl`的子类是`NSBrowser`，`NSButton`（及其子类`NSPopUpButton`），`NSColorWell`，`NSImageView`，`NSMatrix`（及其子类`NSForm`），`NSScroller`，`NSSlider`，`NSTableView`和`NSTextField`。具体的`NSControl`子类的实例通常简称为`控件`。