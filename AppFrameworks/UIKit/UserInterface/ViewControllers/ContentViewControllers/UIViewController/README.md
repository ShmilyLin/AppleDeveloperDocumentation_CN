# UIViewController

管理UIKit应用程序的视图层次结构的对象。

## 定义

```swift
class UIViewController : UIResponder
```

## 概述

`UIViewController`类定义了所有View Controller共有的公共行为。你很少直接创建UIViewController类的实例。相反，你可以子类化`UIViewController`，并添加管理View Controller的视图层次结构所需的方法和属性。

View Controller的主要职责包括：

* 通常根据对基础数据的变化来更新View的内容。

* 响应用户与View的交互。

* 调整View大小并管理整个界面的布局。

* 与应用程序中的其他对象（包括其他View Controller）进行协调。

View Controller与它管理的View紧密绑定，并参与处理其View层次结构中的事件。具体来说，View Controller是[UIResponder]()对象，并插入到View Controller的Root View和该View的Super View之间的响应者链中，Super View通常属于另一个View Controller。如果View Controller的所有View均未处理事件，则View Controller可以选择处理事件或将其传递给Super View。

View Controller很少单独使用。取而代之的是，你经常使用多个View Controller，每个View Controller都拥有应用程序用户界面的一部分。例如，一个View Controller可能显示一个项目表，而另一个View Controller则显示从该表中选择的项目。通常，一次只能看到一个View Controller的视图。View Controller可以提供一个不同的View Controller以显示一组新View，或者可以充当其他View Controller内容的容器，并根据需要设置动画View。

### 子类化注意事项

每个应用程序至少包含一个`UIViewController`的自定义子类。应用程序通常包含许多自定义View Controller。自定义View Controller定义了应用程序的整体行为，包括应用程序的外观以及其对用户交互的响应方式。以下各节简要概述了你的自定义子类执行的某些任务。有关使用和实现View Controller的详细信息，请参阅[《iOS的View Controller编程指南》]()。

#### View管理

每个View Controller管理一个View层次结构，该View层次结构的Root View存储在这个类的[view]()属性中。Root View主要充当其余View层次结构的容器。Root View的大小和位置由拥有它的对象确定，该对象可以是Parent View Controller，也可以是应用程序的窗口。窗口拥有的View Controller是应用程序的Root View Controller，并且其View的大小会自适应填充满窗口。

View Controller将延迟加载其View。当首次访问[view]()属性会加载或创建View Controller的View。有几种方法可以为View Controller指定视图：

* 在应用的Storyboard中指定View Controller及其View。Storyboard是指定View的首选方法。使用Storyboard，你可以指定View及其与View Controller的连接。你还可以指定View Controller之间的关系和顺序，这使得查看和修改应用程序的行为更加容易。<br>要从Storyboard中加载View Controller，请调用相应的[UIStoryboard]()对象的[instantiateViewController(withIdentifier:)]()方法。Storyboard对象将创建View Controller，并将其返回到你的代码中。

* 使用[Nib文件]()为View Controller指定视图。nib文件允许你指定单个View Controller的View，但不允许你定义View Controller之间的顺序或关系。nib文件还仅存储有关View Controller本身的最少信息。<br>要使用nib文件初始化View Controller对象，请以编程方式创建View Controller的类，然后使用[init(nibName:bundle:)]()方法对其进行初始化。当请求其View时，View Controller从nib文件中加载它们。

* 使用[loadView()]()方法为View Controller指定View。使用该方法，以编程方式创建View层次结构，然后将该层次结构的Root View分配给View Controller的[view]()属性。

所有这些技术都有相同的最终结果，即创建适当的View集并通过[view]()属性公开它们。

> **重要**
>
> View Controller是其View及其创建的任何Subview的唯一所有者。它负责创建这些View，并在适当的时间（例如，释放View Controller本身时）放弃对它们的所有权。如果使用Storyboard或Nib文件存储View对象，则当View Controller要求提供这些View时，每个View Controller对象都会自动获得其自己的副本。但是，如果你手动创建View，则每个View Controller必须具有其自己的唯一View集。你不能在View Controller之间共享View。

