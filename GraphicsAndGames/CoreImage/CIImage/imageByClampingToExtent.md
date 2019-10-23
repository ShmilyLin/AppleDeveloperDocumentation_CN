# imageByClampingToExtent

返回一个 通过使沿其边缘的像素颜色在所有方向上无限延伸 而创建的新图像。

| SDK | Version |
|:---:|:---:|
| iOS | 8.0+ |
| macOS | 10.10+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByClampingToExtent;
```

```swift
/* Swift */

```

---

## 返回值

一个表示堆(Clamp)操作结果的图像对象。

---

## 说明

调用此方法相当于使用[CIAffineClamp]()过滤器(Filter)，该过滤器(Filter)通过重复原始图像边缘的像素颜色来创建无限范围的图像。

将图像用作其他过滤器(Filter)的输入时，此操作非常有用。当图像具有有限范围时，Core Image会将范围外的区域视为填充空（黑色，零透明度(Alpha)）像素。如果应用从图像范围外采样的过滤器(Filter)，则这些空像素会影响过滤器(Filter)的结果。

例如，将[CIGaussianBlur]()过滤器(Filter)应用于图像会使模糊图像的边缘变得柔和，因为图像边缘处的不透明像素会模糊到图像范围之外的透明像素中。在模糊过滤器(Filter)之前应用堆效果(Clamp Effect)可通过使原始图像在所有方向上不透明来避免边缘柔化。 （但是，模糊的图像也将具有无限的范围。使用[imageByCroppingToRect:](./imageByCroppingToRect.md)方法返回原始图像的尺寸，同时保留硬边。）
