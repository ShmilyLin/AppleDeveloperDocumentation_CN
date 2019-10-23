# initWithBitmapData:bytesPerRow:size:format:colorSpace:

使用位图数据初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithBitmapData:(NSData *)data 
                       bytesPerRow:(size_t)bytesPerRow 
                              size:(CGSize)size 
                            format:(CIFormat)format 
                        colorSpace:(CGColorSpaceRef)colorSpace;
```

```swift
/* Swift */
init(bitmapData data: Data, 
         bytesPerRow: Int, 
                size: CGSize, 
              format: CIFormat, 
          colorSpace: CGColorSpace?)
```

---

## 参数

* **data**

    图像的位图数据。该数据必须预乘(premultiplied)。

* **bytesPerRow**

    每行的字节数。

* **size**

    图像的尺寸

* **format**

    像素格式常量。请参阅[像素格式]()。

* **colorSpace**

    定义图像的颜色空间。它必须是Quartz 2D颜色空间（[CGColorSpaceRef]()）。对于不包含颜色数据的图像（例如高程图(elevation maps)，法线矢量图(normal vector maps)和采样函数表(sampled function tables)）请传`nil`。

---

## 返回值

初始化的图像对象。

