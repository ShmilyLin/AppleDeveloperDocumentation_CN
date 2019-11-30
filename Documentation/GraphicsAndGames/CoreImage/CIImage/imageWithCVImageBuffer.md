# imageWithCVImageBuffer:

从[CVImageBuffer]()对象的内容创建并返回一个图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithCVImageBuffer:(CVImageBufferRef)imageBuffer;
```

---

## 参数

* **imageBuffer**

    一个[CVImageBuffer]()对象。有关更多信息，请参阅[Core Video编程指南]()和[Core Video]()。

---

## 返回值

使用图像缓冲区对象的内容初始化的图像对象。

