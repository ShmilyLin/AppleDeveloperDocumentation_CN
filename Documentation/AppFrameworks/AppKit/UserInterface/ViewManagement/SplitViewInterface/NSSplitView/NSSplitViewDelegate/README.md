# NSSplitViewDelegate

`NSSplitViewDelegate`协议定义[NSSplitView]的`Delegate`可选实现的方法。

## 定义

```swift
protocol NSSplitViewDelegate
```

## 主题

### 管理`子视图`

* [func splitView(NSSplitView, resizeSubviewsWithOldSize: NSSize)](./1455273-splitview.md)

    允许`Delegate`为`NSSplitView`发送器的`子视图`指定自定义大小行为。

* [func splitViewWillResizeSubviews(Notification)]()

    默认通知中心调用以通知`Delegate`，`分隔视图`将调整其`子视图`的大小。

* [func splitViewDidResizeSubviews(Notification)](./1455314-splitviewdidresizesubviews.md)

    默认通知中心调用以通知`Delegate`，`分隔视图`已经调整完其`子视图`的大小。

* [func splitView(NSSplitView, canCollapseSubview: NSView) -> Bool](./1455304-splitview.md)

    允许`Delegate`确定用户是否可以折叠和取消折叠`子视图`。

* [func splitView(NSSplitView, shouldAdjustSizeOfSubview: NSView) -> Bool]()

    允许`Delegate`指定是否应调整`子视图`的大小。

### 配置和绘制`视图分隔线`

* [func splitView(NSSplitView, effectiveRect: NSRect, forDrawnRect: NSRect, ofDividerAt: Int) -> NSRect]()

    允许`Delegate`修改矩形，在该矩形中单击鼠标即可启动分隔线拖动。

* [func splitView(NSSplitView, shouldHideDividerAt: Int) -> Bool]()

    允许`Delegate`确定是否可以将分隔线拖动或调整到`分隔视图`的边缘之外。

* [func splitView(NSSplitView, additionalEffectiveRectOfDividerAt: Int) -> NSRect]()

    允许`Delegate`返回一个附加的矩形，在该矩形中单击鼠标将启动分隔线拖动。

## 限制分隔位置

* [func splitView(NSSplitView, constrainMaxCoordinate: CGFloat, ofSubviewAt: Int) -> CGFloat]()

    当用户拖动分隔线时，允许发送器的`Delegate`限制分隔线的最大坐标限制。

* [func splitView(NSSplitView, constrainMinCoordinate: CGFloat, ofSubviewAt: Int) -> CGFloat]()

    当用户拖动分隔线时，允许发送器的`Delegate`限制分隔线的最小坐标限制。

* [func splitView(NSSplitView, constrainSplitPosition: CGFloat, ofSubviewAt: Int) -> CGFloat]()

    允许发送器的`Delegate`将分隔线限制在某些位置。