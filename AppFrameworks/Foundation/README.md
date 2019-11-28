# Foundation

访问为你的应用定义基础层功能的基本数据类型，集合和操作系统服务。

## 概述

Foundation框架为App和其他框架提供了基础功能，包括数据存储和数据持久化，文本处理，日期和时间计算，排序和筛选以及联网功能。由Foundation定义的类，协议和数据类型在整个macOS，iOS，watchOS和tvOS SDK中通用。

## 主题

### 一、基本

#### ● [数字，数据和基本值]()
Work with primitive values and other fundamental types used throughout Cocoa.

#### ● [字符串和文本]()
Create and process strings of Unicode characters, use regular expressions to find patterns, and perform natural language analysis of text.

#### ● [集合]()
Use arrays, dictionaries, sets, and specialized collections to store and iterate groups of objects or values.

#### ● [日期和时间]()
Compare dates and times, and perform calendar and time zone calculations.

#### ● [单位和尺寸（组件和大小）]()
Label numeric quantities with physical dimensions to allow locale-aware formatting and conversion between related units.

#### ● [数据格式化]()
Convert numbers, dates, measurements, and other values to and from locale-aware string representations.

#### ● [过滤和排序]()
Use predicates, expressions, and sort descriptors to examine elements in collections and other services.

### 二、应用支持

#### ● [任务管理]()

管理你的应用程序的工作及其与系统服务（如“交接”和“快捷方式”）的交互方式。

#### ● [资源]()

访问与你的应用捆绑在一起的资源和其他数据。

#### ● [通知]()
Design patterns for broadcasting information and for subscribing to broadcasts.

#### ● [应用扩展支持]()

管理应用扩展与其托管应用之间的交互。

#### ● [错误和例外]()
Respond to problem situations in your interactions with APIs, and fine-tune your app for better debugging.

#### ● [脚本支持]()
Allow users to control your app with AppleScript and other automation technologies, or run scripts from within your app.

### 三、文件和数据持久化

#### ● [文件系统]()
Create, read, write, and examine files and folders in the file system.

#### ● [档案和序列化](./FilesAndDataPersistence/ArchivesAndSerialization/)

在属性列表、JSON和其他平面二进制表示形式之间来回转换对象和值。

#### ● [Preferences]()
Persistently store domain-scoped pieces of information used to configure your app.

#### ● [Spotlight]()
Search for files and other items on the local device, and index your app's content for searching.

#### ● [iCloud]()
Manage files and key-value data that are automatically synchronized among a user's iCloud devices.

### 四、网络

#### ● [URL加载系统](./URLLoadingSystem/)
Interact with URLs and communicate with servers using standard Internet protocols.

#### ● [Bonjour]()
Advertise services for easy discovery on local networks, or discover services advertised by others.

### 五、Low-Level Utilities

#### ● [XPC]()
Manage secure interprocess communication.

#### ● [对象运行时（Runtime）]()
Get low-level support for basic Objective-C features, Cocoa design patterns, and Swift integration.

#### ● [进程和线程]()
Manage your app's interaction with the host operating system and other processes, and implement low-level concurrency features.

#### ● [Streams, Sockets, and Ports]()
Use low-level Unix features to manage input and output among files, processes, and the network.


### 六、结构体

#### ● [struct NSOrderedCollectionDifferenceCalculationOptions]()

### 七、类

#### ● [class ListFormatter]()
#### ● [class NSOrderedCollectionChange]()
#### ● [class NSOrderedCollectionDifference]()
#### ● [class RelativeDateTimeFormatter]()
#### ● [class NSSecureUnarchiveFromDataTransformer]()
#### ● [class NSXPCCoder]()
#### ● [class URLSessionWebSocketTask]()
#### ● [class UnitInformationStorage]()


### 八、协议

#### ● [protocol ContiguousBytes]()
#### ● [protocol DataProtocol]()
#### ● [protocol MutableDataProtocol]()
#### ● [protocol URLSessionWebSocketDelegate]()


### 九、参考

#### ● [Foundation枚举]()

#### ● [Foundation常量]()

#### ● [Foundation数据类型]()
This document describes the data types and constants found in the Foundation framework.