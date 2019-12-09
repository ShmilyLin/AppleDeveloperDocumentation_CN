# `Control`与`Cell`如何交互

`Control`通常与一个或多个`Cell`相关联，这些`Cell`是抽象类`NSCell`的子类的实例。`Control`的一个或多个`Cell`通常恰好位于`Control`的边界之内。`Cell`是可以绘制自身并响应事件的对象，但是它们只能根据其`Control`的指示来间接地这样做，这是一种协调的背景。

`Control`管理其`Cell`的行为。通过从`NSView`继承，`Control`可以响应用户的操作并呈现其在屏幕上的表示。当用户单击`Control`时，它会通过将`trackMouse:inRect:ofView:untilMouseUp:`发送到所单击的`Cell`来部分响应。收到此消息后，`Cell`会跟踪鼠标，并可能使`Control`将`Cell`的操作消息发送到其`Target`（鼠标上移还是连续发送，取决于`Cell`的属性）。当`Control`收到显示请求时，它们依次向其一个或多个`Cell`发送一条`drawWithFrame:inView:`消息，以使这些`Cell`进行绘制。

`Control`与`Cell`之间的这种关系使两件事情成为可能：一个`Control`可以管理不同类型、`Target`和`Action`不同的`Cell`（请参阅下文），而单个`Control`可以管理多个`Cell`。大多数Application Kit`Control`（如`NSButtons`和`NSTextFields`）仅管理单个`Cell`。但是某些`Control`（尤其是`NSMatrix`和`NSForm`）可以管理多个`Cell`（通常具有相同的大小和属性，并以规则的方式排列）。由于`Cell`比`Control`轻，因此在继承数据和行为方面，使用多`Cell`的`Control`比使用多个`Control`更有效。

`NSControl`的许多方法（尤其是设置或获取值和属性的方法）在`NSCell`中都有相应的方法。向`Control`发送消息会导致将其转发到`Control`的`Cell`或（如果是多`Cell`的`控件`，则）其选定的`Cell`。但是，许多`NSControl`方法仅在具有单个`Cell`的`Control`中有效（这些方法说明中已提到）。

`NSControl`子类无需使用`NSCell`子类即可实现自身——`NSScroller`和`NSColorWell`是不需要这样做的`NSControl`的示例。但是，这样的子类必须处理`NSCell`所处理的细节。具体来说，它们必须重写设计用于`Cell`的方法。而且，缺少`Cell`意味着你无法利用`NSMatrix`功能来管理多`Cell`阵列，例如`单选按钮`。