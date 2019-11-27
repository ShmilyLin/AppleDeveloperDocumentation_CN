# 关于偏好设置和设置

偏好设置是你永久存储并用于配置应用程序的信息。应用程序需要向用户公开偏好设置，以便他们可以自定义应用程序的外观和行为。大多数偏好设置是使用Cocoa偏好设置系统（称为用户默认系统）本地存储的。应用程序还可以使用键值存储将偏好设置存储在用户的iCloud帐户中。

用户默认系统和键值存储库都设计为在属性列表中存储简单数据类型（字符串，数字，日期，布尔值，URL，数据对象等）。使用属性列表还意味着你可以使用数组和字典类型来组织你的偏好设置数据。通过将其他对象首先编码为NSData对象，也可以将它们存储在属性列表中。

## 初识

应用程序以多种方式集成偏好设置，包括以编程方式在代码的各个点以及作为用户界面的一部分。iOS和Mac应用程序均支持偏好设置。

### 你决定要显示的偏好设置

每个应用程序的偏好设置都不同，并且由你决定要使应用程序的哪些部分可配置。配置涉及从代码中检查存储的偏好设置的值，并根据该值采取措施。因此，偏好设置值本身应始终简单，并具有特定含义，然后由你的应用实现。

> **相关部分：**[什么是良好的偏好设置？](./AboutTheUserDefaultsSystem.md)

### 应用程序提供自己的偏好设置界面

由于每个应用程序的偏好设置都不相同，因此应用程序本身负责决定如何最好地向用户呈现这些偏好设置。iOS和OS X都为你提供了一些整合偏好设置界面的标准位置，但是你仍然负责设计该界面并在适当的时间显示它。

> **相关部分：**[提供偏好设置界面](./AboutTheUserDefaultsSystem.md)

### 使用用户默认对象的Apps访问偏好设置

应用程序使用用户默认对象（它是[NSUserDefaults]()对象（iOS和OS X）或[NSUserDefaultsController]()对象（仅OS X））访问本地存储的偏好设置。除了检索偏好设置的值外，应用程序还可以使用此对象注册偏好设置的默认值并管理偏好设置系统的其他方面。

> **相关章节：**[访问偏好设置的值]()

### iCloud存储共享的偏好设置和配置数据

支持iCloud的应用程序可以将其某些偏好设置数据放入用户的iCloud帐户中，并使该数据可供在用户其他设备上运行的应用程序实例使用。你可以使用此功能来补充（而不是替换）应用程序的现有偏好设置数据，并在用户的设备上提供更一致的体验。 例如，杂志应用程序可能存储有关页码的信息，并由用户最后一次阅读该刊物，以便在其他设备上运行的应用程序可以显示同一页面。

> **相关章节：**[在iCloud中存储偏好设置]()

### 默认值在OS X中按域分组

OS X中偏好设置按域分组，因此可以将系统偏好设置与应用程序偏好设置区分开。以这种方式拆分首选项可使用户全局指定一些偏好设置，然后在应用程序内覆盖这些偏好设置中的一个或多个。

>**相关部分：**[偏好设置的组织]()

### 设置Bundle管理iOS应用的偏好设置

iOS应用可以显示“设置”应用中的偏好设置，这是放置用户不需要经常配置的偏好设置的好地方。要在“设置”应用中显示偏好设置，应用程序的Bundle必须包含特殊资源——名为“Settings”的Bundle，该资源定义了要显示的偏好设置，正确的显示方式以及记录用户选择内容所需的信息。

> **注意：**应用程序不需要使用Settings Bundle来管理所有偏好设置。对于用户可能会经常更改的偏好设置，应用程序可以显示其自己的自定义界面来管理这些偏好设置。

> **相关章节：**[实现iOS的Settings Bundle]()

---

## 其他推荐

有关属性列表的信息，请参见[属性列表编程指南]()。

有关使用Core Foundation管理偏好设置的更多高级信息，请参阅[Core Foundation的偏好设置编程 的主题]()。