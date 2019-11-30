# initWithBitmapImageRep:

使用指定的位图图像抽象数据初始化图像对象。

| SDK | Version |
|:---:|:---:|
| macOS | 10.4+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithBitmapImageRep:(NSBitmapImageRep *)bitmapImageRep;
```

```swift
/* Swift */
init?(bitmapImageRep: NSBitmapImageRep)
```

---

## 参数

* **bitmapImageRep**

    包含位图数据的图像抽象对象。

---

## 返回值

初始化的图像对象，如果对象不能够被初始化会返回`nil`。