View Controller的Root View的大小始终会自适应其被分配的空间。对于View层次结构中的其他View，请使用Interface Builder来指定自动布局约束，这些约束控制着每个View在其Super View范围内的位置和大小。你还可以通过编程方式创建约束，并在适当的时候将其添加到View中。有关如何创建约束的更多信息，请参见[《自动布局指南》]()。

##### 处理与视图相关的通知

当其View的有效性更改时，View Controller会自动调用其自己的方法，以便子类可以响应此更改。使用诸如[viewWillAppear(_:)]()之类的方法来准备将View显示在屏幕上，并使用[viewWillDisappear(_:)]()保存更改或其他状态信息。使用其他方法进行适当的更改。

图1显示了View Controller的View可能的有效状态以及可能发生的状态转换。并非所有的“will”回调方法都只与“did”回调方法配对。你需要确保，如果你以“will”回调方法启动流程，则必须以相应的“did”和相反的“will”回调方法结束该流程。

![图1：有效状态转换](./UIViewController_Class_Reference_2x_ddcaa00c-87d8-4c85-961e-ccfb9fa4aac2.png)

##### 处理视图旋转

从iOS 8开始，不推荐使用所有与旋转相关的方法。相反，旋转被视为View Controller的View大小的变化，因此使用[viewWillTransition(to:with:)]()方法进行报告。当界面方向改变时，UIKit在窗口的Root View Controller上调用此方法。然后，该视View Controller通知其Child View Controller，从而在整个View Controller层次结构中传播消息。

在iOS 6和iOS 7中，你的应用程序支持在应用程序的`Info.plist`文件中定义的界面方向。View Controller可以重写[supportedInterfaceOrientations]()方法以限制支持的方向列表。通常，系统仅在窗口的Root View Controller或显示为填充整个屏幕的View Controller上调用此方法。Child View Controller使用其Parent View Controller为其提供的窗口部分，而不再直接参与有关支持哪些旋转的决策。应用程序的方向蒙版和View Controller的方向蒙版的交集用于确定View Controller可以旋转到的方向。

你可以覆盖视图控制器的[preferredInterfaceOrientationForPresentation]()，该View Controller旨在以特定方向全屏显示。

当可见的View Controller发生旋转时，将在旋转期间调用[willRotate(to:duration:)]()，[willAnimateRotation(to:duration:)]()和[didRotate(from:)]()方法。在View被其父级调整大小并定位后，还会调用[viewWillLayoutSubviews()]()方法。如果在发生方向更改时View Controller不可见，则永远不会调用旋转方法。但是，当View变为可见时，将调用[viewWillLayoutSubviews()]()方法。你可以使用此方法的实现调用[statusBarOrientation]()方法来确定设备的方向。

> **注意**
> 
> 在启动时，应用程序应始终以纵向方向设置其界面。在[application(_:didFinishLaunchingWithOptions:)]()方法返回后，应用程序将使用上述视View Controller旋转机制将View旋转到适当的方向，然后再显示窗口。

#### 实现容器视图控制器

自定义`UIViewController`子类还可以充当Container View Controller。Container View Controller管理其拥有的其他View Controller（也称为其Child View Controller）的内容表示。Child View可以按原样显示，也可以与Container View Controller拥有的View结合显示。

你的Container View Controller子类应声明一个公共接口来关联其子级。这些方法的性质取决于你，并且取决于你要创建的Container的语义。你需要确定View Controller一次可以显示多少个子代，何时显示这些子代以及它们在View Controller的View层次结构中的显示位置。你的View Controller类定义了子级共享的关系（如果有）。通过为Container建立一个干净的公共接口，可以确保子级在逻辑上使用其功能，而不必访问太多有关Container如何实现该行为的私有详细信息。

你的Container View Controller必须在将Child View的Root View添加到View层次结构之前，将Child View Controller与其自身关联。这样，iOS可以将事件正确地路由到Child View Controller以及这些Controller管理的View。同样，在从其Child View层次结构中删除Child View的Root View之后，它应将该Child View Controller与其自身断开连接。为了建立或破坏这些关联，你的Container调用由基类定义的特定方法。Container类的客户端不应该调用这些方法。它们只能由你的Container的实现用于提供预期的收容行为。

这是你可能需要调用的基本方法：

* [addChild(_:)]()

