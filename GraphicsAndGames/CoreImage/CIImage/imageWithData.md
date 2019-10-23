# imageWithData:

创建并返回使用提供的图像数据初始化的图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithData:(NSData *)data;
```

---

## 参数

* **data**

    保存图像文件内容的数据对象（例如TIFF，GIF，JPG或系统支持的任何其他内容）。图像数据必须预乘(premultiplied)。

---

## 返回值

使用提供的数据初始化的图像对象，如果方法无法从提供的数据对象的内容创建图像对象，则返回`nil`。