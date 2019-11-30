# imageWithImageProvider:size::format:colorSpace:options:

创建并返回由图像提供程序提供的数据初始化的图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 9.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithImageProvider:(id)p 
                               size:(size_t)width 
                                   :(size_t)height 
                             format:(CIFormat)f 
                         colorSpace:(CGColorSpaceRef)cs 
                            options:(NSDictionary<NSString *,id> *)options;
```

---

## 参数

* **p**

    实现[CIImageProvider]()非正式协议的数据提供程序。Core Image会维护对此对象的强引用，直到图像被释放。

* **width**

    图像的宽度

* **height**

    图像的高度

* **f**

    像素格式常量。请参阅[像素格式]()。

* **cs**

    定义图像的颜色空间。如果此值为`nil`，则图像不会进行颜色匹配。对于不包含颜色数据的图像（例如高程图(elevation maps)，法线矢量图(normal vector maps)和采样函数表(sampled function tables)）请传入`nil`。

* **options**

    一个指定图像创建选项的字典，`kCIImageProviderTileSize`或`kCIImageProviderUserInfo`。 有关这些选项的更多信息，请参阅[CIImageProvider]()。

---

## 返回值

使用数据提供程序中的数据初始化的图像对象。在对象需要数据之前，Core Image不会填充图像对象。