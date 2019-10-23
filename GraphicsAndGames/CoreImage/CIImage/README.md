# CIImage

由Core Image过滤器(Filter)处理或生成的图像的抽象对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
@interface CIImage : NSObject
```

```swift
/* Swift */

```

---

## 概述

你可以将`CIImage`对象与其他Core Image类（如[CIFilter]()，[CIContext]()，[CIVector]()和[CIColor]()）结合使用，以便在处理图像时利用内置的Core Image过滤器(Filter)。你可以使用从各种来源提供的数据创建`CIImage`对象，包括Quartz 2D图像，Core Video图像缓冲区（[CVImageBufferRef]()），基于URL的对象和[NSData]()对象。

虽然`CIImage`对象具有与之关联的图像数据，但它不是图像。你可以将`CIImage`对象视为图像的“食谱”。`CIImage`对象具有生成图像所需的所有信息，但Core Image实际上不会渲染图像，直到它被告知需要做渲染。这种惰性执行允许Core Image尽可能高效地运行。要将`CIImage`对象显示为屏幕图像，可以在[UIImageView]()中将其显示为[UIImage]()：

```objective-c
/* Objective-C */
// 创建图像的URL NSURL* imageURL = [[NSBundle mainBundle] URLForResource:@"YourJPEGName" withExtension:@"JPG"];

// 加载图像到应用中 CIImage* ciImage = [CIImage imageWithContentsOfURL:imageURL];
     
// 将CIImage转为UIImage UIImage* uiImage = [UIImage imageWithCIImage:ciImage];

// 显示图像
UIImageView* imageView = [[UIImageView alloc] initWithImage:uiImage];

// 务必将imageView作为子视图添加到层次结构中。
[self.view addSubview:imageView];
```

```swift
/* Swift */

