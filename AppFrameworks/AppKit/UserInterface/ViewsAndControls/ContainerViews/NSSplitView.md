# NSSplitView

在一个水平或竖直的线性堆中排列两个或多个视图的视图。



## 概述

一个`Split View`管理着一个`Split View Controller`（一个`NSSplitViewController`的实例）的分隔器和方向。默认情况下，分隔器是水平方向的，因此同级视图垂直分布，从上到下包含在`Split View Controller`中。

Divider indices are zero-based, with the leftmost or topmost divider (depending on the value of the [`isVertical`](apple-reference-documentation://hs0avxpUgt) property) having an index of `0`.



## 讲解

### 自定义SplitView行为事件