* [removeFromParent()]()

* [willMove(toParent:)]()

* [didMove(toParent:)]()

> **注意**
> 
> 创建Container View Controller时，不需要重写任何方法。
> 默认情况下，旋转和外观回调自动转发给子代。你可以选择重写[shouldAutomaticallyForwardRotationMethods()]()和[shouldAutomaticallyForwardAppearanceMethods]()方法，以自己控制此行为。

#### 内存管理

内存是iOS中的重要资源，View Controller提供了内置支持，可在关键时刻减少其内存占用。 `UIViewController`类通过其[didReceiveMemoryWarning()]()方法提供了一些自动处理降低内存的方法，该方法释放了不需要的内存。

#### 状态保持与恢复

如果你为View Controller的[restoreIdentifier]()属性分配一个值，则当应用程序过渡到后台时，系统可能会要求View Controller对自身进行编码。保存后，View Controller将保留其View层次结构中也具有还原标识符的所有View的状态。View Controller不会自动保存任何其他的状态。如果要实现自定义Container View Controller，则必须自己对所有Child View Controller进行编码。你编码的每个子代都必须具有唯一的还原标识符。

有关系统如何确定要保留和还原哪些View Controller的更多信息，请参阅[《iOS应用程序编程指南》]()。要查看状态保存和还原的示例，请参阅[还原应用的状态]()。

## 主题

### 创建一个View Controller

* [init(nibName: String?, bundle: Bundle?)]()
Returns a newly initialized view controller with the nib file in the specified bundle.

* [init?(coder: NSCoder)]()

### 获取Storyboard和Nib的信息

* [var storyboard: UIStoryboard?]()
The storyboard from which the view controller originated.

* [var nibName: String?]()
The name of the view controller's nib file, if one was specified.

* [var nibBundle: Bundle?]()
The view controller's nib bundle if it exists.

### 管理View

* [var view: UIView!]()
The view that the controller manages.

* [var viewIfLoaded: UIView?]()
The view controller’s view, or nil if the view is not yet loaded.

* [var isViewLoaded: Bool]()
A Boolean value indicating whether the view is currently loaded into memory.

* [func loadView()]()
Creates the view that the controller manages.

* [func viewDidLoad()]()
Called after the controller's view is loaded into memory.

* [func loadViewIfNeeded()]()
Loads the view controller’s view if it has not yet been loaded.

* [var title: String?]()
A localized string that represents the view this controller manages.

* [var preferredContentSize: CGSize]()
The preferred size for the view controller’s view.

### 响应与View相关的事件

* [func viewWillAppear(Bool)]()
Notifies the view controller that its view is about to be added to a view hierarchy.

* [func viewDidAppear(Bool)]()
Notifies the view controller that its view was added to a view hierarchy.

* [func viewWillDisappear(Bool)]()
Notifies the view controller that its view is about to be removed from a view hierarchy.

* [func viewDidDisappear(Bool)]()
Notifies the view controller that its view was removed from a view hierarchy.

* [var isBeingDismissed: Bool]()
A Boolean value indicating whether the view controller is being dismissed.

* [var isBeingPresented: Bool]()
A Boolean value indicating whether the view controller is being presented.

* [var isMovingFromParent: Bool]()
A Boolean value indicating whether the view controller is being removed from a parent view controller.

* [var isMovingToParent: Bool]()
A Boolean value indicating whether the view controller is being moved to a parent view controller.

### 扩展视图的安全区域

* [Positioning Content Relative to the Safe Area]()
Position views so that they are not obstructed by other content.

* [var additionalSafeAreaInsets: UIEdgeInsets]()
Custom insets that you specify to modify the view controller's safe area.

* [func viewSafeAreaInsetsDidChange()]()
Called to notify the view controller that the safe area insets of its root view changed.

### 管理View的边距

* [Positioning Content Within Layout Margins]()
Position views so that they are not crowded by other content.

* [var viewRespectsSystemMinimumLayoutMargins: Bool]()
A Boolean value indicating whether the view controller's view uses the system-defined minimum layout margins.

* [var systemMinimumLayoutMargins: NSDirectionalEdgeInsets]()
The minimum layout margins for the view controller's root view.

