# Data Binding

Avalonia includes comprehensive support for [binding](http://avaloniaui.net/docs/binding/bindings) between controls and to aribtrary .NET objects. Data binding can be set up [in XAML](http://avaloniaui.net/docs/binding/bindings) or [in code](http://avaloniaui.net/docs/binding/binding-from-code) and supports:

* Multiple binding modes: one way, two way, one-time and one-way to source
* Binding to a [`DataContext`](http://avaloniaui.net/docs/binding/datacontext)
* Binding to [other controls](http://avaloniaui.net/docs/binding/binding-to-controls)
* Binding to [`Task`s and `Observables`](http://avaloniaui.net/docs/binding/binding-to-tasks-and-observables)
* Binding [converters](http://avaloniaui.net/docs/binding/converting-binding-values) and negating binding values

The following example shows a `TextBlock` when an associated `TextBox` is disabled, by using a binding:

```markup
<StackPanel>
    <TextBox Name="input" IsEnabled="False"/>
    <TextBlock IsVisible="{Binding !#input.IsEnabled}">Sorry, no can do!</TextBlock>
</StackPanel>
```

In this example, a binding is set up to the `IsEnabled` property of the `input` control using `#input.IsEnabled` and the value of that binding is negated and fed into the `TextBlock.IsVisible` property.

