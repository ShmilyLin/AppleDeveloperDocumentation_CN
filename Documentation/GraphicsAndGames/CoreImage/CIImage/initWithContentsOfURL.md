# initWithContentsOfURL:

通过从URL读取图像来初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithContentsOfURL:(NSURL *)url;
```

```swift
/* Swift */
init?(contentsOf url: URL)
```

---

## 参数

* **url**

    要读取的图片文件的位置。

---

## 返回值

初始化的图像对象，如果对象不能够被初始化会返回`nil`。