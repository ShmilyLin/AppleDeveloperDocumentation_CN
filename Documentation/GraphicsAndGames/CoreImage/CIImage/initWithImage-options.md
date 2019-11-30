# initWithImage:options:

使用指定的选项通过指定的UIKit图像对象初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithImage:(UIImage *)image 
                      options:(NSDictionary<CIImageOption, id> *)options;
```

```swift
/* Swift */
init?(image: UIImage, 
    options: [CIImageOption : Any]? = nil)
```

---

## 参数

* **image**

    包含源数据的图像。

* **options**

    包含用于创建图像对象的选项的字典。你可以提供像素格式和颜色空间等选项。请参见[图像字典键]()。

---

## 返回值

初始化的图像对象，如果对象不能够被初始化会返回`nil`。