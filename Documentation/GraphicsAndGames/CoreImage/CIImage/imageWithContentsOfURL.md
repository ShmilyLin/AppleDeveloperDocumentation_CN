# imageWithContentsOfURL:

通过文件内容创建并返回图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithContentsOfURL:(NSURL *)url;
```

---

## 参数

* **url**

    文件的位置。

---

## 返回值

使用文件内容初始化的图像对象。