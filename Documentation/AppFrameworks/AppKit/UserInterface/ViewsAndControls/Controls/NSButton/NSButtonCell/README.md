# NSButtonCell

定义用户界面的`Button`或`View`的其他可单击区域的对象。

## 定义

```swift
class NSButtonCell : NSActionCell
```

## 概述

设置NSButtonCell对象的整数，浮点数，双精度数或对象值会导致调用状态，并将值转换为整数。在[objectValue]()的情况下，`nil`等于`0`，并且不响应[intValue]()的非`null`对象会将`state`设置为`1`。否则，state将设置为对象的[intValue]()。同样，对于大多数`按钮`类型，查询`NSButtonCell`的整数，浮点，双精度或对象值会返回所请求表示形式中的当前状态。对于[objectValue]()，这是一个`NSNumber`，其中`on`表示`true`，`off`表示`false`，混合状态的整数值`-`1。对于支持压力敏感性的系统上的加速器按钮（类型为[NSAcceleratorButton]()或[NSMultiLevelAcceleratorButton]()），查询[doubleValue]()将返回在按下按钮时施加的压力量。

`NSButtonCell`对象的配置控制按钮对象的外观和行为，但是单击按钮时，是由NSButton发送消息的。有关NSButtonCell行为的更多信息，请参见NSButton和NSMatrix类规范以及Button编程主题。

### 例外情况

在执行compare（_ :)方法（在NSCell中声明）的实现中，如果otherCell参数不是NSButtonCell类的对象，则NSButtonCell会引发NSBadComparisonException。