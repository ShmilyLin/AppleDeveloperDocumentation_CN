# CALayer

一个对象，该对象管理基于图像的内容，并允许你对该内容执行动画。

## 定义

```swift
class CALayer : NSObject
```

## 概述

`Layer`通常用于为`View`提供后备存储，但是也可以在没有`View`的情况下使用`Layer`来显示内容。`Layer`的主要工作是管理你提供的视觉内容，但是`Layer`本身具有可以设置的视觉属性，例如背景颜色，边框和阴影。除了管理视觉内容之外，`Layer`还维护有关其内容的几何形状（例如其位置，大小和变换）的信息，这些信息用于在屏幕上呈现该内容。修改`Layer`的属性是在`Layer`的内容或几何图形上启动动画的方式。`Layer`对象采用[CAMediaTiming]()协议来封装`Layer`及其动画的持续时间和步调，该协议定义了`Layer`的计时信息。

如果`Layer`对象是由`View`创建的，则`View`通常会自动将其自身分配为`Layer`的`Delegate`，并且你不应更改该关系。对于你自己创建的图层，你可以分配一`Delegate`对象，并使用该对象动态提供`Layer`的内容并执行其他任务。`Layer`还可以具有一个布局管理器对象（分配给[layoutManager]()属性），以分别管理子视图的布局。

## 主题

### 创建一个`Layer`

* [init()](./1410835-init.md)

    返回一个初始化完成的`CALayer`对象。

* [init(layer: Any)]()

    重写以复制或自定义初始化指定层的字段。

* [init(remoteClientId: UInt32)]()

    使用远程客户端ID初始化层。

### 访问相关的`Layer`对象

* [func presentation() -> Self?]()

    返回表示层对象的副本，该对象表示当前在屏幕上显示的`Layer`的状态。

* [func model() -> Self]()

    返回与接收器关联的模型层对象（如果有）。

### 访问`Delegate`

* [var delegate: CALayerDelegate?]()

    `Layer`的`Delegate`对象。

### 提供`Layer`的内容

* [var contents: Any?]()

    提供`Layer`内容的对象。可设置动画。

* [var contentsRect: CGRect]()

    单位坐标空间中的矩形，用于定义应使用的`Layer`内容部分。可设置动画。

* [var contentsCenter: CGRect]()

    矩形，用于定义在调整`Layer`内容大小时如何缩放`Layer`内容。可设置动画。

* [func display()](./1410926-display.md)

    重新加载该`Layer`的内容。

* [func draw(in: CGContext)]()

    使用指定的图形上下文绘制`Layer`的内容。

### 更改`Layer`的显示

* [var contentsGravity: CALayerContentsGravity]()

    一个常数，指定`Layer`内容如何在其边界内定位或缩放。

* [Contents Gravity Values]()

    当`Layer`边界大于内容对象的边界时，内容重力常数指定内容对象的位置。它们由[contentsGravity]()属性使用。

* [var opacity: Float]()

    接收者的不透明度。可设置动画。

* [var isHidden: Bool]()

    指示是否显示`Layer`的布尔值。可设置动画。

* [var masksToBounds: Bool]()

    一个布尔值，指示是否将子层裁剪到该`Layer`的边界（即，超出`Layer`边界不显示）。可设置动画。

* [var mask: CALayer?]()

    可选图层，其Alpha通道用于掩盖`Layer`的内容。

* [var isDoubleSided: Bool]()

    一个布尔值，指示当背离查看器时，`Layer`是否显示其内容。可设置动画。

* [var cornerRadius: CGFloat]()

    绘制图层背景的圆角时使用的半径。可设置动画。

* [var maskedCorners: CACornerMask]()

* [struct CACornerMask]()

* [var borderWidth: CGFloat]()

    `Layer`边框的宽度。可设置动画。

* [var borderColor: CGColor?]()

    `Layer`边框的颜色。可设置动画。

* [var backgroundColor: CGColor?]()

    接收器的背景颜色。可设置动画。

* [var shadowOpacity: Float]()

    `Layer`阴影的不透明度。可设置动画。

* [var shadowRadius: CGFloat]()

    用于渲染`Layer`阴影的模糊半径（以点为单位）。可设置动画。

* [var shadowOffset: CGSize]()

    `Layer`阴影的偏移量（以点为单位）。可设置动画。

* [var shadowColor: CGColor?]()

    `Layer`阴影的颜色。可设置动画。

* [var shadowPath: CGPath?]()

    `Layer`阴影的形状。可设置动画。

* [var style: [AnyHashable : Any]?]()

    可选字典，用于存储未由`Layer`明确定义的属性值。

* [var allowsEdgeAntialiasing: Bool]()

    一个布尔值，指示是否允许该`Layer`执行边缘抗锯齿。

