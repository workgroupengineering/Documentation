# Implementing IDataTemplate for advanced scenarios

If you need more control over your `DataTemplate` you can do this by creating a class which implements the `IDataTemplate`-interface. With this interface you can create your own `DataTemplate` not only respecting the `DataType` of your data, but also its properties or whatever you like. 

To use this interface you must implement the following two members in your class:
- `public bool Match(object data) { ... }` you need to check in this method if the provided data matches your `IDataTemplate` or not. You need to return true if the data matches, otherwise false.
- `public IControl Build(object param) { ... }` In this method you need to build and return the control which represents your data. 

### Basic Example

Below is a very basic sample implementation of the `IDataTemplate`-interface:

```csharp
// remember to import the needed namespace
// using Avalonia.Controls.Templates;

public class MyDataTemplate : IDataTemplate
{
    public IControl Build(object param)
    {
        // build the control to display
        return new TextBlock() { Text = (string)param };
    }

    public bool Match(object data)
    {
        // Check if we can accept the provided data
        return data is string;
    }
}
```

You can now use the class `MyDataTemplate` in your view like this:

```markup
<!-- remember to add the needed prefix in your view -->
<!-- xmlns:dataTemplates="using:MyApp.DataTemplates" -->

<ContentControl Content="{Binding MyContent}">
	<ContentControl.ContentTemplate>
		<dataTemplates:MyDataTemplate />
	</ContentControl.ContentTemplate>
</ContentControl>
```


### Advanced Example

Sometimes you may want to display a different Control for different states of your `ViewModel`. Let's assume you have a Property which is an `enum` called `ShapeType`, defined like this:

```csharp
public enum ShapeType
{
    RedCircle,
    RedSquare, 
    BlueCircle,
    BlueSquare
}
```

We use this `enum` in our `ViewModel` as a property:

```csharp
// In our sample we use ReactiveUI but you don't need to do it.

private ShapeType _ShapeType;

/// <summary>
/// Gets or sets the shape type to display
/// </summary>
public ShapeType ShapeType
{
    get { return _ShapeType; }
    set { this.RaiseAndSetIfChanged(ref _ShapeType, value); }
}
```

In our view we want to show a red circle if the user selects `ShapeType.RedCircle` and we want to show a blue square if the user selects `ShapeType.BlueSquare`. To achieve this will create a class called `ShapesTemplateSelector`, where have a `Dictionary` which stores the shape representations we want to look up.

```csharp
// remember to import the needed namespace
// using Avalonia.Controls.Templates;

public class ShapesTemplateSelector : IDataTemplate
{
    // This Dictionary should store our shapes. We mark this as [Content], so we can directly add elements to it later.
    [Content]
    public Dictionary<string, IDataTemplate> AvailableTemplates { get; } = new Dictionary<string, IDataTemplate>();

    // Build the DataTemplate here
    public IControl Build(object param)
    {
        var key = param.ToString(); // Our Keys in the dictionary are strings, so we call .ToString() to get the key to look up
        if(key is null) // If the key is null, we throw an ArgumentNullException
        {
            throw new ArgumentNullException(nameof(param));
        }
        return AvailableTemplates[key].Build(param); // finally we look up the provided key and let the System build the DataTemplate for us
    }

    // Check if we can accept the provided data
    public bool Match(object data)
    {
         // Our Keys in the dictionary are strings, so we call .ToString() to get the key to look up
        var key = data.ToString(); 
        
        return data is ShapesEnum                      // the provided data needs to be our enum type
               && !string.IsNullOrEmpty(key)           // and the key must not be null or empty
               && AvailableTemplates.ContainsKey(key); // and the key must be found in our Dictionary
    }
}
```

Now we will setup the `ShapesTemplateSelector` in the `DataTemplates`-section of our `App.axaml`: 

```markup
<!-- remember to add the needed prefix in your view -->
<!-- xmlns:dataTemplates="using:MyApp.DataTemplates" -->
<!-- xmlns:model="using:MyApp.Model" -->

<Application.DataTemplates>
	<dataTemplates:ShapesTemplateSelector>
		<DataTemplate x:Key="RedCircle" DataType="model:ShapesEnum">
			<Ellipse Width="50" Height="50" Fill="Red" Stroke="DarkRed" StrokeThickness="2" />
		</DataTemplate>
		<DataTemplate x:Key="BlueCircle" DataType="model:ShapesEnum">
			<Ellipse  Width="50" Height="50" Fill="Blue" Stroke="DarkBlue" StrokeThickness="2" />
		</DataTemplate>
		<DataTemplate x:Key="RedSquare" DataType="model:ShapesEnum">
			<Rectangle  Width="50" Height="50" Fill="Red" Stroke="DarkRed" StrokeThickness="2" />
		</DataTemplate>
		<DataTemplate x:Key="BlueSquare" DataType="model:ShapesEnum">
			<Rectangle  Width="50" Height="50" Fill="Blue" Stroke="DarkBlue" StrokeThickness="2" />
		</DataTemplate>
	</dataTemplates:ShapesTemplateSelector>
</Application.DataTemplates>
```

Now we can will create a `ComboBox` which the user can use to select a `ShapeType`:

```markup
<!-- remember to add the needed prefix in your view -->
<!-- xmlns:model="using:MyApp.Model" -->

<StackPanel>

	<TextBlock Text="Select a Shape" />

	<ComboBox SelectedIndex="0">
		<model:ShapeType>RedCircle</model:ShapeType>
		<model:ShapeType>BlueCircle</model:ShapeType>
		<model:ShapeType>RedSquare</model:ShapeType>
		<model:ShapeType>BlueSquare</model:ShapeType>
	</ComboBox>
</StackPanel>
```

Our final result looks like this: 

![](../../.gitbook/assets/IDataTemplateExample.png)