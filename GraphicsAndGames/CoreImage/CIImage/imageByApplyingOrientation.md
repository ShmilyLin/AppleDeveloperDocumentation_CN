# imageByApplyingOrientation:

返回一个 通过将原始图像转换为指定的EXIF方向 而创建的新图像。

| SDK | Version |
|:---:|:---:|
| iOS | 8.0+ |
| macOS | 10.10+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByApplyingOrientation:(int)orientation;
```

```swift
/* Swift */

```

---

## 参数

* **orientation**

    一个整数，根据EXIF规范指定图像方向。有关详细信息，请参阅[kCGImagePropertyOrientation]()。

---

## 返回值

一个表示将图像旋转或镜像到目标方向的结果的图像对象。

---

## 说明

此方法确定然后应用将图像重定向到指定方向所需的转换。如果你还计划应用其他转换，则可以通过调用[imageTransformForOrientation:](./imageTransformForOrientation.md)方法来检索此方法将使用的转换。

