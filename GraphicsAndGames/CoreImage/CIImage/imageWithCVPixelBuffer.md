# imageWithCVPixelBuffer:

从[CVPixelBuffer]()对象的内容创建并返回一个图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.11+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithCVPixelBuffer:(CVPixelBufferRef)pixelBuffer;
```

---

## 参数

* **pixelBuffer**

    一个[CVPixelBuffer]()对象。

---

## 返回值

使用图像缓冲区对象的内容初始化的图像对象。

