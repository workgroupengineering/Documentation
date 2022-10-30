# Mouse & Pointer devices

Avalonia operates on the abstraction called pointer devices. These devices including, but not limited to mouse, joystic, touchpad etc. Each control in Avalonia provides following events which allow developer subscribe to the pointer device movements, clicks and wheel movements: 
- PointerEnter
- PointerLeave
- PointerMoved
- PointerPressed
- PointerReleased
- PointerWheelChanged

Example how to react on mouse button pressed.

```csharp
control.PointerPressed += (args) =>
{
    var point = args.GetCurrentPoint(control);
    var x = point.Position.X;
    var y = point.Position.Y;
    if (point.Properties.IsLeftButtonPressed) {
        // left button pressed
    }
    if (point.Properties.IsRightButtonPressed) {
        // right button pressed
    }
}
```

In the example above, coordinates `x` and `y` are relatively to control origin. If you want coordinates relative to your window, you may pass it to `PointerEventArgs.GetCurrentPoint` method like this: `var pointWindowCoords = args.GetCurrentPoint(window);`

### Reference <a id="reference"></a>

[Control](http://reference.avaloniaui.net/api/Avalonia.Controls/Control/)
[PointerEventArgs](http://reference.avaloniaui.net/api/Avalonia.Input/PointerEventArgs/)
