# imageByApplyingFilter:

将过滤器(Filter)应用于图像并返回输出。

| SDK | Version |
|:---:|:---:|
| iOS | 11.0+ |
| macOS | 10.13+ |
| tvOS | 11.0+ |

---

## 声明

```objective-c
/* Objective-C */
- (CIImage *)imageByApplyingFilter:(NSString *)filterName;
```

```swift
/* Swift */

```

---

## 描述

一种便捷的方法，用于将单个过滤器(Filter)应用于方法接收器并返回输出图像。与使用默认参数[imageByApplyingFilter:withInputParameters:](./imageByApplyingFilter-withInputParameters.md)方法相同。

> **重要**
> 
> 该方法虽然方便，但如果连续多次使用是低效率的。通过链接过滤器(Filter)可以实现更好的性能，并且无需考虑各个过滤器的输出。

---

## 返回值

返回一个图像对象。