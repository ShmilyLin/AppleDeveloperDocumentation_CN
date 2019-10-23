# initWithIOSurface:

使用IOSurface的内容初始化图像。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.6+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithIOSurface:(IOSurfaceRef)surface;
```

```swift
/* Swift */
init(ioSurface surface: IOSurfaceRef)
```

---

## 参数

* **surface**

    一个IOSurface对象

---

## 返回值

使用IOSurface对象中的数据初始化的图像对象。

---

## 描述

IOSurface对象是一个帧缓冲对象，适合跨进程边界共享。你可以使用它来允许你的应用 将复杂的图像解压 以及 绘图逻辑移动 到单独的进程中，以提高安全性。
