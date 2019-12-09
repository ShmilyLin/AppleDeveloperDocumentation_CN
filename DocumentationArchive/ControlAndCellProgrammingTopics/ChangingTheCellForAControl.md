# 更改`Control`的`Cell`

由于`NSControl`使用从`NSCell`类派生的对象来实现其大部分功能，因此通常可以通过创建`NSCell`的子类而不是`NSControl`来实现唯一的用户界面设备。举例来说，假设你希望所有应用程序的`NSSlider`都具有除普通`NSSliderCell`之外的其他类型的`Cell`。首先，创建`NSCell`、`NSActionCell`或`NSSliderCell`的子类。（我们称它为`MyCellSubclass`。）然后，你只需调用`NSSlider`的`setCellClass`类方法即可：

```Objective-C
[NSSlider setCellClass:[MyCellSubclass class]];
```

此后创建的所有`NSSlider`都将使用`MyCellSubclass`，直到再次调用`setCellClass:`为止。

如果要在与使用`MyCellSubclass`的自定义`NSSlider`相同的App中创建通用`NSSlider`（使用`NSSliderCell`的App），则有两种可能的方法。一种是调用`setCellClass:`如上所述，每当你要创建自定义`NSSlider`时，随后将`Cell`类重置为`NSSliderCell`。另一种方法是创建一个`NSSlider`的自定义子类，该子类自动使用`MyCellSubclass`，如`NSControl`类参考中所述。