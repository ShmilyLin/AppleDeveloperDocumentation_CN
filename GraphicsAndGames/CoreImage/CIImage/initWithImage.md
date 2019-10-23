# initWithImage:

使用指定的UIKit图像对象初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithImage:(UIImage *)image;
```

```swift
/* Swift */
init?(image: UIImage)
```

---

## 参数

* **image**

    包含源数据的图像。

---

## 返回值

初始化的图像对象，如果对象不能够被初始化会返回`nil`。