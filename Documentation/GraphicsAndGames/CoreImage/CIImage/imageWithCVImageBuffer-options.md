# imageWithCVImageBuffer:options:

使用指定的选项从[CVImageBuffer]()对象的内容创建并返回一个图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithCVImageBuffer:(CVImageBufferRef)imageBuffer 
                            options:(NSDictionary<CIImageOption, id> *)options;
```

---

## 参数

* **imageBuffer**

    一个[CVImageBuffer]()对象。有关更多信息，请参阅[Core Video编程指南]()和[Core Video]()。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）

---

## 返回值

使用图像缓冲区对象的内容，并设置了指定选项进行初始化的图像对象。
