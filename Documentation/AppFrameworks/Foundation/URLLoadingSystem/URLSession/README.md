# URLSession

协调一组相关网络数据传输任务的对象。

---
## 概述

The URLSession class and related classes provide an API for downloading content. This API provides a rich set of delegate methods for supporting authentication and gives your app the ability to perform background downloads when your app isn’t running or, in iOS, while your app is suspended.

The URLSession class natively supports the data, file, ftp, http, and https URL schemes, with transparent support for proxy servers and SOCKS gateways, as configured in the user’s system preferences.

URLSession supports the HTTP/1.1, SPDY, and HTTP/2 protocols. HTTP/2 support is described by RFC 7540, and requires a server supporting either ALPN or NPN for protocol negotiation.

You can also add support for your own custom networking protocols and URL schemes (for your app’s private use) using URLProtocol.

> Important
> 
> The URLSession API involves many different classes working together in a fairly complex way that may not be obvious if you read the reference documentation by itself. Before using this API, you should read URL Session Programming Guide to gain a conceptual understanding of how these classes interact with one another.

With the URLSession API, your app creates one or more sessions, each of which coordinates a group of related data transfer tasks. For example, if you’re creating a web browser, your app might create one session per tab or window, or one session for interactive use and another for background downloads. Within each session, your app adds a series of tasks, each of which represents a request for a specific URL (following HTTP redirects, if necessary).

The tasks within a given URL session share a common session configuration object, which defines connection behavior, such as the maximum number of simultaneous connections to make to a single host, whether to allow connections over a cellular network, and so on. The behavior of a session is determined in part by which method you call when creating its configuration object:

* The singleton shared session (which has no configuration object) is for basic requests. It’s not as customizable as sessions that you create, but it serves as a good starting point if you have very limited requirements. You access this session by calling the shared class method. See that method’s discussion for more information about its limitations.

* Default sessions behave much like the shared session (unless you customize them further), but let you obtain data incrementally using a delegate. You can create a default session configuration by calling the default method on the URLSessionConfiguration class.

* Ephemeral sessions are similar to default sessions, but they don’t write caches, cookies, or credentials to disk. You can create an ephemeral session configuration by calling the ephemeral method on the URLSessionConfiguration class.

* Background sessions let you perform uploads and downloads of content in the background while your app isn’t running. You can create a background session configuration by calling the backgroundSessionConfiguration(_:) method on the URLSessionConfiguration class.

The session configuration object also contains a reference to URL cache and cookie storage objects that may be used when making requests and handling the responses, depending on the configuration and request type.

The tasks in a session also share a common delegate that lets you provide and obtain information when various events occur—when authentication fails, when data arrives from the server, when data is ready to be cached, and so on. Using a URL Session has a step-by-step list of events that occur when a session is performing a task, and which delegate methods are called as a result.

On the other hand, if you don’t need any of the features provided by a delegate, you can use this API without providing one by passing nil when you create a session.

> Important
> 
> The session object keeps a strong reference to the delegate until your app exits or explicitly invalidates the session. If you don’t invalidate the session, your app leaks memory until it exits.

Within a session, you create tasks that optionally upload data to a server and then retrieve data from the server either as a file on disk or as one or more NSData objects in memory. The URLSession API provides three types of tasks:

* Data tasks send and receive data using NSData objects. Data tasks are intended for short, often interactive requests to a server.

* Upload tasks are similar to data tasks, but they also send data (often in the form of a file), and support background uploads while the app isn’t running.

* Download tasks retrieve data in the form of a file, and support background downloads and uploads while the app isn’t running.

Like most networking APIs, the URLSession API is highly asynchronous. It returns data to your app in one of two ways, depending on the methods you call:

* By calling a completion handler block when a transfer finishes successfully or with an error.

* By calling methods on the session’s delegate as data is received and when the transfer is complete.

In addition to delivering this information to delegates, the URLSession API provides status and progress properties that you can query if you need to make programmatic decisions based on the current state of the task (with the caveat that its state can change at any time).

URL sessions also support canceling, restarting or resuming, and suspending tasks, and provide the ability to resume suspended, canceled, or failed downloads where they left off.

### Related Classes

The URLSession API uses a number of classes that are also commonly used with other APIs, such as NSURLConnection and NSURLDownload. Some of these shared classes include:

* NSURL—An object that contains a URL.

* NSURLRequest—Encapsulates metadata related to a URL request, including the URL, request method, and so on.

* URLResponse—Encapsulates metadata related to a server’s response to a request, such as the content MIME type and length.

* HTTPURLResponse—Adds metadata specific to HTTP requests, such as response headers.

