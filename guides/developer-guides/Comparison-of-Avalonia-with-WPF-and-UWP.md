# Comparison of Avalonia with WPF and UWP

Originally based on [UWPvsWPF.md](https://github.com/robloo/PublicDocs/blob/master/UWPvsWPF.md) with Avalonia-specific changes. Licensed CC BY-SA 4.0

This section lists the main differences (primarily from a XAML viewpoint) between Avaloni, UWP and WPF.

Legend:

* ✔ Indicates the platform (defined by the Avalonia, WPF or UWP column) has the feature
* ✖ Indicates the feature is generally missing in the platform
* ⚡ Indicates the feature is only partially implemented compared to other platforms

## Markup Extensions

|Item|Avalonia|WPF|UWP|Notes|
|-----|:---:|:---:|:---:|----------|
|x:Uid for localization|✖|✖|✔|x:uid is a powerful localization system similar to what exists in Windows Forms. WPF is sorely missing this type of localization support. This is a clear advantage of UWP.
|x:Bind|✖|✖|✔|x:Bind has also become a powerful feature of UWP over WPF. Compiled bindings can be used for nearly anything and can replace other missing features like MultiBinding. Other advantages include debugging support as well as increased performance.
|x:Array|✖|✔|✖|x:Array isn't supported in UWP.
|x:Static|✔|✔|⚡|x:Static could be replaced with x:Bind
|x:Type|✔|✔|✖|
|Full Markup Extension|✔|✔|✖|UWP only implements a subset of the full markup extension support in WPF. This area needs to be expanded upon in the future.
|Compiled Bindings|✔|✖|✖|

## Binding

|Item|Avalonia|WPF|UWP|Notes|
|-----|:---:|:---:|:---:|----------|
|OneWayToSource BindingMode|✔|✔|✖|
|Binding to ConverterParameter|✔|✔|✖|
|MultiBinding / IMultiValueConverter|✔|✔|✖|Very useful feature in WPF for advanced binding scenarios no longer exists for UWP. UWP does have function binding with x:Bind though (Used to re-implement converter logic).
|ICommand|✔|✔|⚡|While the interface technically exists, ICommand is nothing like what it was in WPF. The programmer is now responsible for doing every little part of the command. This was improved in Windows 10 version 1809 which added XamlUICommand and StandardUICommand.
|RelativeSource / AncestorType|✔|✔|⚡|Not nearly as powerful in UWP, relative source only supports `{RelativeSource Self}` and `{RelativeSource TemplatedParent}` as compared to more powerful expressions in WPF like `{RelativeSource PreviousData}` or `{Binding RelativeSource={RelativeSource Mode=PreviousData, AncestorType={x:Type TextBox}}`.
|StringFormat|✔|✔|✖|XAML such as `{Binding DateValue, StringFormat=Date: {0:dddd yyyy-MM-dd}}` isn't supported in UWP and requires custom converters.
|Functions in binding|✖|✖|✔|x:Bind in UWP supports OneWay and TwoWay function binding that can replace converters.

## Styling

|Item|Avalonia|WPF|UWP|Notes|
|-----|:---:|:---:|:---:|----------|
|DataTriggers / PropertyTrigger / EventTrigger within Style.Triggers|✖|✔|✖|
|VisualStateManager|✖|⚡|✔|A different concept from WPF that takes the place of DataTriggers, this is very verbose and more often than not increases complexity compared to data triggers. @Felix-Dev VisualStateManager does exist in WPF (it was added in .NET Framework 4.0). It's not as elegant as in UWP though, i.e. it has no VisuaStateManager.Setters property. That means you have to use Storyboards to set your values.
|Implicit DataTemplate|✔|✔|✖|Set the DataType property of the DataTemplate to the corresponding type and the template is then applied automatically to all instances of that particular type
|Binding in Style setter|✔|✔|✖|Any other than TemplateBinding isn't support in a template/style within UWP
|BasedOn default Style|✖|✔|⚡|`BasedOn={StaticResource {x:Type TextBlock}` isn't supported in UWP but works in WPF. Instead, BasedOn requires the use of a key which is a problem as not all default styles define one. This is a specific example of the missing x:Type markup extension in UWP.

## Other

|Item|Avalonia|WPF|UWP|Notes|
|-----|:---:|:---:|:---:|----------|
|Coercion|✔|✔|✖|Coercion of Dependency Properties is not supported in UWP.
|Data (Input) Validation|✔|✔|✖|The entire WPF data validation system including the classes/inferfaces: ValidationRule (and all standard implementations), Binding.ValidationRules, IDataErrorInfo, INotifyDataErrorInfo, Binding.ValidatesOnNotifyDataErrors, etc. is not implemented in UWP. This will be added in WinUI 3.0 but the story for using this within the UWP app model with WinUI 3.0 is less clear.
|x:TypeArguments directive|✔|✔|✖|The TypeArguments directive isn't implemented in UWP which causes problems with generics. Missing this requires some work-arounds with classes and creating a non-generic class to use in XAML from a generic one.
|UIElement.IsVisible / IsVisibleChanged|✔|✔|✖|UWP has no way of tracking which controls are actually visible on the display. WPF has the UIElement.IsVisible property and the IsVisibleChanged event. This hinders the ability to optimize controls for performance.
|UIElement.Visibility / Visibility.Hidden|⚡|✔|⚡|UWP does not include the Visibility.Hidden enum value used for UIElement.Visibility. Hidden in WPF allowed a control to still be used in measure/layout but appear invisible when rendered for display.
|UIElement.Clip|✔|✔|⚡|Both WPF and UWP have UIElement.Clip properties. However, WPF can take any Geometry allowing for non-rectangular clipping. UWP can only use a RectangleGeometry for clipping. WPF: public Geometry UIElement.Clip, UWP: public RectangleGeometry UIElement.Clip
|UIElement.ClipToBounds|✔|✔|✖|In WPF it's possible to clip child contents to the parents bounds by setting ClipToBounds to True. UWP doesn't have this property at all. The work-around is to use UIElement.Clip which can only do rectangular clipping.
|LayoutTransform|✔|✔|✖|Layout transform is needed to transform elements before layouting. This allows for easily changing textbox direction and then putting it in a table. RenderTransform, as it applies after layout, does not resize parent controls for transformed children.
|VisualBrush / DrawingBrush|✔|✔|✖|VisualBrush is not a XAML brush in UWP. Instead, must fall back to composition brushes which are not 1:1 equivalent. DrawingBrush is not supported at all in UWP.
|Supplemental Shapes: Arrow, Callout, Star, etc|✔|✔|✖|Several shapes present in WPF are missing in UWP.
|Adorner|✔|✔|✖|[Adorners overview](https://docs.microsoft.com/en-us/dotnet/framework/wpf/controls/adorners-overview)
|Thickness|✔|✔|⚡|The Thickness struct exposes fields for Top, Bottom, Left and Right instead of dependency properties as in WPF. This means you cannot Bind or asign resources to an individual thickness parameter.
|Size / Rect / Point|✔|✔|✔|Size, Rect and Point are fully supported in both WPF and UWP. However, UWP uses single-precision float types for properties instead of double in WPF. This creates an incompatiblity when porting code.
|ItemsControl.AlternationIndex / ItemsControl.AlternationCount|✖|✔|✖|WPF has an easy way to change the style of items in a list using ItemsControl.AlternationIndex and ItemsControl.AlternationCount. This allows, for example, to change the background color of a listed item for even/odd entries. UWP doesn't support this at all in any controls. The partial work-around in UWP is to create a new control deriving from the framework's implementation and override the PrepareContainerForItemOverride() method.
|Custom Cursor at runtime|✔|✔|✖|
|Sub-pixel anti-aliasing|✔|✔|✖|Anti-aliasing in UWP along with rendering in general is poor compared to WPF. It's assumed this is for performance reasons on mobile devices and the web (Silverlight).
|Nested Types in XAML|✔|✔|✖|Nesting different types in XAML is generally not possible in UWP. Code such as `<ListBox.ItemsSource><x:Array><s:string>foo<s/:string><x/:Array></ListBox.ItemsSource>` works in WPF but not in UWP.
|Event Tunneling / Event Bubbling / Routed Events|✔|✔|⚡|A lot more events are simply direct in UWP. Some cases of event bubbling such as ButtonBase.Click to parent are not supported in UWP. Event Tunneling, a concept fully supported in WPF, isn't support at all in UWP.
|Window|✔|✔|✖|For some good reasons UWP has no concept of a window. This is fine for mobile devices but can be a problem for purely desktop applications. Without a window, there is no way to control an app's size or position. There are currently proposals to add this in the transition to WinUI 3.0.

## Controls

This section describes the differences in controls in vanilla WPF and UWP (with the WinUI 2.x library). It excludes some primitives and shapes (Ellipse, Rect, etc.)

|Avalonia|WPF|UWP|Notes|
|:---:|:---:|:---:|----------|
|&#10006;|&#10006;|AppBarButton||
|&#10006;|&#10006;|AppBarSeparator||
|&#10006;|&#10006;|AppBarToggleButton||
|AutoCompleteBox|&#10006;|AutoSuggestBox|AutoCompleteBox doesn't support query events|
|Border|Border|Border||
|BulletDecorator|&#10006;||
|Button|Button|Button||
CalendarDatePicker|DatePicker|CalendarDatePicker|UWP DatePicker is different from WPF DatePicker. The WPF DatePicker is closer to the UWP CalendarDatePicker in functionality.|
|Calendar|Calendar|CalendarView||
|Canvas|Canvas|Canvas||
|&#10006;|&#10006;|CaptureElement||
|CheckBox|CheckBox|CheckBox||
|&#10006;|&#10006;|ColorPicker||
|ComboBox|ComboBox|ComboBox||
|&#10006;|ToolBar|CommandBar||
|&#10006;|&#10006;|CommandBarFlyout|First introduced in the Windows UI Library|
|ContentControl|&#10006;|ContentControl||
|ContentPresenter|&#10006;|ContentPresenter||
|DataGrid|DataGrid|&#10006;|Available for UWP in the Windows Community Toolkit (albeit with many bugs)|
|DatePicker|&#10006;|DatePicker|A picker to select a date without a calendar view does not exist in WPF.|
|DatePickerFlyout|&#10006;|DatePickerFlyout||
|DockPanel|DockPanel|&#10006;|Available for UWP in the Windows Community Toolkit|
|&#10006;|DocumentViewer|&#10006;||
|&#10006;|&#10006;|DropDownButton|First introduced in the Windows UI Library|
|Expander|Expander|&#10006;|Available for UWP in the Windows Community Toolkit|
|Carousel|&#10006;|FlipView||
|&#10006;|FlowDocumentPageViewer|&#10006;||
|&#10006;|FlowDocumentReader|&#10006;||
|&#10006;|FlowDocumentScrollViewer|&#10006;||
|&#10006;|&#10006;|Flyout||
|&#10006;|Frame|Frame||
|Grid|Grid|Grid||
|GridSplitter|GridSplitter|&#10006;|Available for UWP in the Windows Community Toolkit|
|&#10006;|&#10006;|GridView||
|&#10006;|GroupBox|&#10006;||
|&#10006;|&#10006;|Hub||
|&#10006;|&#10006;|HubSection||
|&#10006;|&#10006;|HyperlinkButton||
|Image|Image|Image||
|&#10006;|InkCanvas||
|&#10006;|InkToolbar||
|ItemsControl|&#10006;|ItemsControl||
|ItemsPresenter|&#10006;|ItemsPresenter||
|ItemsRepeater|&#10006;|ItemsRepeater|First introduced in the Windows UI Library|
|Label|Label|&#10006;|For compatiblity with Windows Forms|
|ListBox|ListBox|ListBox||
|&#10006;|ListView|ListView||
|&#10006;|&#10006;|MapControl||
|&#10006;|&#10006;|MediaElement||
|&#10006;|&#10006;|MediaTransportControls||
|Menu|Menu|MenuBar|First introduced in the Windows Community Toolkit then Windows UI Library|
|ContextMenu|ContextMenu|MenuFlyout||
|&#10006;|&#10006;|NavigationView||
|Panel|Panel|&#10006;||
|&#10006;|&#10006;|ParallaxView||
|TextBox (PasswordChar)|PasswordBox|PasswordBox||
|&#10006;|&#10006;|PersonPicture||
|TabControl|TabControl|Pivot||
|TabItem|TabItem|PivotItem||
|Popup|Popup|Popup||
|&#10006;|PrintDialog|&#10006;||
|ProgressBar|ProgressBar|ProgressBar||
|&#10006;|&#10006;|ProgressRing||
|&#10006;|&#10006;|PullToRefresh||
|RadioButton|RadioButton|RadioButton||
|&#10006;|&#10006;|RatingControl||
|Rectangle|Rectangle|Rectangle||
|&#10006;|&#10006;|RefreshContainer|First introduced in the Windows UI Library|
|RelativePanel|&#10006;|RelativePanel||
|RepeatButton|RepeatButton|RepeatButton||
|&#10006;|RichTextBox|RichEditBox||
|&#10006;|&#10006;|RichTextBlock||
|&#10006;|&#10006;|RichTextBlockOverflow||
|ScrollBar|ScrollBar|ScrollBar||
|ScrollContentPresenter|&#10006;|ScrollContentPresenter||
|ScrollViewer|ScrollViewer|ScrollViewer||
|&#10006;|&#10006;|SemanticZoom||
|Separator|Separator|&#10006;||
|Slider|Slider|Slider||
|&#10006;|&#10006;|SplitButton|First introduced in the Windows UI Library|
|SplitView|SplitView||
|StackPanel|StackPanel|StackPanel||
|&#10006;|StatusBar|&#10006;|No longer a UI convention|
|&#10006;|&#10006;|SwipeControl|First introduced in the Windows UI Library|
|&#10006;|&#10006;|TabView|First introduced in the Windows UI Library|
|&#10006;|&#10006;|TeachingTip|First introduced in the Windows UI Library|
|TextBlock|TextBlock|TextBlock||
|TextBox|TextBox|TextBox||
|TimePicker|&#10006;|TimePicker||
|TimePickerFlyout|&#10006;|TimePickerFlyout||
|ToggleButton|ToggleButton|ToggleButton||
|&#10006;|&#10006;|ToggleSplitButton|First introduced in the Windows UI Library|
|ToggleSwitch|&#10006;|ToggleSwitch||
|ToolTip|ToolTip|ToolTip||
|TreeView|TreeView|TreeView||
|&#10006;|&#10006;|TwoPaneView|First introduced in the Windows UI Library|
|&#10006;|&#10006;|VariableSizedWrapGrid||
|Viewbox|Viewbox|Viewbox||
|&#10006;|&#10006;|WebView||
|WrapPanel|WrapPanel|&#10006;|Available for UWP in the Windows Community Toolkit|
|Window|Window|&#10006;|There is no top-level window concept in UWP|

## Quirks

* Several UWP controls have reentrancy issues. For example, changing the selected item while in a ComboBox SelectionChanged event is largely not possible and will result in a crash. This makes validation directly in the event handler nearly impossible.
* UWP controls are generally not as powerful as the WPF counterparts. For example, for several years the ComboBox in UWP was not editable. The UWP DatePicker also does not allow typing in a specific date.
* UWP has no support for data (input) validation. This is a large issue for line-of-business apps migrating from WPF to UWP that heavily use this feature in view models or binding.
* The UWP styling system is different enough from WPF to require extra effort during porting. UWP uses the VistualStateManger instead of concepts like DataTriggers or EventTriggers from WPF. Styling/Templating are one of the main differences.
* The ResourceDictionary XAML markup in UWP supports far fewer features than in WPF.
* UWP seems to follow only the XAML/2006 spec instead of [XAML/2009]((https://docs.microsoft.com/en-us/dotnet/desktop-wpf/xaml-services/xaml-2009-language-features)) supported by WPF
* Several UWP controls are sealed and new controls cannot derive from them
* For advanced rendering, UWP has fewer features built in. This requires falling back to Win2D or composition more often.
* There are several namespaces differences in UWP and WPF. For example, WPF has System.Windows.Media.Colors while UWP moves this to Windows.UI.Colors.
