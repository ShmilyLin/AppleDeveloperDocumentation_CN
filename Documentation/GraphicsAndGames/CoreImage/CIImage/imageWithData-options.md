# imageWithData:options:

使用指定的选项创建并返回使用提供的图像数据初始化的图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithData:(NSData *)data 
                   options:(NSDictionary<CIImageOption, id> *)options;
```

---

## 参数

* **data**

    指向图像数据的指针。图像数据必须预乘(premultiplied)。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）

---

## 返回值

使用提供的数据初始化的图像对象，并使用指定的选项进行设置。