# initWithIOSurface:options:

使用指定的选项初始化具有IOSurface内容的图像。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.6+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithIOSurface:(IOSurfaceRef)surface 
                          options:(NSDictionary<CIImageOption, id> *)options;
```

```swift
/* Swift */
init(ioSurface surface: IOSurfaceRef, 
               options: [CIImageOption : Any]? = nil)
```

---

## 参数

* **surface**

    一个IOSurface对象

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）
    
---

## 返回值

使用IOSurface对象中的数据初始化的图像对象。