* [var allowsGroupOpacity: Bool]()

    一个布尔值，指示是否允许该`Layer`将其自身作为与其父级分开的组进行组合。

### `Layer`过滤器

* [var filters: [Any]?
An array of Core Image filters to apply to the contents of the layer and its sublayers. Animatable.

* [var compositingFilter: Any?
A CoreImage filter used to composite the layer and the content behind it. Animatable.

* [var backgroundFilters: [Any]?
An array of Core Image filters to apply to the content immediately behind the layer. Animatable.

* [var minificationFilter: CALayerContentsFilter
The filter used when reducing the size of the content.

* [var minificationFilterBias: Float
The bias factor used by the minification filter to determine the levels of detail.

* [var magnificationFilter: CALayerContentsFilter
The filter used when increasing the size of the content.

### 配置`Layer`渲染行为

* [var isOpaque: Bool]()

    一个布尔值，指示该`Layer`是否包含完全不透明的内容。

* [var edgeAntialiasingMask: CAEdgeAntialiasingMask]()

    定义如何光栅化接收器边缘的位掩码。

* [func contentsAreFlipped() -> Bool]()

    返回一个布尔值，指示在渲染时是否隐式翻转`Layer`内容。

* [var isGeometryFlipped: Bool]()

    一个布尔值，指示该`Layer`及其子层的几何形状是否垂直翻转。

* [var drawsAsynchronously: Bool]()

    一个布尔值，指示是否在后台线程中延迟和异步处理绘图命令。

* [var shouldRasterize: Bool]()

    一个布尔值，指示在合成之前是否将`Layer`渲染为位图。可设置动画。

* [var rasterizationScale: CGFloat]()

    相对于`Layer`的坐标空间栅格化内容的比例。可设置动画。

* [var contentsFormat: CALayerContentsFormat]()

    有关所需的`Layer`内容存储格式的提示。

* [func render(in: CGContext)]()

    将`Layer`及其`Sublayer`渲染到指定的上下文中。

### 修改`Layer`几何形状

* [var frame: CGRect]()

    `Layer`的框架矩形。

* [var bounds: CGRect]()

    `Layer`的边界矩形。可设置动画。

* [var position: CGPoint]()

    `Layer`在其上层坐标空间中的位置。可设置动画。

* [var zPosition: CGFloat]()

    `Layer`在z轴上的位置。可设置动画。

* [var anchorPointZ: CGFloat]()

    `Layer`沿z轴位置的锚点。可设置动画。

* [var anchorPoint: CGPoint]()

    定义`Layer`边界矩形的锚点。可设置动画。

* [var contentsScale: CGFloat]()

    应用于`Layer`的比例因子。

### 管理`Layer`的变换

* [var transform: CATransform3D
The transform applied to the layer’s contents. Animatable.

* [var sublayerTransform: CATransform3D
Specifies the transform to apply to sublayers when rendering. Animatable.

* [func affineTransform() -> CGAffineTransform
Returns an affine version of the layer’s transform.

* [func setAffineTransform(CGAffineTransform)
Sets the layer’s transform to the specified affine transform.

### 管理`Layer`层次结构

* [var sublayers: [CALayer]?]()

    包含`Layer`的`Sublayer`的数组。

* [var superlayer: CALayer?]()

    `Layer`的`Superlayer`。

* [func addSublayer(CALayer)]()

    将`Layer`添加到`Layer`的`Sublayer`列表中。

* [func removeFromSuperlayer()]()

    将`Layer`从其`Superlayer`中分离。

* [func insertSublayer(CALayer, at: UInt32)]()
Inserts the specified layer into the receiver’s list of sublayers at the specified index.

* [func insertSublayer(CALayer, below: CALayer?)]()
Inserts the specified sublayer below a different sublayer that already belongs to the receiver.

* [func insertSublayer(CALayer, above: CALayer?)]()
Inserts the specified sublayer above a different sublayer that already belongs to the receiver.

* [func replaceSublayer(CALayer, with: CALayer)]()
Replaces the specified sublayer with a different layer object.

### 更新`Layer`的显示

* [func setNeedsDisplay()](./1410855-setneedsdisplay.md)

    将`Layer`的内容标记为需要更新。

* [func setNeedsDisplay(CGRect)]()

    将指定矩形内的区域标记为需要更新。

* [var needsDisplayOnBoundsChange: Bool]()

    一个布尔值，指示当其边界矩形更改时是否必须更新图层内容。

* [func displayIfNeeded()](./1410813-displayifneeded.md)

    如果`Layer`当前被标记为需要更新，则启动该`Layer`的更新过程。

* [func needsDisplay() -> Bool](./1410958-needsdisplay.md)

    返回一个布尔值，指示该`Layer`是否已标记为需要更新。

* [class func needsDisplay(forKey: String) -> Bool]()

    返回一个布尔值，指示对指定键的更改是否需要重新显示该`Layer`。

### `Layer`动画

* [func add(CAAnimation, forKey: String?)
Add the specified animation object to the layer’s render tree.

* [func animation(forKey: String) -> CAAnimation?
Returns the animation object with the specified identifier.

* [func removeAllAnimations()
Remove all animations attached to the layer.

* [func removeAnimation(forKey: String)
Remove the animation object with the specified key.

* [func animationKeys() -> [String]?
Returns an array of strings that identify the animations currently attached to the layer.

### 管理`Layer`大小调整和布局

* [var layoutManager: CALayoutManager?
The object responsible for laying out the layer’s sublayers.

* [func setNeedsLayout()
Invalidates the layer’s layout and marks it as needing an update.

* [func layoutSublayers()
Tells the layer to update its layout.

* [func layoutIfNeeded()
Recalculate the receiver’s layout, if required.

* [func needsLayout() -> Bool
Returns a Boolean indicating whether the layer has been marked as needing a layout update.

* [var autoresizingMask: CAAutoresizingMask
A bitmask defining how the layer is resized when the bounds of its superlayer changes.

* [func resize(withOldSuperlayerSize: CGSize)
Informs the receiver that the size of its superlayer changed.

* [func resizeSublayers(withOldSize: CGSize)
Informs the receiver’s sublayers that the receiver’s size has changed.

* [func preferredFrameSize() -> CGSize
Returns the preferred size of the layer in the coordinate space of its superlayer.

### 管理`Layer`约束

* [var constraints: [CAConstraint]?
The constraints used to position current layer’s sublayers.

* [func addConstraint(CAConstraint)
Adds the specified constraint to the layer.

### 获取`Layer`的动作

* [func action(forKey: String) -> CAAction?
Returns the action object assigned to the specified key.

* [var actions: [String : CAAction]?
A dictionary containing layer actions.

* [class func defaultAction(forKey: String) -> CAAction?
Returns the default action for the current class.

### 坐标和时空之间的映射

* [func convert(CGPoint, from: CALayer?) -> CGPoint
Converts the point from the specified layer’s coordinate system to the receiver’s coordinate system.

* [func convert(CGPoint, to: CALayer?) -> CGPoint
Converts the point from the receiver’s coordinate system to the specified layer’s coordinate system.

* [func convert(CGRect, from: CALayer?) -> CGRect
Converts the rectangle from the specified layer’s coordinate system to the receiver’s coordinate system.

* [func convert(CGRect, to: CALayer?) -> CGRect
Converts the rectangle from the receiver’s coordinate system to the specified layer’s coordinate system.

* [func convertTime(CFTimeInterval, from: CALayer?) -> CFTimeInterval
Converts the time interval from the specified layer’s time space to the receiver’s time space.

* [func convertTime(CFTimeInterval, to: CALayer?) -> CFTimeInterval
Converts the time interval from the receiver’s time space to the specified layer’s time space

### 命中测试

* [func hitTest(CGPoint) -> CALayer?
Returns the farthest descendant of the receiver in the layer hierarchy (including itself) that contains the specified point.

* [func contains(CGPoint) -> Bool
Returns whether the receiver contains a specified point.

### 滚动

* [var visibleRect: CGRect
The visible region of the layer in its own coordinate space.

* [func scroll(CGPoint)
Initiates a scroll in the layer’s closest ancestor scroll layer so that the specified point lies at the origin of the scroll layer.

* [func scrollRectToVisible(CGRect)
Initiates a scroll in the layer’s closest ancestor scroll layer so that the specified rectangle becomes visible.

### `Layer`的标识

* [var name: String?
The name of the receiver.

### 键值编码扩展

* [func shouldArchiveValue(forKey: String) -> Bool
Returns a Boolean indicating whether the value of the specified key should be archived.

* [class func defaultValue(forKey: String) -> Any?
Specifies the default value associated with the specified key.

### 常量

* [struct CAAutoresizingMask
These constants are used by the 
autoresizingMask
 property.

* [Action Identifiers
These constants are the predefined action identifiers used by 
action(forKey:)
, 
add(_:forKey:)
, 
defaultAction(forKey:)
, 
removeAnimation(forKey:)
, Layer Filters, and the 
CAAction
 protocol method 
run(forKey:object:arguments:)
.

* [struct CAEdgeAntialiasingMask
This mask is used by the 
edgeAntialiasingMask
 property.

* [Identity Transform
Defines the identity transform matrix used by Core Animation.

* [Scaling Filters
These constants specify the scaling filters used by 
magnificationFilter
 and 
minificationFilter
.

* [struct CATransform3D
The standard transform matrix used throughout Core Animation.

### 实例属性

* [var cornerCurve: CALayerCornerCurve

### 类方法

* [class func cornerCurveExpansionFactor(CALayerCornerCurve) -> CGFloat