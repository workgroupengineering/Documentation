# 👋 Introduction to Avalonia

## Welcome

Welcome to Avalonia - the best open source, easy to learn .NET C\# multiplatform package for desktop \(Windows, Mac and Linux\)  development.

* Avalonia is being developed very fast by [extremely bright people](https://github.com/AvaloniaUI/Avalonia/graphs/contributors).
* Avalonia is [100% open source - and will continue as an open source project](https://github.com/AvaloniaUI/Avalonia) and has great and constantly expanding documentation and a great number of open source samples showing how to use Avalonia.
* Avalonia has a decent [free support on Avalonia Gitter](https://gitter.im/AvaloniaUI/Avalonia), one can also post questions on [Avalonia Github Discussions](https://github.com/AvaloniaUI/Avalonia/discussions). If you're in need of more support you can opt for a  [paid support plan](https://avaloniaui.net/support.html) which helps support the continued growth of the project.
* Avalonia has Visual Studio and Rider support for creating XAML files while having advantage of XAML IntelliSense. Visual Studio also has a designer view available.
* Avalonia has a tool that facilitate the visual development and debugging called [DevTools](docs/getting-started/developer-tools.md). This tool is also multiplatform - meaning you can use it on Mac and Linux and completely open source.

If you're familiar with WPF or UWP then you should feel right at home with Avalonia. Although Avalonia is not API compatible with either of these frameworks \(and so controls can't be used without porting\), there's a lot of similarity. If you're a WPF user we have a [page which describes the main differences between WPF and Avalonia](misc/wpf/).


## Why Avalonia is a Hit

* Avalonia allows creating applications that look and behave the same on most popular Desktop and Mobile platforms \(Windows, Mac, various flavors of Linux\) while also allowing the platform specific customizations.
* Avalonia is supported by the following companies:

  [![](.gitbook/assets/se.png)](https://www.se.com/us/en/) 
  [![](.gitbook/assets/jblogo%20%282%29.png)](https://www.jetbrains.com/) 
  [![](.gitbook/assets/unitylogo.png)](https://unity.com/) 
  [![](.gitbook/assets/logo_thales_500.png)](https://www.thalesgroup.com/) 
  [![](.gitbook/assets/synergy-logo.png)](https://synergysports.com/) 
  [![](.gitbook/assets/gritworld-logo.png)](https://en.gritworld.com/) 
  [![](.gitbook/assets/wasabi-wallet-logo.svg)](https://www.wasabiwallet.io/) 
  [![](.gitbook/assets/mailbird-logo.png)](https://www.getmailbird.com/) 

  and many other smaller companies.

* Several extremely popular .NET open source projects have been ported to Avalonia. Among them are
  * [AvalonEdit](http://avalonedit.net/) - the port is available as [AvaloniaEdit](https://github.com/AvaloniaUI/AvaloniaEdit) - Rich Text Editor.
  * [RoslynPad](https://roslynpad.net/) - C\# code editor with intellisense.
* Avalonia \(just like WPF and Silverlight\) is fully compositional: you can create a button out of Avalonia primitives in a fashion similar to creating a complex page, while its competitors \(Web, Xamarin and Java\) packages are not compositional to the same degree as will be detailed later.
* Avalonia UI, unlike JavaScript has full advantage of a strongly typed language. Also Avalonia has full advantage of a compiled-to-binary code language.
* Avalonia is an open source multiplatform descendant of great Microsoft packages - WPF and Silverlight which brought the UI development on a completely new level creating a set of new concepts and which allow to create a full blown UI application in fraction of time and effort in comparison to other technologies. Here is the list of some of the concepts:

  * Visual and Logical Trees
  * Attached or Dependency Properties which can be defined outside of the object on which they are used and do not take any extra memory unless they are assigned a non-default value and have a special event to fire when their values change.
  * Attached Routed Events that can be defined outside of the objects that fire them and can propagate and be handled up and down on the trees.
  * Bindings and the Related MVVM pattern
  * ControlTemplates
  * DataTemplates
  * Styles
  * Behaviors - way to modify and augment the behavior of a C\# class without modifying the class itself by using the events.

  All these paradigms have been implemented for multiple platforms in Avalonia.

## Supported .NET Version

Avalonia is supported for .NET Core 3.1 and higher.

## Supported Platforms

Avalonia is supported on the following platforms:

* Windows 8 and higher
* MaxOS High Sierra 10.13 and higher
* for Linux:
  * Debian 9 \(Stretch\) and higher
  * Ubuntu 16.5 and higher
  * Fedora 30 and higher

## Supported Development Environments

The following environments support Avalonia XAML with IntelliSense:

* Visual Studio 2017 and higher \(with or without Resharper 2020.3\). Avalonia Visual Designer is also supported.
* JetBrains Rider 2020.3 and higher \(Avalonia Designer coming soon to Rider\).

## Installing Avalonia Extension for Visual Studio

In order to start using Avalonia, you need to set up your development environment \(Visual Studio or Rider\) first. 

You achieve in in Visual Studio by installing "Avalonia for Visual Studio" extension as described below.

Open you VS extension manager \(in VS 2019 it is located under Extensions menu\). Find the extension called "Avalonia for Visual Studio" online and install it:

![Installing Avalonia for Visual Studio extension](.gitbook/assets/installavaloniaextension.png)

Avalonia for Visual Studio extension installs the templates for creating the Avalonia UI projects and various XAML based files and it also installs the intellisense for XAML. 

## Creating and Running a Simple Avalonia Application under Visual Studio

Once you have installed the "Avalonia for Visual Studio" extension, start Visual Studio choose New-&gt;Project menu item for the File menu:

![Creating new Project in Visual Studio](.gitbook/assets/createnewproject.png)

and choose "Avalonia Application" project type:

![Choosing Avalonia Application Project Type](.gitbook/assets/avaloniaappprojecttype.png)

 Press button "Next" and choose the name and location for your first Avalonia project, e.g:

![Creating simple avalonia project](.gitbook/assets/createsimpleavaloniaproject.png)

Pressing button "Create" will create the Avalonia Application project. It will have dependencies on three Avalonia nuget packages:  `Avalonia`, `Avalonia.Desktop` and `Avalonia.Diagnostics`:

![Avalonia Application project Files and Dependencies](.gitbook/assets/projectpackagesandfiles.png)

The newly created project contains five files:  _App.axaml_, _App.axaml.cs_, _MainWindow.axaml_, _MainWindow.axaml.cs_ and _Program.cs_. Note that Avalonia XAML files have "._axaml_" extension \(unlike WPF XAML files that have "._xaml_" extension\). The Avalonia XAML syntax is very similar to WPF XAML syntax, with some specialty when it comes to the so called Style Selectors \(which will be explained in the future\). 

Among the five files listed above, it is likely you will have to modify _MainWindow.axaml_ and _MainWindow.axaml.cs_ files most, then perhaps slightly change also _App.axaml_ and _App.axaml.cs_ files and you probably won't have to change _Program.cs_ file ever.

 Open _MainWindow.xaml_ file and replace its content \(which by default consists of "`Welcome to Avalonia!`" text\) with the following code:

```markup
<Button x:Name="CloseWindowButton"
        Content="Close Window"
        HorizontalAlignment="Center"
        VerticalAlignment="Center"
        Padding="10,5"/>
```

If you run the application now, there will be a Button in the middle of the window \(which is ensured by Horizontal and Vertical Alignments - the words "**Close Window**" will be written in the middle of the button \(`Button`'s content\) and the margins from the "**Close Button**" text to the sides of the button will be 10 generic pixels on the right and left and 5 generic pixels at the top and the bottom \(specified by the `Padding` property\):

![](.gitbook/assets/windowwithbutton.png)

 So far so good, but if you press the button, nothing is going to happen. We need to try to connect the button's "Click" event to the action that closes the window. In this first sample, we are going to employ the simplest, but also the **worst** way of achieving such purpose - the code behind. File _MainWindow.xaml.cs_ contains the so called "code behind" - C\# code for the _MainWindow.xaml_ file:

```csharp
public partial class MainWindow : Window
{
    public MainWindow()
    {
        InitializeComponent();
#if DEBUG
        this.AttachDevTools();
#endif
    }

    private void InitializeComponent()
    {
        AvaloniaXamlLoader.Load(this);
    }
}
```

 We named out button "`CloseWindowButton`". In WPF, the corresponding class member would have been generated. `Avalonia`, still does not include this feature, but we can easily find the button by adding the following line:

```csharp
var button = this.FindControl<Button>("CloseWindowButton");
```

after `InitializeComponent();` is called within the constructor. Then we can add a handler to the button's `Click` event: `button.Click += Button_Click;`. Finally, within the handler we can call `Close()` method on the window:

```csharp
private void Button_Click(object? sender, RoutedEventArgs e)
{
    this.Close();
}
```

 The full code for `MainWindow` constructor and the handler will look like below:

```csharp
public MainWindow()
{
    InitializeComponent();
#if DEBUG
    this.AttachDevTools();
#endif
    var button = this.FindControl<Button>("CloseWindowButton");

    button.Click += Button_Click;
}

private void Button_Click(object? sender, RoutedEventArgs e)
{
    this.Close();
}
```

Now if you run the application and press "**Close**" button, the window will close.

The code for this application is located under [_NP.Demos.SimpleAvaloniaProject_](https://github.com/npolyak/NP.CodeForAvaloniaInEasySampleArticle/tree/main/NP.Demos.SimpleAvaloniaProject), but if you are new to Avalonia and WPF, it is imperative that you should go over the exercise above.
