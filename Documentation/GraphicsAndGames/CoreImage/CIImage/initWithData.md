# initWithData:

使用提供的图像数据初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithData:(NSData *)data;
```

```swift
/* Swift */
init?(data: Data)
```

---

## 参数

* **data**

    图像数据。图像数据必须预乘(premultiplied)。

---

## 返回值

初始化的图像对象，如果对象不能够被初始化会返回`nil`。