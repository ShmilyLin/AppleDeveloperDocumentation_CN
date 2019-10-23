# imageWithCVPixelBuffer:options:

使用指定的选项从[CVPixelBuffer]()对象的内容创建并返回一个图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.11+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithCVPixelBuffer:(CVPixelBufferRef)pixelBuffer 
                            options:(NSDictionary<CIImageOption, id> *)options;
```

---

## 参数

* **pixelBuffer**

    一个[CVPixelBuffer]()对象。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）
---

## 返回值

使用图像缓冲区对象的内容初始化的图像对象。