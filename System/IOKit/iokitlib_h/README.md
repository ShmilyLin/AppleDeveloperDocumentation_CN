# IOKitLib.h

## 概述

`IOKitLib`实现了对常见`IOKit`对象类型（`IORegistryEntry`，`IOService`，`IOIterator`等）的非内核任务访问。这些函数是通用的-家族可以提供更具体的API。

`IOKitLib`代表内核外部的`IOKit`对象，其类型为`io_object_t`，`io_registry_entry_t`，`io_service_t`和`io_connect_t`。函数名称通常以它们兼容的对象类型开头——例如，`IOObjectRelease`可以与任何`io_object_t`一起使用。在内核内部，c++类层次结构允许每种对象类型的子类接收来自用户级别客户端的相同请求，例如在内核中，`IOService`是`IORegistryEntry`的子类，这意味着可以使用`IOKitLib`中的任何`IORegistryEntryXXX`函数与`io_service_t`和`io_registry_t`一起使用。`io_object_t`等任何人都可以使用函数来内省内核对象的类。代表。所有函数返回的`IOKit`对象应与`IOObjectRelease`一起释放。

IOKitLib implements non-kernel task access to common IOKit object types - IORegistryEntry, IOService, IOIterator etc. These functions are generic - families may provide API that is more specific.

IOKitLib represents IOKit objects outside the kernel with the types io_object_t, io_registry_entry_t, io_service_t, & io_connect_t. Function names usually begin with the type of object they are compatible with - eg. IOObjectRelease can be used with any io_object_t. Inside the kernel, the c++ class hierarchy allows the subclasses of each object type to receive the same requests from user level clients, for example in the kernel, IOService is a subclass of IORegistryEntry, which means any of the IORegistryEntryXXX functions in IOKitLib may be used with io_service_t's as well as io_registry_t's. There are functions available to introspect the class of the kernel object which any io_object_t et al. represents. IOKit objects returned by all functions should be released with IOObjectRelease.