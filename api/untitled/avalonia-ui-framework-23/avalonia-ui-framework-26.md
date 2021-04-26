# Avalonia.Data.Core.Plugins

## Avalonia.Data.Core.Plugins Namespace

## Class Types <a id="ClassTypes"></a>

| Class | Summary |
| :--- | :--- |
| [AvaloniaPropertyAccessorPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/AvaloniaPropertyAccessorPlugin) | Reads a property from a [`AvaloniaObject`](http://reference.avaloniaui.net/api/Avalonia/AvaloniaObject). |
| [DataAnnotationsValidationPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/DataAnnotationsValidationPlugin) | Validates properties on that have `ValidationAttribute`s. |
| [DataValidationBase](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/DataValidationBase) | Base class for data validators. |
| [ExceptionValidationPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/ExceptionValidationPlugin) | Validates properties that report errors by throwing exceptions. |
| [IndeiValidationPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IndeiValidationPlugin) | Validates properties on objects that implement `INotifyDataErrorInfo`. |
| [InpcPropertyAccessorPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/InpcPropertyAccessorPlugin) | Reads a property from a standard C\# object that optionally supports the `INotifyPropertyChanged` interface. |
| [ObservableStreamPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/ObservableStreamPlugin) | Handles binding to [`IObservable`](http://reference.avaloniaui.net/)s for the '^' stream binding operator. |
| [PropertyAccessorBase](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/PropertyAccessorBase) | Defines a default base implementation for a [`IPropertyAccessor`](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IPropertyAccessor). |
| [PropertyError](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/PropertyError) | An [`IPropertyAccessor`](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IPropertyAccessor) that represents an error. |
| [TaskStreamPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/TaskStreamPlugin) | Handles binding to [`Task`](http://reference.avaloniaui.net/)s for the '^' stream binding operator. |

## Interface Types <a id="InterfaceTypes"></a>

| Interface | Summary |
| :--- | :--- |
| [IDataValidationPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IDataValidationPlugin) | Defines how data validation is observed by an [`ExpressionObserver`](http://reference.avaloniaui.net/api/Avalonia.Data.Core/ExpressionObserver). |
| [IPropertyAccessor](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IPropertyAccessor) | Defines an accessor to a property on an object returned by a [`IPropertyAccessorPlugin`](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IPropertyAccessorPlugin) |
| [IPropertyAccessorPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IPropertyAccessorPlugin) | Defines how a member is read, written and observed by an [`ExpressionObserver`](http://reference.avaloniaui.net/api/Avalonia.Data.Core/ExpressionObserver). |
| [IStreamPlugin](http://reference.avaloniaui.net/api/Avalonia.Data.Core.Plugins/IStreamPlugin) | Defines a plugin that handles the '^' stream binding operator. |

