# imageByCompositingOverImage:

返回一个 通过在指定目标图像上合成原始图像 而创建的新图像。

| SDK | Version |
|:---:|:---:|
| iOS | 8.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByCompositingOverImage:(CIImage *)dest;
```

```swift
/* Swift */

```

---

## 参数

* **dest**

    一个用作合成操作目标的图像。

---

## 返回值

一个表示合成操作结果的图像对象。

---

## 说明

调用此方法等同于使用[CISourceOverCompositing]()过滤器。要使用其他合成操作和混合模式，请使用[CICategoryCompositeOperation]()类别中的一个内置过滤器(Filter)创建[CIFilter]()对象。有关详细信息，请参阅[Core Image过滤器(Filter)参考]()。
