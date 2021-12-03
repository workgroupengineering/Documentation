# Hotkeys

You can assign a Hotkey to any Control that implements `ICommandSource`.

```markup
<Menu>
    <MenuItem Header="_File">
        <MenuItem x:Name="SaveMenuItem" Header="_Save"/>
    </MenuItem>
</Menu>
```

```csharp
this.WhenActivated(disposables =>
{
    this.BindCommand(ViewModel, vm => vm.Save, view => view.SaveMenuItem)
        .DisposeWith(disposables);
});

InitializeComponent();

HotKeyManager.SetHotKey(SaveMenuItem, new KeyGesture(Key.S, KeyModifiers.Control));
```

### Reference <a id="reference"></a>

[HotKeyManager](http://reference.avaloniaui.net/api/Avalonia.Controls/HotKeyManager/)

### Source code <a id="source-code"></a>

[HotkeyManager.cs](https://github.com/AvaloniaUI/Avalonia/blob/master/src/Avalonia.Controls/HotkeyManager.cs)
