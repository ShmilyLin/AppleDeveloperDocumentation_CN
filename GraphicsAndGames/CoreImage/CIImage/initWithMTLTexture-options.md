# initWithMTLTexture:options:

使用一个Metal纹理(Metal Texture)提供的数据初始化图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 9.0+ |
| macOS | 10.11+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (instancetype)initWithMTLTexture:(id<MTLTexture>)texture 
                           options:(NSDictionary<CIImageOption, id> *)options;
```

```swift
/* Swift */
init?(mtlTexture texture: MTLTexture, 
                 options: [CIImageOption : Any]? = nil)
```

---

## 参数

* **texture**

    用于使用图像数据的Metal纹理(Metal Texture)。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）

---

## 返回值

初始化的图像对象，如果对象不能够被初始化会返回`nil`。

---

## 描述

要使用Metal渲染，请将此图像与使用[contextWithMTLDevice:]()方法创建的基于Metal的[CIContext]()对象一起使用，并调用[render:toMTLTexture:commandBuffer:bounds:colorSpace:]()方法在另一个Metal纹理(Metal Texture)对象中创建输出图像。
