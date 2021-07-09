# Transitions

Transitions in Avalonia are also heavily inspired by CSS Animations. They listen to any changes in target property's value and subsequently animates the change according to its parameters. They can be defined on any `Control` via `Transitions` property:

```markup
<Window xmlns="https://github.com/avaloniaui">
    <Window.Styles>
        <Style Selector="Rectangle.red">
            <Setter Property="Height" Value="100"/>
            <Setter Property="Width" Value="100"/>
            <Setter Property="Background" Value="Red"/>
            <Setter Property="Opacity" Value="0.5"/>
        </Style>
        <Style Selector="Rectangle.red:pointerover">
            <Setter Property="Opacity" Value="1"/>
        </Style>
    </Window.Styles>

    <Rectangle Classes="red">
        <Rectangle.Transitions>
            <Transitions>
                <DoubleTransition Property="Opacity" Duration="0:0:0.2"/>
            </Transitions>
        </Rectangle.Transitions>
    </Rectangle>

</Window>
```

The above example will listen to changes in the `Rectangle`'s `Opacity` property, and when the value changes, apply a smooth transition from the old value to the new value over 2 seconds.

Transitions can also be defined in any style by using a `Setter` with `Transitions` as the target property and encapsulating them in a `Transitions` object, like so:

```markup
<Window xmlns="https://github.com/avaloniaui">
    <Window.Styles>
        <Style Selector="Rectangle.red">
            <Setter Property="Height" Value="100"/>
            <Setter Property="Width" Value="100"/>
            <Setter Property="Background" Value="Red"/>
            <Setter Property="Opacity" Value="0.5"/>
            <Setter Property="Transitions">
                <Transitions>
                    <DoubleTransition Property="Opacity" Duration="0:0:0.2"/>
                </Transitions>
            </Setter>
        </Style>
        <Style Selector="Rectangle.red:pointerover">
            <Setter Property="Opacity" Value="1"/>
        </Style>
    </Window.Styles>

    <Rectangle Classes="red"/>

</Window>
```

Every transition has a `Property`, `Delay`, `Duration` and an optional `Easing` property.

`Property` refers to a transition's target for listening and animating values upon.

`Delay` refers to the amount of time before the transition is applied to the target.

`Duration` refers to the amount of time that the transition plays.

The easing functions are the same as those described in [Keyframe Animations](https://docs.avaloniaui.net/docs/animations/keyframe-animations#easings).

The following transition types are available. The correct type must be used depending on the type of the property being animated.

* `DoubleTransitions`: For `double` target properties
* `FloatTransitions`: For `float` target properties
* `IntegerTransitions`: For `int` target properties
* `TransformOperationsTransition` : For `ITransform` properties

## Transitioning Render Transforms

Render transforms applied to controls using CSS-like syntax can be transitioned. The following example shows a Border which rotates 45 degrees when the pointer is hovered over it:

{% tabs %}
{% tab title="XAML" %}
```markup
<Border Width="100" Height="100" Background="Red">
    <Border.Styles>
        <Style Selector="Border">
            <Setter Property="RenderTransform" Value="rotate(0)"/>
        </Style>
        <Style Selector="Border:pointerover">
            <Setter Property="RenderTransform" Value="rotate(45deg)"/>
        </Style>
    </Border.Styles>
    <Border.Transitions>
        <Transitions>
            <TransformOperationsTransition Property="RenderTransform" Duration="0:0:1"/>
        </Transitions>
    </Border.Transitions>
</Border>
```
{% endtab %}

{% tab title="C\#" %}
```
new Border
{
    Width = 100,
    Height = 100,
    Background = Brushes.Red,
    Styles =
    {
        new Style(x => x.OfType<Border>())
        {
            Setters =
            {
                new Setter(
                    Border.RenderTransformProperty,
                    TransformOperations.Parse("rotate(0)"))
            },
        },
        new Style(x => x.OfType<Border>().Class(":pointerover"))
        {
            Setters =
            {
                new Setter(
                    Border.RenderTransformProperty,
                    TransformOperations.Parse("rotate(45deg)"))
            },
        },
    },
    Transitions = new Transitions
    {
        new TransformOperationsTransition
        {
            Property = Border.RenderTransformProperty,
            Duration = TimeSpan.FromSeconds(1),
        }
    }
};
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Avalonia also supports WPF-style render transforms such as `otateTransform`, `ScaleTransform` etc. These transforms cannot be transitioned: always use the CSS-like format if you want to apply a transition to a render transform.
{% endhint %}



