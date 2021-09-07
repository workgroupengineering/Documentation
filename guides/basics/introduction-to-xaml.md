# Introduction to XAML

Avalonia uses XAML to define user-interfaces. XAML is an XML-based markup language that is used by many UI frameworks.

This section is intended as a basic introduction to using XAML in Avalonia. For more information see the [Microsoft XAML documentation for WPF](https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/xaml-overview-wpf) or [Microsoft XAML documentation for UWP](https://docs.microsoft.com/en-us/windows/uwp/xaml-platform/xaml-overview) - many of the concepts are the same between frameworks.

## XAML or AXAML file? <a id="xaml-or-axaml-file"></a>

The traditional extension for XAML files is `.xaml` but due to problems with Visual Studio we have been forced to move to our own `.axaml` extension for Avalonia XAML files. From version 0.9.11 Avalonia XAML files created in Visual Studio use the `.axaml` extension and from version 0.10 all of our templates will be standardized on using the `.axaml` extension.

For more information see [https://github.com/AvaloniaUI/Avalonia/issues/4102](https://github.com/AvaloniaUI/Avalonia/issues/4102).

Both `.xaml` and `.axaml` will be supported going foward, so feel free to use the extension you prefer.

## Format of an Avalonia XAML File <a id="format-of-an-avalonia-xaml-file"></a>

A basic Avalonia XAML file looks like this:

```text
<Window xmlns="https://github.com/avaloniaui"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        x:Class="AvaloniaApplication1.MainWindow">
</Window>
```

There are three parts to this file:

* The root element `Window` - this descibes the type of the root control in the XAML file; in this case [`Window`](http://reference.avaloniaui.net/api/Avalonia.Controls/Window/)
* `xmlns="https://github.com/avaloniaui"` - this is the XAML namespace for Avalonia. Without this, the file will not be recognised as an Avalonia XAML document.
* `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` - this is the XAML-language XAML namespace. This isn't strictly necessary, but you will probably need it for accessing certain features of the XAML language.
* `x:Class="AvaloniaApplication1.MainWindow"` - this tells the XAML compiler where to find the associated class for this file, defined in [code-behind](https://docs.avaloniaui.net/guides/basics/code-behind)

## Declaring Controls <a id="declaring-controls"></a>

Controls are added to the XAML by adding an XML element with the control's class name. For example to add a button as the child of the window you would write:

```text
<Window xmlns="https://github.com/avaloniaui"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Button>Hello World!</Button>
</Window>
```

See the [controls documentation](https://docs.avaloniaui.net/docs/controls) for a list of the controls included with Avalonia.

## Setting Properties <a id="setting-properties"></a>

You can set a property of a control by adding an XML attribute to an element. For example to create a button with a blue background you could write:

```text
<Window xmlns="https://github.com/avaloniaui"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Button Background="Blue">Hello World!</Button>
</Window>
```

You can also use _property element syntax_ for setting properties. For more information see the [WPF documentation](https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/xaml-overview-wpf#property-element-syntax).

## Content Properties <a id="content-properties"></a>

You may notice that the button above has its "Hello World!" content placed directly inside the XML element. This could also be written as a property using:

```text
<Window xmlns="https://github.com/avaloniaui"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Button Content="Hello World"/>
</Window>
```

This is because [`Button.Content`](http://reference.avaloniaui.net/api/Avalonia.Controls/ContentControl/) is declared as a _`[Content]` Property_ which means that any content placed inside its XML tag will be assigned to this property.

## Binding <a id="binding"></a>

You can bind a property using the `{Binding}` markup extension:

```text
<Window xmlns="https://github.com/avaloniaui"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
    <Button Content="{Binding Greeting}"/>
</Window>
```

For more information, see the [binding documentation](https://docs.avaloniaui.net/docs/data-binding).

## Code-behind <a id="code-behind"></a>

Many XAML files also have an associated _code-behind_ file which usually has the extension `.xaml.cs`. For more information see the [codebehind documentation](https://docs.avaloniaui.net/guides/basics/code-behind).

