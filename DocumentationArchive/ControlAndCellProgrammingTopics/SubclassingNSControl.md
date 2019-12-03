# 子类化`NSControl`

如果要创建执行其自身初始化的自定义[NSControl]()类，则应重写指定的初始化程序（[initWithFrame:]())。但是请注意，当从`nil`文件创建Application Kit `Control`类的子类的实例时，不会调用此方法。

如果创建与自定义`Cell`子类配对的自定义`Control`子类（例如，[NSSlider]()的自定义子类和[NSSliderCell]()的自定义子类），则可以通过两种方式将该自定义`Cell`的实例与该自定义`Control`的实例相关联。第一种方法要求你具有3.0版的`Interface Builder`。在`Interface Builder`中，将`Control`放在`窗口`上时，将实例化`Control`及其`Cell`，并在保存用户界面时将这些对象（以及其他放置的对象）编码并序列化为`nib`文件。`Interface Builder`还可以帮助你定义自定义子类，包括框架控件类的子类，例如`NSButton`和`NSSlider`。`Interface Builder`还允许你将放置的`Control`对象的类更改为自定义`Control`类，但是App的早期版本无法对与`Control`对象关联的自定义`Cell`进行相同的操作。

但是使用`Interface Builder`3.0版，你可以设置`Control Cell`的类。为此，请单击`Control`以将其选中，然后右键单击鼠标（按住Control键单击单键鼠标）。然后再次在出现的弹出列表的右上角单击。子菜单列出了鼠标指针下方的对象，包括`Control`的`Cell`。对于`NSSliderCell`对象，如图1所示，子菜单包含“Slider Cell”项。选择`Cell`项。

![图1在Interface Builder中选择`Control`的`Cell`](./select_cell_of_control.jpg)

接下来，打开所选`Cell`对象的`Inspector`窗口。找到“`Object inspector`”部分，然后在`Custom Class`组合框中选择（或输入）自定义`Cell`类的名称。

![图2设置`Control`的自定义`Cell`类](./set_class_of_cell.jpg)

如果没有3.0版本的`Interface Builder`，你仍然可以通过编程的方式将自定义`Cell`的实例分配给自定义`Control`，如例1所示。在自定义`Control`子类中，当从`nib`初始化时，创建自定义`Cell`的实例，并为其分配当前`Cell`的所有相关属性。然后使用`NSControl`的`setCell:`方法将自定义`Cell`设置为`Control`的`Cell`。

**例1** 为自定义`Control`创建和设置自定义`Cell`
```Objective-C
- (void)awakeFromNib {
    MySliderCell *newCell = [[MySliderCell alloc] init];
    id oldCell = [self cell];
    [newCell setImage:[oldCell image]];
    [newCell setMinValue:[oldCell minValue]];
    [newCell setMaxValue:[oldCell maxValue]];
    [newCell setSliderType:[oldCell sliderType]];
    // ....  set other slider cell attributes
    [self setCell:newCell];
    [newCell release];
}
```

每当`Control`需要为其自己创建一个新`Cell`时（例如，如果它是使用`initWithFrame:`实例化的），都可以重写[cellClass]()方法。`initWithFrame:`方法使用`cellClass`的返回值来分配和初始化正确类型的`NSCell`对象。

**例2** 重写`cellClass`
```Objective-C
+ (Class) cellClass
{
    return [MySliderCell class];
}
```

**注意** 重写`NSControl`的`cellClass`类方法不会更改从nib文件创建的`Cell`对象的类。