# imageWithContentsOfURL:options:

使用指定的选项通过文件内容创建并返回图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.4+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithContentsOfURL:(NSURL *)url 
                            options:(NSDictionary<CIImageOption, id> *)options;
```

---

## 参数

* **url**

    文件的位置。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）

---

## 返回值

使用文件内容，并设置了指定选项进行初始化的图像对象。