* [func viewLayoutMarginsDidChange()]()
Called to notify the view controller that the layout margins of its root view changed.

### 配置View的布局行为

* [var edgesForExtendedLayout: UIRectEdge]()
The edges that you extend for your view controller.

* [struct UIRectEdge]()
Constants that specify the edges of a rectangle.

* [var extendedLayoutIncludesOpaqueBars: Bool]()
A Boolean value indicating whether or not the extended layout includes opaque bars.

* [func viewWillLayoutSubviews()]()
Called to notify the view controller that its view is about to layout its subviews.

* [func viewDidLayoutSubviews()]()
Called to notify the view controller that its view has just laid out its subviews.

* [func updateViewConstraints()]()
Called when the view controller's view needs to update its constraints.

### 配置View旋转设置

* [var shouldAutorotate: Bool]()
Returns a Boolean value indicating whether the view controller's contents should auto rotate.

* [var supportedInterfaceOrientations: UIInterfaceOrientationMask]()
Returns all of the interface orientations that the view controller supports.

* [var preferredInterfaceOrientationForPresentation: UIInterfaceOrientation]()
Returns the interface orientation to use when presenting the view controller.

* [class func attemptRotationToDeviceOrientation()]()
Attempts to rotate all windows to the orientation of the device.

### Performing Segues

* [func shouldPerformSegue(withIdentifier: String, sender: Any?) -> Bool]()
Determines whether the segue with the specified identifier should be performed.

* [func prepare(for: UIStoryboardSegue, sender: Any?)]()
Notifies the view controller that a segue is about to be performed.

* [func performSegue(withIdentifier: String, sender: Any?)]()
Initiates the segue with the specified identifier from the current view controller's storyboard file.

* [func allowedChildrenForUnwinding(from: UIStoryboardUnwindSegueSource) -> [UIViewController]]()
Returns an array of child view controllers to search for an unwind segue destination.

* [func childContaining(UIStoryboardUnwindSegueSource) -> UIViewController?]()
Returns the child view controller that contains the source of the unwind segue.

* [func canPerformUnwindSegueAction(Selector, from: UIViewController, sender: Any?) -> Bool]()
Called on a view controller to determine whether it responds to an unwind action.

* [func unwind(for: UIStoryboardSegue, towards: UIViewController)]()
Called when an unwind segue transitions to a new view controller.

### 呈现一个View Controller

* [func show(UIViewController, sender: Any?)](./1621377-show.md)

    在主要上下文中显示View Controller。

* [func showDetailViewController(UIViewController, sender: Any?)](./1621432-showdetailviewcontroller.md)

    在辅助（或详细信息）上下文中显示View Controller。

* [func present(UIViewController, animated: Bool, completion: (() -> Void)?)](./1621380-present.md)

    模态呈现一个View Controller。

* [func dismiss(animated: Bool, completion: (() -> Void)?)](./1621505-dismiss.md)

    消除由View Controller模态显示的View Controller。

* [var modalPresentationStyle: UIModalPresentationStyle](./1621355-modalpresentationstyle.md)

    模态呈现View Controller时的呈现样式。

* [enum UIModalPresentationStyle](./UIModalPresentationStyle/)

    呈现View Controller时可用的模态呈现样式。

* [var modalTransitionStyle: UIModalTransitionStyle]()
The transition style to use when presenting the view controller.

* [enum UIModalTransitionStyle]()
Transition styles available when presenting view controllers.

* [var isModalInPresentation: Bool]()
A Boolean value indicating whether the view controller enforces a modal behavior.

* [var definesPresentationContext: Bool]()
A Boolean value that indicates whether this view controller's view is covered when the view controller or one of its descendants presents a view controller.

* [var providesPresentationContextTransitionStyle: Bool]()
A Boolean value that indicates whether the view controller specifies the transition style for view controllers it presents.

* [var disablesAutomaticKeyboardDismissal: Bool]()
Returns a Boolean indicating whether the current input view is dismissed automatically when changing controls.

* [class let showDetailTargetDidChangeNotification: NSNotification.Name]()
Posted when a split view controller is expanded or collapsed.

### 添加自定义过渡或演示

* [var transitioningDelegate: UIViewControllerTransitioningDelegate?]()
The delegate object that provides transition animator, interactive controller, and custom presentation controller objects.

