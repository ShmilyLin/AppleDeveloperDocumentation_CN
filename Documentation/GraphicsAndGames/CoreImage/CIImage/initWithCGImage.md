# initWithCGImage:

使用Quartz 2D图像初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithCGImage:(CGImageRef)image;
```

```swift
/* Swift */
init(cgImage image: CGImage)
```

---

## 参数

* **image**

    一个Quartz 2D图像（[CGImageRef]()）对象。 有关更多信息，请参阅[Quartz 2D编程指南]()和[CGImage]()。

---

## 返回值

初始化的图像对象。

