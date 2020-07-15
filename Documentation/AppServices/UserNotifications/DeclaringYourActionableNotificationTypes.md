# 声明你允许使用的通知类型

区分你的通知，并将操作按钮添加到通知界面。

## 概述

可操作的通知使用户无需启动相应的应用程序即可响应已发送的通知。其他通知会在通知界面中显示信息，但是用户唯一的操作方法是启动应用程序。对于可操作的通知，系统除显示通知界面外，还显示一个或多个按钮。 轻击按钮会将选定的动作发送到应用程序，然后该应用程序在后台处理该动作。

要支持可行的通知，你必须：

* 在启动时从你的iOS应用声明一个或多个通知类别。
* 将适当的操作分配给你的通知类别。
* 处理你注册的所有操作。
* 生成通知时，将`category`标识符分配给通知有效负载。

> **注意**
>
> 系统还使用`category`来确定是启动通知服务应用扩展还是通知内容应用扩展。有关如何创建Notification Service应用程序扩展的信息，请参阅[在新发送的通知中修改内容](#)。有关如何创建通知内容应用程序扩展的信息，请参阅[自定义通知的外观](#)。

### 声明您的自定义操作和通知类型

因为你的应用程序必须处理所有操作，所以你必须在启动时声明应用程序支持的操作。你可以使用`category`和`action`对象的组合来声明操作。[UNNotificationCategory](./UNNotificationCategory/)对象定义你的应用程序支持的通知类型，[UNNotificationAction](./UNNotificationAction/)对象定义每种类型显示的按钮。例如，会议邀请的通知可能包括接受或拒绝邀请的按钮。

每个[UNNotificationCategory](./UNNotificationCategory/)对象都有一个唯一的标识符和用于处理该类型通知的选项。标识符属性中的字符串是`category`对象的最重要部分。生成通知时，必须在通知的有效负载中包含相同的字符串。系统使用该字符串来找到相应的`category`对象和对应的操作。

要将操作与通知类别关联，请为其分配一个或多个[UNNotificationAction](./UNNotificationAction/)对象。每个`action`对象都包含要向用户显示的本地化字符串和指示你要如何处理该操作的选项。例如，当你将一个动作标记为破坏性动作时，系统会以不同的高亮显示该动作以指示其行为。

下面代码显示了如何通过两个操作来注册自定义类别。除了标题和选项外，每个动作还具有唯一的标识符。当用户选择操作时，系统会将该标识符传递给你的应用。

```swift
// Define the custom actions.
let acceptAction = UNNotificationAction(identifier: "ACCEPT_ACTION",
      title: "Accept", 
      options: UNNotificationActionOptions(rawValue: 0))
let declineAction = UNNotificationAction(identifier: "DECLINE_ACTION",
      title: "Decline", 
      options: UNNotificationActionOptions(rawValue: 0))
// Define the notification type
let meetingInviteCategory = 
      UNNotificationCategory(identifier: "MEETING_INVITATION",
      actions: [acceptAction, declineAction], 
      intentIdentifiers: [], 
      hiddenPreviewsBodyPlaceholder: "",
      options: .customDismissAction)
// Register the notification type.
let notificationCenter = UNUserNotificationCenter.current()
notificationCenter.setNotificationCategories([meetingInviteCategory])
```

> **重要**
>
> 你所有的`action`对象都必须具有唯一的标识符。 在处理动作时，标识符是区分一个动作与另一个动作的唯一方法，即使这些动作属于不同的类别。

大多数操作只是允许用户选择，但是文本输入操作也允许用户键入基于文本的自定义响应。然后，你的应用可以将用户键入的响应传递到你对操作的处理中。例如，消息传递应用程序可以将键入的文本作为对传入消息的响应进行发送。 若要创建文本输入操作，请创建[UNTextInputNotificationAction]()对象而不是[UNNotificationAction]()对象。 当用户点击按钮进行文本输入操作时，系统将显示一个可编辑的文本字段。向你的应用报告操作时，系统会包含用户键入的文本作为响应的一部分。

### 在有效负载中包括通知类别

系统仅针对其有效负载包含有效类别标识符字符串的通知显示其对应的操作。系统使用类别标识符来查找你应用程序的已注册的类别及其相关操作。然后，它使用该信息将操作按钮添加到通知界面。

要将类别分配给本地通知，请将适当的字符串分配给[UNMutableNotificationContent](#)对象的[categoryIdentifier](#)属性。 下面代码显示了本地通知内容的创建。 除了基本信息之外，此代码还将自定义数据添加到通知的[userInfo](#)字典中，以供以后处理邀请。

```swift
let content = UNMutableNotificationContent()
content.title = "Weekly Staff Meeting"
content.body = "Every Tuesday at 2pm"
content.userInfo = ["MEETING_ID" : meetingID, 
                    "USER_ID" : userID ]
content.categoryIdentifier = "MEETING_INVITATION"
```

要将类别标识符添加到远程通知中，请在JSON有效负载的aps字典中包括`category`关键字，如下面代码所示。将此关键字的值设置为适当的类别字符串。在示例中，类别设置为与先前定义的会议邀请类别相同。与本地通知示例一样，有效负载包括带有会议ID和用户ID的自定义键，这些自定义键被放入有效负载的[userInfo](#)字典中。 该应用可以使用该信息来接受或拒绝邀请。

```json
{
   “aps” : {
      “category” : “MEETING_INVITATION”
      “alert” : {
         “title” : “Weekly Staff Meeting”
         “body” : “Every Tuesday at 2pm”
      },
   },
   “MEETING_ID” : “123456789”,
   “USER_ID” : “ABCD1234”

} 
```

### 处理选定的操作

你的应用必须处理其定义的所有操作。 当用户选择一个操作时，系统会在后台启动你的应用程序，并通知共享的[UNUserNotificationCenter](./UNUserNotificationCenter/)对象，该对象将通知其`delegate`。使用`delegate`对象的[userNotificationCenter(_:didReceive:withCompletionHandler:)](#)方法来标识选定的操作并提供适当的响应。

下面的代码显示了用于管理会议邀请的应用程序的`delegate`方法的实现。该方法使用响应的[actionIdentifier](#)属性来确定是接受还是拒绝给定邀请。它还依靠来自通知有效负载的自定义数据来成功处理通知。完成操作后，请始终调用完成处理程序。

```swift
func userNotificationCenter(_ center: UNUserNotificationCenter,
       didReceive response: UNNotificationResponse,
       withCompletionHandler completionHandler: 
         @escaping () -> Void) {
       
   // Get the meeting ID from the original notification.
   let userInfo = response.notification.request.content.userInfo
   let meetingID = userInfo["MEETING_ID"] as! String
   let userID = userInfo["USER_ID"] as! String
        
   // Perform the task associated with the action.
   switch response.actionIdentifier {
   case "ACCEPT_ACTION":
      sharedMeetingManager.acceptMeeting(user: userID, 
                                    meetingID: meetingID)
      break
        
   case "DECLINE_ACTION":
      sharedMeetingManager.declineMeeting(user: userID, 
                                     meetingID: meetingID)
      break
        
   // Handle other actions…
 
   default:
      break
   }
    
   // Always call the completion handler when done.    
   completionHandler()
}
```

> **重要**
>
> 如果你对某个操作的响应涉及访问磁盘上的文件，请考虑使用其他方法。用户可以在设备锁定时对操作做出响应，这会使使用[complete](#)选项加密的文件对你的应用程序不可用。如果发生这种情况，你可能需要暂时保存更改，然后将其集成到应用程序的数据结构中。