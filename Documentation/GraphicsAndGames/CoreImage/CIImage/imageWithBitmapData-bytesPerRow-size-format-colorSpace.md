# imageWithBitmapData:bytesPerRow:size:format:colorSpace:

通过位图数据（BMP）创建并返回一个图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithBitmapData:(NSData *)data 
                     bytesPerRow:(size_t)bytesPerRow 
                            size:(CGSize)size 
                          format:(CIFormat)format 
                      colorSpace:(CGColorSpaceRef)colorSpace;
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

    每个像素的格式和大小。你必须提供像素格式常量。请参阅[像素格式]()。

* **colorSpace**

    定义图像的颜色空间。如果此值为`nil`，则图像不会匹配颜色。对于不包含颜色数据的图像（例如高程图(elevation maps)，法线矢量图(normal vector maps)和采样函数表(sampled function tables)）请传`nil`。

---

## 返回值

一个图像对象。

