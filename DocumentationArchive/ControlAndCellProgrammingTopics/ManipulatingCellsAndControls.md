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

如果`Cell`显示的是图像而不是文本（或除文本之外也显示图像），则可以通过覆盖[imageRectForBounds:]()方法来影响图像在`Cell`中的放置，该方法由`NSCell`和`NSMenuItemCell`类都声明。此方法返回绘制`Cell`图像的矩形，通常是一个稍微偏离`Cell`边界的矩形。例2给出了一个示例。

> **注意：** 此技术要求你将`Cell`类子类化。有关信息，请参见[“对NSCell进行子类化”]()。

**例2** 将图像居中放置在`Cell`中
```Objective-C
- (NSRect) imageRectForBounds:(NSRect)theBounds {
    NSRect r = theBounds;
    // get size. If no image, result of method returning NSSize is undefined so assume NSZeroSize
    NSSize imageSize = [self image] != nil ? [[self image] size] : NSZeroSize;
    r.origin.x = floor((r.size.width/2)  - (imageSize.width/2)  + 0.5);
    r.origin.y = floor((r.size.height/2) - (imageSize.height/2) + 0.5);
    r.size     = imageSize;
    return r;
}
```

在此示例中，`Cell`将图像居中。请注意，它会将返回值四舍五入到最接近的像素，以避免使用部分像素偏移可能导致的绘图模糊。该代码还将返回的矩形的`size`字段设置为图像的大小，以便在矩形中正确绘制（假设`NSImage`对象使用[drawInRect:fromRect:operation:fraction:]()进行绘制，而不使用[compositeToPoint:operation:]()）。