* CachedURLResponse—Encapsulates a URL response object, along with the actual body data of the server’s response, for caching purposes.

### App Transport Security (ATS)

Starting in iOS 9.0 and OS X 10.11, a new security feature called App Transport Security (ATS) is enabled by default for all HTTP connections made with URLSession. ATS requires that HTTP connections use HTTPS (RFC 2818).

For more information, see NSAppTransportSecurity in the Information Property List Key Reference.

### Using a URL Session

To make a request using the URLSession class:

1. Create a session configuration. For background sessions, this configuration must contain a unique identifier. Store that identifier, and use it to reassociate with the session if your app crashes or is terminated or suspended.

2. Create a session, specifying a configuration object and, optionally, a delegate.

3. Create task objects within a session that each represent a resource request. These task objects are subclasses of URLSessionTask—URLSessionDataTask, URLSessionUploadTask, or URLSessionDownloadTask, depending on the behavior you’re trying to achieve. Each task starts in a suspended state. After your app calls resume() on the task, it begins downloading the specified resource.

After you start a task, the session calls methods on its delegate, as follows:

1. If the initial handshake with the server requires a connection-level challenge (such as an SSL client certificate), URLSession calls either the urlSession(_:task:didReceive:completionHandler:) or urlSession(_:didReceive:completionHandler:) delegate method.

2. If the task’s data is provided from a stream, the URLSession object calls the delegate’s urlSession(_:task:needNewBodyStream:) delegate method to obtain an instance of InputStream that provides the body data for the new request.

3. During the initial upload of body content to the server (if applicable), the delegate periodically receives urlSession(_:task:didSendBodyData:totalBytesSent:totalBytesExpectedToSend:) callbacks that report the progress of the upload.

4. The server sends a response.

5. If the response indicates that authentication is required, the session calls its delegate’s urlSession(_:task:didReceive:completionHandler:) method. Go back to step 2.

6. If the response is an HTTP redirect response, the URLSession object calls the delegate’s urlSession(_:task:willPerformHTTPRedirection:newRequest:completionHandler:) method. That delegate method calls the provided completion handler with either the provided NSURLRequest object (to follow the redirect), a new NSURLRequest object (to redirect to a different URL), or nil (to treat the redirect’s response body as a valid response and return it as the result).

   * If you decide to follow the redirect, go back to step 2.

   * If the delegate doesn’t implement this method, the redirect is followed up to the maximum number of redirects.

7. For a download (or redownload) task created by calling downloadTask(withResumeData:) or downloadTask(withResumeData:completionHandler:), URLSession calls the delegate’s urlSession(_:downloadTask:didResumeAtOffset:expectedTotalBytes:) method with the new task object.

8. For a data task, the URLSession object calls the delegate’s urlSession(_:dataTask:didReceive:completionHandler:) method. Decide whether to convert the data task into a download task, and then call the completion handler to convert, continue, or cancel the task. If your app chooses to convert the data task to a download task, URLSession calls the delegate’s urlSession(_:dataTask:didBecome:) method with the new download task as a parameter. After this call, the delegate receives no further callbacks from the data task, and begins receiving callbacks from the download task.

9. During the transfer from the server, the delegate periodically receives a task-level callback to report the progress of the transfer. For a data task, the session calls the delegate’s urlSession(_:dataTask:didReceive:)method with the actual pieces of data as they’re received. For a download task, the session calls the delegate’s urlSession(_:downloadTask:didWriteData:totalBytesWritten:totalBytesExpectedToWrite:) method with the number of bytes successfully written to disk. If the user tells your app to pause the download, cancel the task by calling the cancel(byProducingResumeData:) method. Later, if the user asks your app to resume the download, pass the returned resume data to either the downloadTask(withResumeData:) or downloadTask(withResumeData:completionHandler:) method to create a new download task that continues the download. (Go to step 1.)

10. For a data task, the URLSession object may call the delegate’s urlSession(_:dataTask:willCacheResponse:completionHandler:) method. Your app should then decide whether to allow caching. If you don’t implement this method, the default behavior is to use the caching policy specified in the session’s configuration object.

11. If the response is multipart encoded, the session may call the delegate’s didReceiveResponse method again, followed by zero or more additional didReceiveData calls. If this happens, go to step 8 (handling the didReceiveResponse call).

12. If a download task completes successfully, then the URLSession object calls the task’s urlSession(_:downloadTask:didFinishDownloadingTo:) method with the location of a temporary file. Your app must either read the response data from this file or move it to a permanent location before this delegate method returns.

