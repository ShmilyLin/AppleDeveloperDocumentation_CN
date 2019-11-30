# NSMenu

管理应用菜单的对象。

## 定义

```swift
class NSMenu : NSObject
```

## 主题

### 管理菜单栏

* [class func menuBarVisible() -> Bool]()

返回一个布尔值，该值指示菜单栏是否可见。

* [class func setMenuBarVisible(Bool)]()

设置菜单栏是否可见并是否可被用户选择。

* [var menuBarHeight: CGFloat]()

主菜单的菜单栏高度（以像素为单位）。

### 创建一个`NSMenu`对象

* [init(title: String)]()

初始化并返回一个具有指定标题且启用了菜单项自动启用功能的菜单。

### 添加和删除菜单项

* [func insertItem(NSMenuItem, at: Int)]()

将菜单项插入菜单中的指定位置。

* [func insertItem(withTitle: String, action: Selector?, keyEquivalent: String, at: Int) -> NSMenuItem]()

Creates and adds a menu item at a specified location in the menu.
* [func addItem(NSMenuItem)]()

Adds a menu item to the end of the menu.
* [func addItem(withTitle: String, action: Selector?, keyEquivalent: String) -> NSMenuItem]()

Creates a new menu item and adds it to the end of the menu.
* [func removeItem(NSMenuItem)]()

Removes a menu item from the menu.
* [func removeItem(at: Int)]()

Removes the menu item at a specified location in the menu.
* [func itemChanged(NSMenuItem)]()

Invoked when a menu item is modified visually (for example, its title changes).
* [func removeAllItems()]()

Removes all the menu items in the menu.

### 查找菜单项

* [func item(withTag: Int) -> NSMenuItem?]()

Returns the first menu item in the menu with the specified tag.
* [func item(withTitle: String) -> NSMenuItem?]()

Returns the first menu item in the menu with a specified title.
* [func item(at: Int) -> NSMenuItem?]()

Returns the menu item at a specific location of the menu.
* [var numberOfItems: Int]()

The number of menu items in the menu, including separator items.
* [var items: [NSMenuItem]]()

An array containing the menu items in the menu.

### 查找菜单项的索引

* [func index(of: NSMenuItem) -> Int]()

Returns the index identifying the location of a specified menu item in the menu.
* [func indexOfItem(withTitle: String) -> Int]()

Returns the index of the first menu item in the menu that has a specified title.
* [func indexOfItem(withTag: Int) -> Int]()

Returns the index of the first menu item in the menu identified by a tag.
* [func indexOfItem(withTarget: Any?, andAction: Selector?) -> Int]()

Returns the index of the first menu item in the menu that has a specified action and target.
* [func indexOfItem(withRepresentedObject: Any?) -> Int]()

Returns the index of the first menu item in the menu that has a given represented object.
* [func indexOfItem(withSubmenu: NSMenu?) -> Int]()

Returns the index of the menu item in the menu with the given submenu.

### 管理子菜单

* [func setSubmenu(NSMenu?, for: NSMenuItem)]()

Assigns a menu to be a submenu of the menu controlled by a given menu item.
* [func submenuAction(Any?)]()

The action method assigned to menu items that open submenus.
* [var supermenu: NSMenu?]()

The parent menu that contains the menu as a submenu.

### 启用和禁用菜单项

* [var autoenablesItems: Bool]()

指示菜单是否自动启用和禁用其菜单项。

* [func update()]()

根据[NSMenuValidation]()非正式协议启用或禁用菜单的菜单项，并在必要时调整菜单大小以适合其当前菜单项。

### 获取和设置菜单字体

* [var font: NSFont!]()

The font of the menu and its submenus.

### 处理键盘等效项

* [func performKeyEquivalent(with: NSEvent) -> Bool]()

对与给定键等效的菜单项执行操作。

### 模拟鼠标点击

* [func performActionForItem(at: Int)]()

使应用程序将指定菜单项的操作消息发送到其目标。

### 管理标题

* [var title: String]()

The title of the menu.

### 配置菜单大小

* [var minimumWidth: CGFloat]()

The minimum width of the menu in screen coordinates.
var size: NSSize

The size of the menu in screen coordinates

### 获取菜单属性

* [var propertiesToUpdate: NSMenu.Properties]()

The available properties for the menu.

### 显示上下文菜单

* [var allowsContextMenuPlugIns: Bool]()

Indicates whether the pop-up menu allows appending of contextual menu plug-in items.

### 显示上下文相关帮助

* [class func popUpContextMenu(NSMenu, with: NSEvent, for: NSView)]()

Displays a contextual menu over a view for an event.
* [class func popUpContextMenu(NSMenu, with: NSEvent, for: NSView, with: NSFont?)]()

Displays a contextual menu over a view for an event using a specified font.

* [func popUp(positioning: NSMenuItem?, at: NSPoint, in: NSView?) -> Bool]()

Pops up the menu at the specified location.

### 管理状态列的显示

* [var showsStateColumn: Bool]()

Indicates whether the menu displays the state column.

### 处理高亮

* [var highlightedItem: NSMenuItem?]()

Indicates the currently highlighted item in the menu.

### 管理用户界面

* [var userInterfaceLayoutDirection: NSUserInterfaceLayoutDirection]()

配置菜单中菜单项的布局方向。

### 管理Delegate

* [var delegate: NSMenuDelegate?]()

The delegate of the menu.

### 处理跟踪

* [func cancelTracking()]()

Dismisses the menu and ends all menu tracking.
* [func cancelTrackingWithoutAnimation()]()

Dismisses the menu and ends all menu tracking without displaying the associated animation.

### 常量

* [struct NSMenu.Properties]()

These constants are used as a bitmask for specifying a set of menu or menu item properties, and are contained by the
propertiesToUpdate
property.

### 通知

* [class let didAddItemNotification: NSNotification.Name]()

Posted after a menu item is added to the menu.
* [class let didChangeItemNotification: NSNotification.Name]()

Posted after a menu item in the menu changes appearance.
* [class let didBeginTrackingNotification: NSNotification.Name]()

Posted when menu tracking begins.
* [class let didEndTrackingNotification: NSNotification.Name]()

Posted when menu tracking ends, even if no action is sent.
* [class let didRemoveItemNotification: NSNotification.Name]()

Posted after a menu item is removed from the menu.
* [class let didSendActionNotification: NSNotification.Name]()

Posted just after the application dispatches a menu item’s action method to the menu item’s target.
* [class let willSendActionNotification: NSNotification.Name]()

Posted just before the application dispatches a menu item’s action method to the menu item’s target.

### 初始化

* [init(coder: NSCoder)]()