# IODataQueueClient.h

## 概述

### 引用的头文件

* <sys/cdefs.h>

* <AvailabilityMacros.h>

* <libkern/OSTypes.h>

* <mach/port.h>

* <IOKit/IOReturn.h>

* <IOKit/IODataQueueShared.h>

## 主题

### 杂项

* [func IODataQueueAllocateNotificationPort() -> mach_port_t]()

    分配并返回一个新的mach端口，该端口可以从IODataQueue接收可用数据的通知。

* [func IODataQueueDataAvailable(UnsafeMutablePointer<IODataQueueMemory>!) -> Bool]()

    用于确定队列上是否有更多数据。

* [func IODataQueueDequeue(UnsafeMutablePointer<IODataQueueMemory>!, UnsafeMutableRawPointer!, UnsafeMutablePointer<UInt32>!) -> IOReturn]()

    使队列中的下一个可用条目出队，并将其复制到给定的数据指针中。

* [func IODataQueueEnqueue(UnsafeMutablePointer<IODataQueueMemory>!, UnsafeMutableRawPointer!, UInt32) -> IOReturn]()

    使新条目进入队列。

* [func IODataQueuePeek(UnsafeMutablePointer<IODataQueueMemory>!) -> UnsafeMutablePointer<IODataQueueEntry>!]()

    用于窥视队列中的下一个条目。

* [func IODataQueueSetNotificationPort(UnsafeMutablePointer<IODataQueueMemory>!, mach_port_t) -> IOReturn]()

    创建一个简单的mach消息，以port中指定的mach端口为目标。

* [func IODataQueueWaitForAvailableData(UnsafeMutablePointer<IODataQueueMemory>!, mach_port_t) -> IOReturn]()

    在给定的notifyPort上等待传入dataAvailable消息。