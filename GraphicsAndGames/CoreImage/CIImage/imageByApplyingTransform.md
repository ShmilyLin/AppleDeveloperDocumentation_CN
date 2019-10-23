# imageByApplyingTransform:

返回一个原始图像应用仿射变换后表示的新图像。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByApplyingTransform:(CGAffineTransform)matrix;
```

```swift
/* Swift */

```

---

## 参数

* **matrix**

    一个仿射变换

---

## 返回值

一个变换后的图像对象。