13. When any task completes, the URLSession object calls the delegate’s urlSession(_:task:didCompleteWithError:) method with either an error object or nil (if the task completed successfully). If the download task can be resumed, the NSError object’s userInfo dictionary contains a value for the NSURLSessionDownloadTaskResumeData key. Your app should pass this value to call downloadTask(withResumeData:) or downloadTask(withResumeData:completionHandler:) to create a new download task that continues the existing download. If the task can’t be resumed, your app should create a new download task and restart the transaction from the beginning. In either case, if the transfer failed for any reason other than a server error, go to step 3 (creating and resuming task objects).

14. If you no longer need a session, you can invalidate it by calling either invalidateAndCancel() (to cancel outstanding tasks) or finishTasksAndInvalidate() (to allow outstanding tasks to finish before invalidating the object). If you don’t invalidate the session, it automatically goes away when your app is terminated (unless it’s a background session with active tasks). After invalidating the session, when all outstanding tasks have been canceled or have finished, the session calls the delegate’s urlSession(_:didBecomeInvalidWithError:) method. When that delegate method returns, the session disposes of its strong reference to the delegate.

If your app cancels an in-progress download, the URLSession object calls the delegate’s urlSession(_:task:didCompleteWithError:) method as though an error occurred.

### NSCopying Behavior

Session and task objects conform to the NSCopying protocol as follows:

* When your app copies a session or task object, you get the same object back.

* When your app copies a configuration object, you get a new copy that you can independently modify.

### Thread Safety

The URL session API itself is fully thread-safe. You can freely create sessions and tasks in any thread context, and when your delegate methods call the provided completion handlers, the work is automatically scheduled on the correct delegate queue.

> Warning
> 
> Your urlSessionDidFinishEvents(forBackgroundURLSession:) session delegate method may be called on a secondary thread. However, in iOS, your implementation of that method may need to call a completion handler provided to you in your application(_:handleEventsForBackgroundURLSession:completionHandler:) app delegate method. You must call that completion handler on the main thread.

---
## 主题

### 一、创建一个会话

#### ● [init(configuration: URLSessionConfiguration)]()
Creates a session with the specified session configuration.

#### ● [init(configuration: URLSessionConfiguration, delegate: URLSessionDelegate?, delegateQueue: OperationQueue?)]()
Creates a session with the specified session configuration, delegate, and operation queue.

#### ● [class var shared: URLSession]()
Returns a shared singleton session object.

### 二、配置一个会话

#### ● [var configuration: URLSessionConfiguration]()
A copy of the configuration object for this session.

#### ● [var delegate: URLSessionDelegate?]()
The delegate assigned when this object was created.

#### ● [protocol URLSessionDelegate](./URLSessionDelegate/)

`NSURLSessionDelegate`协议描述[URLSession]()对象在其`delegates`上调用以处理会话级别事件的方法。

#### ● [protocol URLSessionTaskDelegate](./URLSessionTaskDelegate/)

`NSURLSessionTaskDelegate`协议定义了在使用任何类型的[URLSession]()任务时应该实现的特定任务的委托方法。

#### ● [var delegateQueue: OperationQueue]()
The operation queue provided when this object was created.

#### ● [var sessionDescription: String?]()
An app-defined descriptive label for the session.

### 三、给一个会话添加数据任务（`Data Tasks`）

#### ● [func dataTask(with: URL)]()
Creates a task that retrieves the contents of the specified URL.

#### ● [func dataTask(with: URL, completionHandler: (Data?, URLResponse?, Error?) -> Void)]()
Creates a task that retrieves the contents of the specified URL, then calls a handler upon completion.

#### ● [func dataTask(with: URLRequest)]()
Creates a task that retrieves the contents of a URL based on the specified URL request object.

#### ● [func dataTask(with: URLRequest, completionHandler: (Data?, URLResponse?, Error?) -> Void)]()
Creates a task that retrieves the contents of a URL based on the specified URL request object, and calls a handler upon completion.

#### ● [class URLSessionDataTask]()
A URL session task that returns downloaded data directly to the app in memory.

#### ● [protocol URLSessionDataDelegate](./URLSessionDataDelegate/)

`NSURLSessionDataDelegate`协议定义了[URLSession]()对象的`delegate`可以实现的方法，以处理特定数据任务和上传任务的任务级事件。

### 四、给一个会话添加下载任务

#### ● [func downloadTask(with: URL)]()
Creates a download task that retrieves the contents of the specified URL and saves the results to a file.

#### ● [func downloadTask(with: URL, completionHandler: (URL?, URLResponse?, Error?) -> Void)]()
Creates a download task that retrieves the contents of the specified URL, saves the results to a file, and calls a handler upon completion.

