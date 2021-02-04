# JavaFX概述

想要灵活使用JavaFX，我们首先需要了解JavaFX是如何设计的，了解整个JavaFX的大概内容以及他拥有的特性。本章节是关于JavaFX的概述、JavaFX的总体结构以及一些特性。

总得来说，JavaFX应用包含一个或多个*stage*,*stage*对应的是*windows（窗口）*。每一个*stage*包含一个*scene*。每个*scene*可以具有控件，布局等的对象图。这个附加到其身上的称为*scene graph*。下面是概念图。

![JavaFX overview of JavaFX internal application structure.](http://tutorials.jenkov.com/images/java-javafx/javafx-overview-1.png)

## Stage

*stage*是JavaFX应用程序的外部框架。一个*stage*通常相当于一个*window窗口*。<del>在早期，JavaFX可以在浏览器中运行，stage也可以指web页面中JavaFX可以自己绘制的区域。由于Java浏览器插件JavaFX已被弃用，它主要用于桌面应用程序</del>。现在，JavaFX取代了Swing，成为倍受推荐的桌面GUI框架。我必须说，JavaFX看起来比Swing更加一致，功能更加丰富。

在桌面*(desktop)*环境中使用时，JavaFX应用程序可以打开多个窗口。每个窗口都是一个*stage*。

每个*stage*都由JavaFX应用程序中的`Stage`对象表示。JavaFX应用程序有一个主要的Stage对象，它是由JavaFX运行时为您创建的。如果需要打开额外的窗口，JavaFX应用程序可以创建额外的Stage对象。例如，对于*对话框(dialog)*、*向导(wizards)*等。

## Scene

要想在JavaFX应用程序的*stage*上显示任何东西，您需要一个*scene*。一个*stage*一次只能展示一个*scene*，但*stage*可以在运行时交换*scene*。就像剧院中的*舞台(stage)*可以重新安排以在一出戏中显示多个场景(scene)一样，但是需要特别注意，**每个*stage*可以有多个*stage*，但是一次只能显示一个*scene。***

您可能会疑惑，为什么JavaFX应用每个*stage*会有多*scene*。这就类似一个电脑游戏。游戏可能会向用户呈现多个“屏幕”。例如，初始菜单屏幕、游戏主屏幕(即玩游戏的地方)、游戏结束屏幕和排名屏幕。每个屏幕都可以用不同的*scene*来表示。当游戏需要从一个屏幕切换到下一个屏幕时，它只需将相应的*scene*附加到JavaFX应用程序的*stage*上即可。

一个stage由JavaFX中的一个`Stage`对象表示。一个JavaFX应用程序必须创建它需要的所有*scene*对象。

##  Scene Graph *——场景图*

所有视觉组件(控件、布局等)都必须附加到一个*scene*中显示，而该*scene*也必须附加到一个*stage*上，以便来使*scene*可见。加在一个scene上的所有控件、布局等的包含所有组件的图称为*scene graph*场景图。

## Nodes

连接到*scene graph*的所有组件都被称为*node*。所有的*node*都是JavaFX .scene.Node的子类。有两种类型的node，一个是*Branch node(分支节点)*，另一个称为*Leaf node(叶节点)*。*branch node*是可以包含其他node的节点。分支节点也被称为*parent node（父节点）*，因为它们可以包含其他子节点。*Leaf node(叶节点)*是不能包含其他节点的节点。例如`VBox`就是*branch node*的一类，`Button`是*leaf branch* 的类。

> 后文中的组件通常指的就是*node*

## Controls*——控件*

JavaFX *controls* 是JavaFX的组件，可在JavaFX应用程序内部提供某种控件功能。 例如：按钮、单选按钮、表格、树图等。

为了使控件可见，必须将其附加到某个scene的*scene graph(场景图)*上。

控件通常嵌套在一些JavaFX *layout* 组件中，*layout* 组件可以管理控件之间的相对布局。

下面列出了JavaFX自带的控件：

***Accordion 可折叠标签***

| 折叠时                                                       | 展开时                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![image-20210204125423684](W:\JavaFX-ch\JavaFX----\docs\JavaFX概述.assets\image-20210204125423684.png) | ![image-20210204125432821](W:\JavaFX-ch\JavaFX----\docs\JavaFX概述.assets\image-20210204125432821.png) |

***Button	按钮***

***CheckButton	复选框***

***ChoiceBox	单选框***

***ColorPicker	颜色选择器***

***ComboBox	下拉列表(选择)框***

***DatePicker	日期选择器***

***Label	标签***

***ListView	列表视图***

***Menu	菜单***

***MenuBar	菜单条***

***PasswordField	密码输入框***

***ProgressBar	进度条***

***RadioButton	单选按钮***

***Slider	滑块***

***Spinner	选择框***

***SplitMenuButton	分割菜单按钮***

***SplitPane	分割窗体***

 ***TableView	表格视图***

***TabPane	页面板***

***TextArea	文字区域框***

***TextField	输入框***

***TitledPane	标签板***

***ToggleButton	开关按钮***

***ToolBar	工具条***

***TreeTableView***	

***TreeView	树状视图***

## Layouts*——布局*

JavaFX *layout*是可以包含其他组件的组件。*layout*组件管理嵌套在其中的组件的布局。JavaFX布局组件有时也被称为*parent components*，因为它们可以包含子组件，而且`Layout`类是`Parent`类的子类。

一个布局组件必须添加到某个*scene*对象的*scene graph*上才能可见。

下面列出了JavaFX自带的布局组件：

***Group	Region	Pane	HBox	VBox	FlowPane***

***BorderPane	StackPane	TilePane GridPane	AnchorPane***

***TextFlow***

### Nested Layouts*——嵌套布局*

可以将*layout*组件嵌套到其他*layout*组件中。这对于实现特定的布局非常有用。

## Charts*——图表*

JavaFX自带了一组内置的随时可用的*charts（图表）*组件，所以在你需要使用时，不需要从头开始编写图表。

下面列出了JavaFX自带的图表组件：
***AreaChart	BarChart	BubbleChart***

***LineChart	PieChart	ScatterChart***

***StackedAreaChart	StackedBarChart***

## 2D Graphics *——2D图形*

JavaFX包含了一些特性，可以很容易地在屏幕上绘制2D图形。



## 3D Graphics *——3D图形*

JavaFX包含了一些特性，可以很容易地在屏幕上绘制3D图形。

## Audio*——音频*

JavaFX包含的特性使得在JavaFX应用程序中很容易播放音频。这在游戏或教育应用中非常有用。

## Video*——视频*

JavaFX包含的特性使得在JavaFX应用程序中播放视频变得容易。这在流媒体应用程序、游戏或教育应用程序中通常很有用

## WebView

JavaFX包含一个WebView组件，能够显示网页(HTML5、CSS等)。JavaFX WebView组件是基于WebKit引擎的，WebKit是Chrome和Safari中使用的网页渲染引擎。WebView组件使混合桌面应用程序和web应用程序成为可能。例如，如果你已经有了一个像样的web应用程序，但需要一些只有桌面应用程序才能提供的功能——比如磁盘访问、与HTTP以外的其他网络协议通信(如UDP、IAP等)。

