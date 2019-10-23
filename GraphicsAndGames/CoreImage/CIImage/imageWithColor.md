# imageWithColor:

创建并返回一个无限大小的图像，其内容为指定颜色。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.5+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithColor:(CIColor *)color;
```

---

## 参数

* **color**

    一个颜色对象。

---

## 返回值

使用[CIColor]()对象表示的颜色初始化的图像对象。