#### ● [func downloadTask(with: URLRequest)]()
Creates a download task that retrieves the contents of a URL based on the specified URL request object and saves the results to a file.

#### ● [func downloadTask(with: URLRequest, completionHandler: (URL?, URLResponse?, Error?) -> Void)]()
Creates a download task that retrieves the contents of a URL based on the specified URL request object, saves the results to a file, and calls a handler upon completion.

#### ● [func downloadTask(withResumeData: Data)]()
Creates a download task to resume a previously canceled or failed download.

#### ● [func downloadTask(withResumeData: Data, completionHandler: (URL?, URLResponse?, Error?) -> Void)]()
Creates a download task to resume a previously canceled or failed download and calls a handler upon completion.

#### ● [class URLSessionDownloadTask]()
A URL session task that stores downloaded data to file.

#### ● [protocol URLSessionDownloadDelegate]()
The NSURLSessionDownloadDelegate protocol defines delegate methods that you should implement when using 
URLSession
 download tasks.

### 五、给一个会话添加上传任务

#### ● [func uploadTask(with: URLRequest, from: Data)]()
Creates a task that performs an HTTP request for the specified URL request object and uploads the provided data.

#### ● [func uploadTask(with: URLRequest, from: Data?, completionHandler: (Data?, URLResponse?, Error?) -> Void)]()
Creates a task that performs an HTTP request for the specified URL request object, uploads the provided data, and calls a handler upon completion.

#### ● [func uploadTask(with: URLRequest, fromFile: URL)]()
Creates a task that performs an HTTP request for uploading the specified file.

#### ● [func uploadTask(with: URLRequest, fromFile: URL, completionHandler: (Data?, URLResponse?, Error?) -> Void)]()
Creates a task that performs an HTTP request for uploading the specified file, then calls a handler upon completion.

#### ● [func uploadTask(withStreamedRequest: URLRequest)]()
Creates a task that performs an HTTP request for uploading data based on the specified URL request.

#### ● [class URLSessionUploadTask]()
A URL session task that uploads data to the network in a request body.

#### ● [protocol URLSessionDataDelegate]()
The NSURLSessionDataDelegate protocol defines the methods that a delegate of an 
URLSession
 object can implement to handle task-level events specific to data tasks and upload tasks.

 ### 六、给一个会话添加流任务（`Stream Tasks`）

#### ● [func streamTask(withHostName: String, port: Int)]()
Creates a task that establishes a bidirectional TCP/IP connection to a specified hostname and port.

#### ● [func streamTask(with: NetService)]()
Creates a task that establishes a bidirectional TCP/IP connection using a specified network service.

#### ● [class URLSessionStreamTask]()
A URL session task that is stream-based.

#### ● [protocol URLSessionStreamDelegate]()
The NSURLSessionStreamDelegate protocol defines delegate methods that you should implement when using 
URLSession
 stream tasks.

### 七、管理会话

#### ● [func finishTasksAndInvalidate()]()
Invalidates the session, allowing any outstanding tasks to finish.

#### ● [func flush(completionHandler: () -> Void)]()
Flushes cookies and credentials to disk, clears transient caches, and ensures that future requests occur on a new TCP connection.

#### ● [func getTasksWithCompletionHandler(([URLSessionDataTask], [URLSessionUploadTask], [URLSessionDownloadTask]) -> Void)]()
Asynchronously calls a completion callback with all data, upload, and download tasks in a session.

#### ● [func getAllTasks(completionHandler: ([URLSessionTask]) -> Void)]()
Asynchronously calls a completion callback with all tasks in a session

#### ● [func invalidateAndCancel()]()
Cancels all outstanding tasks and then invalidates the session.

#### ● [func reset(completionHandler: () -> Void)]()
Empties all cookies, caches and credential stores, removes disk files, flushes in-progress downloads to disk, and ensures that future requests occur on a new socket.

### 八、常量

#### ● [NSURLSession-Specific NSError userInfo Dictionary Keys]()
Keys used in conjunction with NSError objects returned by the NSURLSession API.

#### ● [Background Task Cancellation reasons]()
Constants that indicate why a background task was cancelled.

#### ● [enum URLSession.DelayedRequestDisposition]()
The action to take on a delayed URL session task.

#### ● [Transfer Size Constant]()
A constant denoting an unknown transfer size.

---
## 关系

### 继承自

[NSObject]()

### 遵守

* [CVarArg]()
* [Equatable]()
* [Hashable]()

---
## 其他内容

