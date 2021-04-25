# Binding to Tasks and Observables

You can subscribe to the result of a task or an observable by using the `^` stream binding operator.

For example if `DataContext.Name` is an `IObservable<string>` then the following example will bind to the length of each string produced by the observable as each value is produced

```markup
<TextBlock Text="{Binding Name^.Length}"/>
```

