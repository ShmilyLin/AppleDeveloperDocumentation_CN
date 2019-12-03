# 操纵`Cell`和`Control`

本文包含用于处理`Cell`和`Control`的其他技巧和示例。

## 设置`Cell`或`Control`的大小

要将`Cell`（以及任何封闭的只有一个`Cell`的`Control`）的大小设置为符合人机界面准则的最佳大小，请执行以下操作：

1. 如果`Cell`包含文本，请将文本的字体设置为与以下三种标准大小之一一致：`regular`，`small`和`mini`。为此，请使用`NSFont`类方法[systemFontSizeForControlSize:]()。该方法的参数是`NSControl`类声明的[NSControlSize]()常量。

```objective-c
float fontSize = [NSFont systemFontSizeForControlSize:NSMiniControlSize];
NSCell *theCell = [theControl cell];
NSFont *theFont = [NSFont fontWithName:[[theCell font] fontName] size:fontSize];
[theCell setFont:theFont];
```

2. 使用相同的常数将`Control`大小设置为与字体大小相同的大小。使用`NSControl`的[setControlSize:]()方法。

```objective-c
[theCell setControlSize:NSMiniControlSize];
```

3. 最后，将[sizeToFit]()发送到`Control`以修剪额外的宽度。

```objective-c
[theControl sizeToFit];
```

## 在`Cell`边界内绘制聚焦环

The NSSetFocusRingStyle sets the style that a focus ring will be drawn in the next time you fill a bezier path. It takes a constant of type of NSFocusRingPlacement to tell the Application Kit to draw the focus ring over an image, under text, or (when neither text or image is a consideration) around a shape. You can use this function with a constant of NSFocusRingOnly to draw a focus ring just inside a cell's bounds.

Listing 1 shows how you draw such a focus ring. It requires you to override the NSCell drawWithFrame:inView:. In this method, if the cell is supposed to draw evidence of first-responder status, set the rectangle for the focus ring, call NSSetFocusRingStyle with an argument of NSFocusRingOnly, and then create and fill a bezier path defining that rectangle. Filling in this case simply draws the ring.

Note: This technique requires you to subclass a cell class. See "Subclassing NSCell" for information.

Listing 1  Drawing a focus ring just inside a cell's bounds

```objective-c
- (void)drawWithFrame:(NSRect)cellFrame inView:(NSView *)controlView {
    // other stuff might happen here
    if ([self showsFirstResponder]) {
         // showsFirstResponder is set for us by the NSControl that is drawing  us.
        NSRect focusRingFrame = cellFrame;
        focusRingFrame.size.height -= 2.0;
        [NSGraphicsContext saveGraphicsState];
        NSSetFocusRingStyle(NSFocusRingOnly);
        [[NSBezierPath bezierPathWithRect: NSInsetRect(focusRingFrame,4,4)] fill];
        [NSGraphicsContext restoreGraphicsState];
    }
     // other stuff might happen here
}
```

## 在`Cell`内放置图像