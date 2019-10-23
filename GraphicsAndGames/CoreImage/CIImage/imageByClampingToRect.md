# imageByClampingToRect:

返回一个 通过裁剪到指定区域，然后沿着裁剪图像的边缘使像素颜色在所有方向上无限延伸 而创建的新图像。

| SDK | Version |
|:---:|:---:|
| iOS | 10.0+ |
| macOS | 10.12+ |
| tvOS | 10.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByClampingToRect:(CGRect)rect;
```

```swift
/* Swift */

```

---

## 参数

* **rect**

     图像坐标中用于裁剪图像的矩形。

---

## 返回值

一个表示堆(Clamp)操作结果的图像对象。

---

## 说明

调用此方法相当于裁剪图像（使用[imageByCroppingToRect:](./imageByCroppingToRect.md)方法或[CICrop]()过滤器(Filter)），然后使用[imageByClampingToExtent](./imageByClampingToExtent.md)方法（或[CIAffineClamp]()过滤器(Filter)），该方法通过重复裁 剪边缘的像素颜色 来创建无限范围的图像。
