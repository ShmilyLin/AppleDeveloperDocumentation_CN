# imageByApplyingFilter:withInputParameters:

返回 通过将过滤器(Filter)应用于指定名称和参数的原始图像 而创建的新图像。

| SDK | Version |
|:---:|:---:|
| iOS | 5.0+ |
| macOS | 10.5+ |
| tvOS | 9.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByApplyingFilter:(NSString *)filterName 
               withInputParameters:(NSDictionary<NSString *,id> *)params;
```

```swift
/* Swift */

```

---

## 参数

* **filterName**

    要应用的过滤器(Filter)的名称，同使用[filterWithName:]()方法创建[CIFilter]()实例时使用的一样。

* **params**

    将键值对设置为过滤器(Filter)的输入值的字典。每个键都是一个常量，它指定过滤器(Filter)的输入参数的名称，相应的值是该参数的值。有关内置过滤器(Filter)及其允许的参数，请参阅[Core Image过滤器(Filter)参考]()。

---

## 返回值

一个表示应用过滤器(Filter)结果的图像对象。

## 说明

调用此方法等效于以下步骤：

1. 创建一个[CIFilter]()实例。

2. 设置原始图像作为过滤器(Filter)的`inputImage`参数的值。

3. 通过`params`字典设置过滤器(Filter)的其他参数。

4. 从过滤器(Filter)的[outputImage]()属性对象获取结果。

> **重要**
>
> 该方法虽然方便，但如果连续多次使用是低效率的。通过链接过滤器(Filter)可以实现更好的性能，并且无需考虑各个过滤器的输出。