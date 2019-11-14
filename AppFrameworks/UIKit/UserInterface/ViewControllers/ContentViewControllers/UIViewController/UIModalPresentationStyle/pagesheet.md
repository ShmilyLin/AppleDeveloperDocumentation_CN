# UIModalPresentationStyle.pageSheet

一种呈现样式，部分覆盖了基础内容。

## 定义

```swift
case pageSheet = 1
```

## 说明

在水平规则（Horizontally Regular）和垂直规则（Vertically Regular）的环境中，此选项在背景内容上添加一个调光层，并以大致页面大小的尺寸显示View Controller的内容，其中高度大于宽度。实际尺寸会根据设备的屏幕尺寸和方向而有所不同，但是部分底层内容始终保持可见。

在垂直规则（Vertically Regular）但水平紧凑（Horizontally Compact）的环境中，此选项显示sheet界面，其中部分底层内容在屏幕顶部附近仍然可见。

在垂直紧凑（Vertically Compact）的环境中，此选项与[UIModalPresentationStyle.fullScreen](./fullScreen.md)基本相同。

如果基础内容仍然可见，则Presenting View Controller不会收到[viewWillDisappear(_:)]()和[viewDidDisappear(_:)]()回调。