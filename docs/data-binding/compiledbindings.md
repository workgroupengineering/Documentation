# Compiled Bindings

Bindings defined in the XAML are using reflection in order to find the requested property in your ViewModel, read or update the data. In Avalonia you can also use compiled bindings, which has some benefits:
  * If you use compiled bindings and the property you bind to is not found, the application will crash. Hence you get a much better debugging experience.
  * Reflection is known to be slow ([see this article on codeproject.com](https://www.codeproject.com/Articles/1161127/Why-is-reflection-slow)). Using compiled bindings can therefore improve the performance of your application. 
 
## How to enable / disable compiled bindings

Compiled bindings are not enabled by default. To enable compiled bindings, you need to define the `DataType` 



---------
--------

You bind in XAML using the `{Binding}` markup extension. By using bindings \(assuming you've implemented [change notifications](https://docs.avaloniaui.net/docs/data-binding/change-notifications)\) any changes to the data context will automatically be updated in the control.






By default a binding binds to a property on the [`DataContext`](https://docs.avaloniaui.net/docs/data-binding/the-datacontext), e.g.:

```markup
<!-- Binds to the TextBlock's DataContext.Name property -->
<TextBlock Text="{Binding Name}"/>

<!-- Which is the same as ('Path' is optional) -->
<TextBlock Text="{Binding Path=Name}"/>
```

An empty binding binds to DataContext itself

```markup
<!-- Binds to the TextBlock's DataContext property -->
<TextBlock Text="{Binding}"/>

<!-- Which is the same as -->
<TextBlock Text="{Binding .}"/>
```

We call the property on the control the binding _target_ and the property on the `DataContext` the binding _source_.

## Binding Path <a id="binding-path"></a>

The binding path above can be a single property, or it can be a chain of properties. For example if the object assigned to the `DataContext` has a `Student` property, and the value of this property has a `Name`, you can bind to the student name using:

```markup
<TextBlock Text="{Binding Student.Name}"/>
```

You can also include array/list indexers in binding paths:

```markup
<TextBlock Text="{Binding Students[0].Name}"/>
```

## Binding Modes <a id="binding-modes"></a>

You can change the behavior of a `{Binding}` by specifing a binding `Mode`:

```markup
<TextBlock Text="{Binding Name, Mode=OneTime}">
```

The available binding modes are:

| Mode | Description |
| :--- | :--- |
| `OneWay` | Changes to the source are automatically propagated to the target |
| `TwoWay` | Changes to the source are automatically propagated to the target and vice-versa |
| `OneTime` | The value from the source is propagated at initialization to the target and subsequent changes are ignored |
| `OneWayToSource` | Changes to the target are propagated to the source |
| `Default` | The binding mode is based on the property |

The `Default` mode is assumed if one is not specified. This mode is generally `OneWay` for control properties that do not change due to user input \(e.g. `TextBlock.Text`\) and `TwoWay` for control properties that _do_ change due to user input \(e.g. `TextBox.Text`\).

