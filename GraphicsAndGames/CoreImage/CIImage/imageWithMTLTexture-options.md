# imageWithMTLTexture:options:

使用Metal纹理(Metal Texture)提供的数据创建并返回图像对象。

| SDK | Version |
|:---:|:---:|
| iOS | 9.0+ |
| macOS | 10.11+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
+ (CIImage *)imageWithMTLTexture:(id<MTLTexture>)texture 
                         options:(NSDictionary<CIImageOption, id> *)options;
```

---

## 参数

* **texture**

    用于使用图像数据的Metal纹理(Metal Texture)。

* **options**

    一个指定图像选项的字典。（参见[图像字典键]()。）

---

## 返回值

使用纹理(Texture)数据初始化的图像对象。

---

## 描述

要使用Metal渲染，请将此图像与使用[contextWithMTLDevice:]()方法创建的基于Metal的[CIContext]()对象一起使用，并调用[render:toMTLTexture:commandBuffer:bounds:colorSpace:]()方法在另一个Metal纹理(Metal Texture)对象中创建输出图像。
