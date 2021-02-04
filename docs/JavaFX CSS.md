# JavaFX CSS Styling

>
>
>JavaFx 允许你通过CSS来设计JavaFX组件，就像你可以使用CSS来给HTML添加样式一样。JavaFX使用的CSS语法和web相同，但是这些CSS属性是用在JavaFX组件上的，因此在名称上和使用在web上的有细微的差别。
>
>使用CSS来给JavaFX添加样式可以帮助我们将样式从应用代码中分开。这将会带来更加清晰的代码并且使更改应用的样式更加容易。我们不必查看Java代码来更改样式，不仅如此，通过使用共享的CSS样式表，我们还可以同时更改多个组件的样式。
>
>在这章JavaFX CSS Styling中，我们将深入了解多种将CSS样式应用到Application中的途径，以及了解支持与不支持的CSS属性。JavaFX的CSS特性非常先进，所以使用CSS来设计样式完全没问题。
>
>阅读接下来的内容，请确保对CSS语法、CSS规则和CSS属性有些了解，这里有由原作者完成的[CSS教程(英文原版)](http://tutorials.jenkov.com/css/index.html)。

## CSS Styling Methods

以下列出的是应用CSS样式的几种情况（规则）。

- Default CSS stylesheet *——默认CSS样式*
- Scene specific CSS stylesheet *——Scene特定的CSS样式*
- Parent specific CSS stylesheet *——*`Parent`类的特定CSS样式
- Component  style property——*组件单独设置CSS样式*

在接下来几个部分会简单解释每一个CSS方法是如何工作的。

### Default CSS Stylesheet*——默认CSS样式*

JavaFX应用自带默认的CSS样式。如果我们不任何样式的话，JavaFX会将将默认样式应用到组件上。JavaFX8的默认样式表称为Modena，位于JavaFX JAR文件中。

### Scene Specific CSS Stylesheet *——Scene特定的CSS样式*

你可以在JavaFX的Scene对象上设置CSS样式。所有添加到这个Scene对象的组件都会应用这个CSS样式来覆盖默认的样式。

这是示例

```kotlin
scene.stylesheets.add("style/1/button-styles.css")
```

这个示例让JavaFX去指定的资源目录*style/1*寻找文件*button-styles.css*。这个指向CSS的字符串被解释为了URL，所以也可以使用系统的文件的文件全路径。但是最好将CSS文件视作资源，并将他们和应用程序的代码绑定在一起。使用应用的用户通常不需要修改应用的样式，所以不需要在代码之外分发CSS文件。

### Parent Specific CSS Stylesheets*——*`Parent`类的特定CSS样式

我们可以给`Parent`类的任意子类添加CSS样式。`Parent`类是所有可以添加*children*的组件的父类。这个CSS样式会应用它的*Children*。在`Parent`类的子类中添加的CSS样式通常会优先于应用在Scene和默认的CSS样式。

`layout`类是`Parent`类的子类中典型的例子。如果你为它添加CSS样式。它的*Children*都会应用此样式。

下面是示例

```kotlin
val button = Button("Button")
val anotherButton = Button("Another button")
val vBox = VBox(button,anotherButton)
vbox.stylesheets.add("style1/button-styles.css")
```

文件*style1/button-styles.css*中的样式被应用在了*vBox*上，那么*button*和*anotherButton*都将应用次样式文件。

### Component Style Property——*组件单独设置CSS样式*

我们可以直接给某一特定的组件设置CSS样式。这是通过在组件的*style*属性中添加包含CSS属性的字符串实现的。

通过style属性来设置样式是优先于以上的几种设置方式的。

下面是示例

```kotlin
val button = Button('button')
button.style="-fx-background-color:#0000ff"
```

>
>
>这个示例将通过*-fx-background-color*将按钮的背景颜色设置成蓝色。你可以设置多个CSS属性在这个*style*属性里，下面是设置多个属性的示例。

```kotlin
val styles = """
            -fx-background-color: #0000ff;
            -fx-border-color: #ff0000
        """
val button = Button("button")
button.style = styles
```

## JavaFX CSS Properties*——关于JavaFX中CSS属性命名*

如前所述，JavaFX有自己的一组属性。应用于JavaFX的CSS属性的命名与用于HTML的有些不同。但是JavaFX团队让JavaFX的CSS属性名保持和HTML的CSS属性名十分接近。如果你对HTML中的CSS属性名很熟悉，那么猜出JavaFX中对应的CSS属性名对你而言应该轻而易举。