```

[CIContext]()和`CIImage`对象是不可变的，这意味着每个对象都可以在线程之间安全地共享。多个线程可以使用相同的`GPU`或`CPU CIContext`对象来呈现`CIImage`对象。但是，对于可变的[CIFilter]()对象，情况并非如此。无法在线程之间安全地共享[CIFilter]()对象。如果你的应用程序是多线程的，则每个线程都必须创建自己的[CIFilter]()对象。否则，你的应用可能会出现意外行为。

Core Image还提供自动调整方法。这些方法分析图像中的常见缺陷，并返回一组过滤器(Filter)来纠正这些缺陷。过滤器(Filter)预设有值，用于通过改变肤色，饱和度，对比度和阴影的值以及消除由闪光引起的红眼或其他伪影来提高图像质量。（请参阅[获取自动调整过滤器]()。）

有关可用于在iOS和macOS上创建`CIImage`对象的所有方法的论述，请参阅[Core Image编程指南](../CoreImageProgrammingGuide/)。

---

## 专题

### 一、创建一个图像

#### ● [+ emptyImage](./emptyImage.md)

创建并返回一个空的图像对象。

#### ● [+ imageWithColor:](./imageWithColor.md)

创建并返回一个无限大小的图像，其内容为指定颜色。

#### ● [+ imageWithBitmapData:bytesPerRow:size:format:colorSpace:](./imageWithBitmapData-bytesPerRow-size-format-colorSpace.md)

通过位图数据（BMP）创建并返回一个图像对象。

#### ● [+ imageWithCGImage:](./imageWithCGImage.md)

通过一个Quartz 2D图像创建并返回一个图像对象。

#### ● [+ imageWithCGImage:options:](./imageWithCGImage-options.md)

使用指定的选项从Quartz 2D图像创建并返回一个图像对象。

#### ● ~~+ imageWithCGLayer:~~

通过一个[CGLayer]()对象提供的内容创建并返回图像对象。

#### ● ~~+ imageWithCGLayer:options:~~

使用指定的选项从CGLayer对象提供的内容创建并返回图像对象。

#### ● [+ imageWithContentsOfURL:](./imageWithContentsOfURL.md)

通过文件内容创建并返回图像对象。

#### ● [+ imageWithContentsOfURL:options:](./imageWithContentsOfURL-options.md)

使用指定的选项通过文件内容创建并返回图像对象。

#### ● [+ imageWithCVImageBuffer:](./imageWithCVImageBuffer.md)

从[CVImageBuffer]()对象的内容创建并返回一个图像对象。

#### ● [+ imageWithCVImageBuffer:options:](./imageWithCVImageBuffer-options.md)

使用指定的选项从[CVImageBuffer]()对象的内容创建并返回一个图像对象。

#### ● [+ imageWithCVPixelBuffer:](./imageWithCVPixelBuffer.md)

从[CVPixelBuffer]()对象的内容创建并返回一个图像对象。

#### ● [+ imageWithCVPixelBuffer:options:](./imageWithCVPixelBuffer-options.md)

使用指定的选项从[CVPixelBuffer]()对象的内容创建并返回一个图像对象。

#### ● [+ imageWithData:](./imageWithData.md)

创建并返回使用提供的图像数据初始化的图像对象。

#### ● [+ imageWithData:options:](./imageWithData-options.md)

使用指定的选项创建并返回使用提供的图像数据初始化的图像对象。

#### ● [+ imageWithImageProvider:size::format:colorSpace:options:](./imageWithImageProvider-size-format-colorSpace-options.md)

创建并返回由图像提供程序提供的数据初始化的图像对象。

#### ● ~~+ imageWithTexture:size:flipped:colorSpace:~~

创建并返回使用OpenGL纹理提供的数据初始化的图像对象。

#### ● ~~+ imageWithTexture:size:flipped:options:~~

创建并返回使用OpenGL纹理提供的数据初始化的图像对象。

#### ● [+ imageWithMTLTexture:options:](./imageWithMTLTexture-options.md)

使用Metal纹理(Metal Texture)提供的数据创建并返回图像对象。

#### ● [+ imageWithIOSurface:](./imageWithIOSurface.md)

从IOSurface的内容创建并返回图像。

#### ● [+ imageWithIOSurface:options:](./imageWithIOSurface-options.md)

使用指定的选项创建，并从IOSurface的内容返回图像。


### 二、初始化一个图像

#### ● [- initWithColor:](./initWithColor.md)

初始化无限范围的图像，其整个内容是指定的颜色。

#### ● [- initWithBitmapData:bytesPerRow:size:format:colorSpace:](./initWithBitmapData-bytesPerRow-size-format-colorSpace.md)

使用位图数据初始化图像对象。

#### ● [- initWithCGImage:](./initWithCGImage.md)

使用Quartz 2D图像初始化图像对象。

#### ● [- initWithCGImage:options:](./initWithCGImage-options.md)

使用指定选项通过Quartz 2D图像初始化图像对象。

#### ● [- initWithBitmapImageRep:](./initWithBitmapImageRep.md)

使用指定的位图图像抽象数据初始化图像对象。

#### ● [- initWithImage:](./initWithImage.md)

使用指定的UIKit图像对象初始化图像对象。

#### ● [- initWithImage:options:](./initWithImage-options.md)

使用指定的选项通过指定的UIKit图像对象初始化图像对象。

#### ● ~~- initWithCGLayer:~~

从[CGLayer]()对象提供的内容初始化图像对象。

#### ● ~~- initWithCGLayer:options:~~

使用指定的选项从[CGLayer]()对象提供的内容初始化图像对象。

#### ● [- initWithContentsOfURL:](./initWithContentsOfURL.md)

通过从URL读取图像来初始化图像对象。

#### ● [- initWithContentsOfURL:options:](./initWithContentsOfURL-options.md)

使用指定的选项通过从URL读取图像来初始化图像对象。

#### ● [- initWithCVImageBuffer:](./initWithCVImageBuffer.md)

从[Core Video]()图像缓冲区的内容初始化图像对象。

#### ● [- initWithCVImageBuffer:options:](./initWithCVImageBuffer-options.md)

使用指定的选项从Core Video图像缓冲区的内容初始化图像对象。

#### ● [- initWithCVPixelBuffer:](./initWithCVPixelBuffer.md)

从[Core Video]()像素缓冲区的内容初始化图像对象。

#### ● [- initWithCVPixelBuffer:options:](./initWithCVPixelBuffer-options.md)

使用指定的选项从[Core Video]()像素缓冲区的内容初始化图像对象。

#### ● [- initWithData:](./initWithData.md)

使用提供的图像数据初始化图像对象。

#### ● [- initWithData:options:](./initWithData-options.md)

使用指定的选项通过提供的图像数据初始化图像对象。

#### ● [- initWithImageProvider:size::format:colorSpace:options:](./initWithImageProvider-size-format-colorSpace-options.md)

使用指定的选项通过图像提供程序提供的数据初始化图像对象。

#### ● [kCIImageProviderTileSize](./kCIImageProviderTileSize.md)

图像拼贴大小的键。关联值是[NSArray]()类型，它包含NSNumber对象，用于从图像提供程序请求的图像切片的尺寸。

#### ● [kCIImageProviderUserInfo](./kCIImageProviderUserInfo.md)

图像提供程序所需数据的键。关联值是包含所需数据的对象。

#### ● ~~- initWithTexture:size:flipped:colorSpace:~~

使用OpenGL纹理(OpenGL Texture)提供的数据初始化图像对象。

#### ● ~~- initWithTexture:size:flipped:options:~~

使用OpenGL纹理(OpenGL Texture)提供的数据初始化图像对象。

#### ● [- initWithMTLTexture:options:](./initWithMTLTexture-options.md)

使用一个Metal纹理(Metal Texture)提供的数据初始化图像对象。

#### ● [- initWithIOSurface:](./initWithIOSurface.md)

使用IOSurface的内容初始化图像。

#### ● [- initWithIOSurface:options:](./initWithIOSurface-options.md)

使用指定的选项初始化具有IOSurface内容的图像。

#### ● ~~- initWithIOSurface:plane:format:options:~~

使用指定的格式和选项初始化具有IOSurface中特定数据平面内容的图像。


### 三、通过修改现有的一个图像创建一个图像

#### ● [- imageByApplyingFilter:withInputParameters:](./imageByApplyingFilter-withInputParameters.md)

返回一个 通过将过滤器(Filter)应用于指定名称和参数的原始图像 而创建的新图像。

#### ● [- imageByApplyingFilter:](./imageByApplyingFilter.md)

将过滤器(Filter)应用于图像并返回输出。

#### ● [- imageByApplyingTransform:](./imageByApplyingTransform.md)

返回一个原始图像应用仿射变换后表示的新图像。

#### ● [- imageByCroppingToRect:](./imageByCroppingToRect.md)

返回一个包含原始图像裁剪部分的新图像。

#### ● [- imageByApplyingOrientation:](./imageByApplyingOrientation.md)

返回一个 通过将原始图像转换为指定的EXIF方向 而创建的新图像。

#### ● [- imageByClampingToExtent](./imageByClampingToExtent.md)

返回一个 通过使沿其边缘的像素颜色在所有方向上无限延伸 而创建的新图像。

#### ● [- imageByClampingToRect:](./imageByClampingToRect.md)

返回一个 通过裁剪到指定区域，然后沿着裁剪图像的边缘使像素颜色在所有方向上无限延伸 而创建的新图像。

#### ● [- imageByCompositingOverImage:](./imageByCompositingOverImage.md)

返回一个 通过在指定目标图像上合成原始图像 而创建的新图像。

#### ● [- imageByColorMatchingColorSpaceToWorkingSpace:]()

返回一个 通过从指定颜色空间到上下文的工作颜色空间的颜色匹配 而创建的新图像。
Returns a new image created by color matching from the specified color space to the context’s working color space.

#### ● [- imageByColorMatchingWorkingSpaceToColorSpace:]()

返回一个 通过颜色匹配从上下文的工作颜色空间到指定颜色空间 而创建的新图像。
Returns a new image created by color matching from the context’s working color space to the specified color space.

#### ● [- imageByPremultiplyingAlpha]()

返回一个 通过将图像的RGB值乘以其Alpha值 而创建的新图像。

#### ● [- imageByUnpremultiplyingAlpha]()

返回一个 通过将图像的RGB值除以其alpha值 而创建的新图像。

#### ● [- imageBySettingAlphaOneInExtent:]()

返回一个 通过将指定矩形内的所有Alpha值设置为1.0并在该区域外设置为0.0 而创建的新图像。

#### ● [- imageByApplyingGaussianBlurWithSigma:]()

返回一个 通过对图像应用高斯模糊过滤器(Filter) 而创建的新图像。

#### ● [- imageBySettingProperties:]()

返回一个 通过将指定的元数据属性添加到图像 而创建的新图像。

#### ● [- imageByInsertingIntermediate]()

返回一个 通过插入一个中间体 而创建的新图像。

#### ● [- imageByInsertingIntermediate:]()

返回一个 通过插入一个可缓存中间体 而创建的新图像。