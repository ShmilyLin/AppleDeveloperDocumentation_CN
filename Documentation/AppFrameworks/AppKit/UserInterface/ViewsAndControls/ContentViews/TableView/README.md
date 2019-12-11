# Table View

在行和列中显示自定义数据。



## 讲解

### Views

* [class NSTableView](./NSTableView/)

一组相关记录，显示在代表各个记录的行中和代表这些记录的属性的列中。

* [class NSTableCellView](./NSTableCellView/)

A reusable container view shown for a particular cell in a table view that uses rows for content.



---

### 管理

#### [protocol NSTableViewDataSource]

A set of methods that a table view uses to provide data to a table view and to allow the editing of the table view's data source object.

#### [protocol NSTableViewDelegate]

A set of optional methods you implement in a table view delegate to customize the behavior of the table view. 



---

### 行和列

#### [class NSTableHeaderView]

An object that draws headers over a table view's columns and handles mouse events in those headers.

#### [class NSTableHeaderCell]

An object that a table header view uses to draw the content of the column headers. 

#### [class NSTableRowView]

The view shown for a row in a table view.

#### [class NSTableColumn](./NSTableColumn.md)

显示一个`Table View`中一个列的性质和标示。

#### [class NSTableViewRowAction]

A single action to present when the user swipes horizontally on a table row. 

#### [struct NSTableColumn.ResizingOptions]