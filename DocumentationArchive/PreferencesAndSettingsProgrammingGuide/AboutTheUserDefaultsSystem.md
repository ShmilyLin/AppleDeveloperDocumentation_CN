# 关于User Defaults System

User Defaults System管理每个用户的偏好设置的存储。大多数偏好设置会永久存储，因此在应用程序的后续启动周期之间不会更改。应用程序使用偏好设置来跟踪用户启动和程序启动的配置更改。

## 什么是良好的偏好设置？

When defining your app’s preferences, it is better to use simple values and data types whenever possible. The preferences system is built around property-list data types such as strings, numbers, and dates. Although you can use an NSData object to store arbitrary objects in preferences, doing so is not recommended in most cases.

Storing objects persistently means that your app has to decode that object at some point. In the case of preferences, a stored object means decoding the object every time you access the preference. It also means that a newer version of your app has to ensure that it is able to decode objects created and written to disk using an earlier version of your app, which is potentially error prone.

A better approach for preferences is to store simple strings and values and use them to create the objects your app needs. Storing simple values means that your app can always access the value. The only thing that changes from release to release is the interpretation of the simple value and the objects your app creates in response.

## 提供偏好设置界面

对于面向用户的偏好设置，`表 1-1`列出了用于向用户显示这些偏好设置的选项。从该表中可以看到，大多数选项都涉及创建用于管理和显示偏好设置的自定义用户界面。如果要创建iOS应用，则可以使用Settings Bundle来呈现偏好设置，但仅应在用户不经常更改的设置中这样做。

表 1-1 向用户显示偏好设置的选项
| 偏好设置 | iOS | OS X |
|:-------|:----|:-----|
| 经常更改的偏好 | 自定义UI | 自定义UI |
| 不经常更改的偏好 | Settings Bundle | 自定义UI |

> **注意：**可能会经常变化的偏好，可能包括音量、游戏控制选项等。可能不会经常更改的偏好设置，可能是“邮件”应用程序中的电子邮件地址和服务器设置。对于iOS应用程序，最终由你决定是否适合从“设置”应用程序或应用程序内部显示偏好设置。

Mac应用程序中的偏好设置应该可以从应用程序菜单中的“偏好设置”菜单项访问。使用Xcode模板创建的Cocoa应用程序会自动为你提供这样的菜单项。当用户选择此菜单项时，你应该提供适当的用户界面。你可以通过以下方式提供该用户界面：在应用程序委托中定义一个显示自定义偏好设置窗口的操作方法，然后将该操作方法连接到Interface Builder中的菜单项。

没有标准的方法可以从iOS应用程序内部显示自定义偏好设置。你可以通过多种方式集成偏好设置，包括在标签栏界面中使用单独的标签或使用应用程序屏幕之一中的自定义按钮。 偏好设置通常应使用不同的View Controller来呈现，以便在用户关闭该View Controller时可以记录偏好的变化。