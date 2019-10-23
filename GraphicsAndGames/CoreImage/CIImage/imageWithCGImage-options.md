# imageWithCGImage:options:

使用指定的选项从Quartz 2D图像创建并返回一个图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.5+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithCGImage:(CGImageRef)image 
                      options:(NSDictionary<CIImageOption, id> *)options;
```

---

## 参数

* **image**

    一个Quartz 2D图像（[CGImageRef]()）对象。 有关更多信息，请参阅[Quartz 2D编程指南]()和[CGImage]()。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）

---

## 返回值

使用Quartz 2D图像的内容和指定的选项初始化的图像对象。