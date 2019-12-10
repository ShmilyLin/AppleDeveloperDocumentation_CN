# Core Graphics

利用Quartz技术的力量执行具有高保真输出的轻量级2D渲染。处理基于路径的绘图，抗锯齿渲染，渐变，图像，颜色管理，PDF文档等。

## 概述

Core Graphics框架基于Quartz高级绘图引擎。它提供了低级的轻量级的2D渲染，具有无与伦比的输出保真度。你使用此框架来处理基于路径的绘图，转换，颜色管理，屏幕外渲染，图案，渐变和阴影，图像数据管理，图像创建和图像蒙版，以及PDF文档的创建，显示和解析。

在macOS中，Core Graphics还包括用于处理显示硬件，低级用户输入事件和窗口系统的服务。

## 主题

### 几何数据类型

struct CGFloat
The basic type for floating-point scalar values in Core Graphics and related frameworks.

struct CGPoint
A structure that contains a point in a two-dimensional coordinate system.

struct CGSize
A structure that contains width and height values.

struct CGRect
A structure that contains the location and dimensions of a rectangle.

struct CGVector
A structure that contains a two-dimensional vector.

struct CGAffineTransform
An affine transformation matrix for use in drawing 2D graphics.

### 2D绘图

* [class CGContext](./2DDrawing/CGContext/)

    Quartz 2D绘图环境。

* [class CGImage](./2DDrawing/CGImage/)
A bitmap image or image mask.

* [class CGPath](./2DDrawing/CGPath/)
An immutable graphics path: a mathematical description of shapes or lines to be drawn in a graphics context.

* [class CGMutablePath](./2DDrawing/CGMutablePath/)
A mutable graphics path: a mathematical description of shapes or lines to be drawn in a graphics context.

* [class CGLayer](./2DDrawing/CGLayer/)
An offscreen context for reusing content drawn with Core Graphics.