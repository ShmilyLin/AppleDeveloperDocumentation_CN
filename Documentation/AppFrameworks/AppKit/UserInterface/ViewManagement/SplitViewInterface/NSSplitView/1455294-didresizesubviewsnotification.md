# didResizeSubviewsNotification

在`NSSplitView`更改其部分或全部`Subview`的大小后发布。

## 定义

```swift
class let didResizeSubviewsNotification: NSNotification.Name
```

## 说明

`通知`对象是调整其`子视图`大小的`NSSplitView`。

> **注意**
> 
> 在macOS 10.5及更高版本中，如果由于用户拖动分隔线而发送了通知，则`userInfo`字典包含一个键`NSSplitViewDividerIndex`，其中包含一个`NSNumber`包裹的`NSInteger`，它是被拖动的分隔线的索引。在任何情况下，早期版本的macOS均不会返回`userInfo`字典。