* [var transitionCoordinator: UIViewControllerTransitionCoordinator?]()
Returns the active transition coordinator object.

* [func targetViewController(forAction: Selector, sender: Any?) -> UIViewController?]()
Returns the view controller that responds to the action.

* [var presentationController: UIPresentationController?]()
The nearest presentation controller that is managing the current view controller.

* [var popoverPresentationController: UIPopoverPresentationController?]()
The nearest popover presentation controller that is managing the current view controller.

* [var restoresFocusAfterTransition: Bool]()
A Boolean value that indicates whether an item that previously was focused should again become focused when the item's view controller becomes visible and focusable.

### 适应环境变化

* [func collapseSecondaryViewController(UIViewController, for: UISplitViewController)]()
Called when a split view controller transitions to a compact-width size class.

* [func separateSecondaryViewController(for: UISplitViewController) -> UIViewController?]()
Called when a split view controller transitions to a regular-width size class.

### 调整界面样式

* [var overrideUserInterfaceStyle: UIUserInterfaceStyle]()
The user interface style adopted by the view controller and all of its children.

* [var preferredUserInterfaceStyle: UIUserInterfaceStyle]()
The preferred interface style for this view controller.

* [var childViewControllerForUserInterfaceStyle: UIViewController?]()
The child view controller that supports the preferred user interface style.

* [func setNeedsUserInterfaceAppearanceUpdate()]()
Notifies the view controller that a change occurred that might affect the preferred interface style.

* [enum UIUserInterfaceStyle]()
Constants indicating the interface style for the app.

### 在自定义Container中管理Child View Controller

* [var children: [UIViewController]]()
An array of view controllers that are children of the current view controller.

* [func addChild(UIViewController)]()
Adds the specified view controller as a child of the current view controller.

* [func removeFromParent()]()
Removes the view controller from its parent.

* [func transition(from: UIViewController, to: UIViewController, duration: TimeInterval, options: UIView.AnimationOptions, animations: (() -> Void)?, completion: ((Bool) -> Void)?)]()
Transitions between two of the view controller's child view controllers.

* [var shouldAutomaticallyForwardAppearanceMethods: Bool]()
Returns a Boolean value indicating whether appearance methods are forwarded to child view controllers.

* [func beginAppearanceTransition(Bool, animated: Bool)]()
Tells a child controller its appearance is about to change.

* [func endAppearanceTransition()]()
Tells a child controller its appearance has changed.

* [func setOverrideTraitCollection(UITraitCollection?, forChild: UIViewController)]()
Changes the traits assigned to the specified child view controller.

* [func overrideTraitCollection(forChild: UIViewController) -> UITraitCollection?]()
Retrieves the trait collection for a child view controller.

* [class let hierarchyInconsistencyException: NSExceptionName]()
Raised if the view controller hierarchy is inconsistent with the view hierarchy.

### 响应回收事件

* [func willMove(toParent: UIViewController?)]()
Called just before the view controller is added or removed from a container view controller.

* [func didMove(toParent: UIViewController?)]()
Called after the view controller is added or removed from a container view controller.

### 获取其他相关View Controller

* [var presentingViewController: UIViewController?]()
The view controller that presented this view controller.

* [var presentedViewController: UIViewController?]()
The view controller that is presented by this view controller, or one of its ancestors in the view controller hierarchy.

* [var parent: UIViewController?]()
The parent view controller of the recipient.

* [var splitViewController: UISplitViewController?]()
The nearest ancestor in the view controller hierarchy that is a split view controller.

* [var navigationController: UINavigationController?]()
The nearest ancestor in the view controller hierarchy that is a navigation controller.

* [var tabBarController: UITabBarController?]()
The nearest ancestor in the view controller hierarchy that is a tab bar controller.

### 配置Navigation界面

* [var navigationItem: UINavigationItem]()
The navigation item used to represent the view controller in a parent's navigation bar.

* [var hidesBottomBarWhenPushed: Bool]()
A Boolean value indicating whether the toolbar at the bottom of the screen is hidden when the view controller is pushed on to a navigation controller.

* [func setToolbarItems([UIBarButtonItem]?, animated: Bool)]()
Sets the toolbar items to be displayed along with the view controller.

