---
description: >-
  Learn to leverage your existing knowledge of WPF to kick start your journey
  with Avalonia.
---

# 🖥 WPF Developers Tips

Avalonia is in general very similar to WPF, but you will find differences. Here are the most common:

{% content-ref url="styling.md" %}
[styling.md](styling.md)
{% endcontent-ref %}

{% content-ref url="datatemplates.md" %}
[datatemplates.md](datatemplates.md)
{% endcontent-ref %}

{% content-ref url="hierachicaldatatemplate.md" %}
[hierachicaldatatemplate.md](hierachicaldatatemplate.md)
{% endcontent-ref %}

{% content-ref url="uielement-frameworkelement-and-control.md" %}
[uielement-frameworkelement-and-control.md](uielement-frameworkelement-and-control.md)
{% endcontent-ref %}

{% content-ref url="dependencyproperty.md" %}
[dependencyproperty.md](dependencyproperty.md)
{% endcontent-ref %}

{% content-ref url="grid.md" %}
[grid.md](grid.md)
{% endcontent-ref %}

{% content-ref url="itemscontrol.md" %}
[itemscontrol.md](itemscontrol.md)
{% endcontent-ref %}

{% content-ref url="tunnelling-events.md" %}
[tunnelling-events.md](tunnelling-events.md)
{% endcontent-ref %}

{% content-ref url="class-handlers.md" %}
[class-handlers.md](class-handlers.md)
{% endcontent-ref %}

{% content-ref url="propertychangedcallback.md" %}
[propertychangedcallback.md](propertychangedcallback.md)
{% endcontent-ref %}

{% content-ref url="rendertransforms-and-rendertransformorigin.md" %}
[rendertransforms-and-rendertransformorigin.md](rendertransforms-and-rendertransformorigin.md)
{% endcontent-ref %}

# Dispatcher changes

If you use `Application.Current.Dispatcher`, you should use `Dispatcher.UIThread` instead which provide similar facilities.

**WPF**
```
Application.Current.Dispatcher.InvokeAsync(handler, DispatcherPriority.Background);
```

**Avalonia**
```
Dispatcher.UIThread.InvokeAsync(handler, DispatcherPriority.Background);
```

If you previously access dispatcher on the control itself, you should use global static instance `Dispatcher.UIThread` too.

**WPF**
```
this.Dispatcher.InvokeAsync(handler, DispatcherPriority.Background);
```

**Avalonia**
```
Dispatcher.UIThread.InvokeAsync(handler, DispatcherPriority.Background);
```

In more details, it's explained in the [Accessing the UI thread](../../guides/basics/accessing-the-ui-thread.md) article.

# Visibility of elements

WPF has uses `Visibility` property which can be `Collapsed`, `Hidden` or `Visible`. Avalonia uses simpler and more intuitive model `bool IsVisible`.

# Binding

**WPF**
```
<TextBox Name="MyTextbox" Text="{Binding ElementName=searchTextBox, Path=Text}"" />
```

**Avalonia**
```
<TextBox Name="MyTextbox" Text="{Binding #searchTextBox.Text}" />
```

# Handling attachment to visual tree

There no events like `Loaded`/`Unloaded` in Avalonia, but you can override `OnAttachedToVisualTree`/`OnDetachedFromVisualTree` on the control, to know when control attached to virtual tree, or detatched from it. Alternatively you can use `TemplateApplied` instead of `Loaded` event.

**WPF**
```
Unloaded += OnControl_Unloaded;
Loaded += OnControl_Loaded;

private void OnControl_Loaded(object sender, RoutedEventArgs e)
{
    // Handle control loaded event.
}

private void OnControl_Unloaded(object sender, RoutedEventArgs e)
{
    // Handle control unload event.
}
```

**Avalonia**
```
TemplateApplied += OnControl_Loaded;
private void BuildControl_Loaded(object sender, RoutedEventArgs e)
{

}
// or
protected override void OnAttachedToVisualTree(VisualTreeAttachmentEventArgs e)
{
    // Handle control loaded event.
}

// Use this instead of Unloaded event.
protected override void OnDetachedFromVisualTree(VisualTreeAttachmentEventArgs e)
{
    // Handle control unload event.
}
```
That mean that you cannot subscribe to tree attachment/detachment events for other controls.


# Tooltips

Avalonia controls does not have `ToolTip` property like WPF. Instead you should use `ToolTip.Tip`

**WPF**
```csharp
<Button ToolTip="Save file as..." />
```

**Avalonia**
```csharp
<Button ToolTip.Tip="Save file as..." />
```

# TextRun decorations

**WPF**
```csharp
TextRunProperties.SetTextDecorations(TextDecorations.Underline);
```

**Avalonia**
```csharp
TextRunProperties.Underline = true;
```