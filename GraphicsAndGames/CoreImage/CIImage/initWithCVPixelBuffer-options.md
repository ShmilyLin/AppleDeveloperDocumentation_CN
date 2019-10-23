# initWithCVPixelBuffer:options:

使用指定的选项从[Core Video]()像素缓冲区的内容初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.11+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithCVPixelBuffer:(CVPixelBufferRef)pixelBuffer 
                              options:(NSDictionary<CIImageOption, id> *)options;
```

```swift
/* Swift */
init(cvPixelBuffer pixelBuffer: CVPixelBuffer, 
                       options: [CIImageOption : Any]? = nil)
```

---

## 参数

* **pixelBuffer**

    一个[CVPixelBuffer]()对象。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。像素格式由[CVPixelBuffer]()对象提供。）
---

## 返回值

初始化的图像对象。