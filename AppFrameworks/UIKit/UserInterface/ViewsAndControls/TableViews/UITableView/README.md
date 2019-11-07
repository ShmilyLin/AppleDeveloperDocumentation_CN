# UITableView

　　使用排列在单列中的行显示数据的视图（view）。

> SDK : 
>   iOS 2.0+
>   tvOS 9.0+

---
## 概述

　　表视图（table view）是在一个单列中显示一个item的列表。`UITableView`是[UIScrollView]()的子类，它允许用户滚动表，尽管`UITableView`只允许垂直滚动。包含表的各个项的单元格（cell）是[UITableViewCell]()对象，`UITableView`使用这些对象来绘制表的可见行（row）。单元格（cell）包含有内容——标题和图像——并且可以在右边缘附近包含一个附件视图（accessory view）。标准附件视图（accessory view）是发现指示器（disclosure indicator）或详情发现按钮（detail disclosure button），前者引导到数据层次结构中的下一级别，后者引导到所选项目的详细视图。附件视图（accessory view）也可以是框架内的控件，例如开关（switch）和滑块（slider），或者可以是自定义视图（view）。表视图（table view）可以进入编辑模式，用户可以在其中对表的行（row）进行插入，删除和重新排序。

