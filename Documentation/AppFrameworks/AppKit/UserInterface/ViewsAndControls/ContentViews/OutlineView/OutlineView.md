# Outline View

将层级数据以列表的形式展示出来，每一个层级相对于前一个层级都有一定的缩进距离。



## 讲解

### 视图

* **[class NSOutlineView](./NSOutlineView.md)**

一个用一个行列格式显示层级数据的视图，比如可以展开和折叠的目录或文件系统。



### Management

`protocol NSOutlineViewDataSource`

A set of methods that an outline view calls to retrieve data and information about it from the data source delegate, and—optionally—to update data values.

`protocol NSOutlineViewDelegate`

A set of optional methods implemented by delegates of [`NSOutlineView`](https://developer.apple.com/documentation/appkit/nsoutlineview) objects.



## 相关内容

### 内容视图

* **[Browser View]**

Provide a column-based interface for viewing and navigating hierarchical information.

* **[Collection View](../CollectionView/CollectionView.md)**

在一个高度可配置的排列中展示一个或多个子视图。

* **[class NSOpenGLView]**

A view that displays OpenGL content in a view.

* **[Table View]**

Display custom data in rows and columns.

* **[class NSTextView]**

A view that draws text and handles user interactions with that text.