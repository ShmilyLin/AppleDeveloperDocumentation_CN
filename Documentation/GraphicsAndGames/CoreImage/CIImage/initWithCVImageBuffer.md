# initWithCVImageBuffer:

从Core Video图像缓冲区的内容初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 9.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithCVImageBuffer:(CVImageBufferRef)imageBuffer;
```

```swift
/* Swift */
init(cvImageBuffer imageBuffer: CVImageBuffer)
```

---

## 参数

* **imageBuffer**

    一个支持的像素格式常量的[CVImageBuffer]()对象。有关更多信息，请参阅[Core Video编程指南]()和[Core Video]()。

---

## 返回值

初始化的图像对象。

---

## 描述

`imageBuffer`参数必须是以下格式中的一个：

* [kCVPixelFormatType_32ARGB]()

* [kCVPixelFormatType_422YpCbCr8]()

* [kCVPixelFormatType_32BGRA]()