* [var toolbarItems: [UIBarButtonItem]?]()
The toolbar items associated with the view controller.

### 配置Tab Bar的内容

* [var tabBarItem: UITabBarItem!]()
The tab bar item that represents the view controller when added to a tab bar controller.

* [var tabBarObservedScrollView: UIScrollView?]()
The full-screen scroll view to synchronize with a scrolling tab bar.

### 支持应用程序扩展

* [var extensionContext: NSExtensionContext?]()
Returns the extension context of the view controller.

### 协调系统手势

* [var preferredScreenEdgesDeferringSystemGestures: UIRectEdge]()
The screen edges for which you want your gestures to take precedence over the system gestures

* [var childForScreenEdgesDeferringSystemGestures: UIViewController?]()
Returns the child view controller that should be queried to see if its gestures should take precedence.

* [func setNeedsUpdateOfScreenEdgesDeferringSystemGestures()]()
Call this method when you change the screen edges that you use for deferring system gestures.

* [var prefersHomeIndicatorAutoHidden: Bool]()
Returns a Boolean indicating whether the system is allowed to hide the visual indicator for returning to the Home screen.

* [var childForHomeIndicatorAutoHidden: UIViewController?]()
Returns the child view controller that is consulted about its preference for displaying a visual indicator for returning to the Home screen.

* [func setNeedsUpdateOfHomeIndicatorAutoHidden()]()
Notifies UIKit that your view controller updated its preference regarding the visual indicator for returning to the Home screen.

### 管理Status Bar

* [var childForStatusBarHidden: UIViewController?]()
Called when the system needs the view controller to use for determining status bar hidden/unhidden state.

* [var childForStatusBarStyle: UIViewController?]()
Called when the system needs the view controller to use for determining status bar style.

* [var preferredStatusBarStyle: UIStatusBarStyle]()
The preferred status bar style for the view controller.

* [var prefersStatusBarHidden: Bool]()
Specifies whether the view controller prefers the status bar to be hidden or shown.

* [var modalPresentationCapturesStatusBarAppearance: Bool]()
Specifies whether a view controller, presented non-fullscreen, takes over control of status bar appearance from the presenting view controller.

* [var preferredStatusBarUpdateAnimation: UIStatusBarAnimation]()
Specifies the animation style to use for hiding and showing the status bar for the view controller.

* [func setNeedsStatusBarAppearanceUpdate()]()
Indicates to the system that the view controller status bar attributes have changed.

### 访问可用的键盘命令

* [var performsActionsWhilePresentingModally: Bool]()
A Boolean value indicating whether the view controller performs menu-related actions.

* [func addKeyCommand(UIKeyCommand)]()
Associates the specified keyboard shortcut with the view controller.

* [func removeKeyCommand(UIKeyCommand)]()
Removes the key command from the view controller.

### 向View Controller添加编辑行为

* [var isEditing: Bool]()
A Boolean value indicating whether the view controller currently allows the user to edit the view contents.

* [func setEditing(Bool, animated: Bool)]()
Sets whether the view controller shows an editable view.

* [var editButtonItem: UIBarButtonItem]()
Returns a bar button item that toggles its title and associated state between Edit and Done.

### 处理内存警告

* [func didReceiveMemoryWarning()]()
Sent to the view controller when the app receives a memory warning.

### 管理状态还原

* [Restoring Your App’s State]()
Preserve and restore information related to the user’s current activities.

* [var restorationIdentifier: String?]()
The identifier that determines whether the view controller supports state restoration.

* [var restorationClass: UIViewControllerRestoration.Type?]()
The class responsible for recreating this view controller when restoring the app's state.

* [func encodeRestorableState(with: NSCoder)]()
Encodes state-related information for the view controller.

* [func decodeRestorableState(with: NSCoder)]()
Decodes and restores state-related information for the view controller.

* [func applicationFinishedRestoringState()]()
Called on restored view controllers after other object decoding is complete.

### 支持Swift Playgrounds

* [var playgroundLiveViewRepresentation: PlaygroundLiveViewRepresentation

### 实例属性

* [var childViewControllerForTouchBar: UIViewController?]()

### 实例方法

* [func setNeedsTouchBarUpdate()]()