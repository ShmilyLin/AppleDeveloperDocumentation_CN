# 子类化`NSButton`

如果你创建`NSButton`的子类来执行自己的初始化，则覆盖指定的初始化方法（`NSView`的`initWithFrame:`方法）。如果要将自定义`NSButtonCell`子类与`NSButton`的子类一起使用，则必须重写`cellClass:`方法，如在[子类化`NSControl`]()中所述。