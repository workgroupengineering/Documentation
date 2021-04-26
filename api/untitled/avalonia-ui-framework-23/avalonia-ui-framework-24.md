# Avalonia.Data.Converters

## Avalonia.Data.Converters Namespace

## Class Types <a id="ClassTypes"></a>

| Class | Summary |
| :--- | :--- |
| [BoolConverters](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/BoolConverters) | Provides a set of useful [`IValueConverter`](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IValueConverter)s for working with string values. |
| [DefaultValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/DefaultValueConverter) | Provides a default set of value conversions for bindings that do not specify a value converter. |
| [FuncMultiValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/FuncMultiValueConverter_2)&lt;[TIn](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/FuncMultiValueConverter_2#typeparam-TIn),[TOut](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/FuncMultiValueConverter_2#typeparam-TOut)&gt; | A general purpose [`IValueConverter`](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IValueConverter) that uses a [`Func`](http://reference.avaloniaui.net/) to provide the converter logic. |
| [FuncValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/FuncValueConverter_2)&lt;[TIn](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/FuncValueConverter_2#typeparam-TIn),[TOut](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/FuncValueConverter_2#typeparam-TOut)&gt; | A general purpose [`IValueConverter`](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IValueConverter) that uses a [`Func`](http://reference.avaloniaui.net/) to provide the converter logic. |
| [ObjectConverters](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/ObjectConverters) | Provides a set of useful [`IValueConverter`](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IValueConverter)s for working with objects. |
| [StringConverters](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/StringConverters) | Provides a set of useful [`IValueConverter`](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IValueConverter)s for working with string values. |
| [StringFormatMultiValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/StringFormatMultiValueConverter) | A multi-value converter which calls `System.String.Format(System.String,System.Object)` |
| [StringFormatValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/StringFormatValueConverter) | A value converter which calls `System.String.Format(System.String,System.Object)` |

## Interface Types <a id="InterfaceTypes"></a>

| Interface | Summary |
| :--- | :--- |
| [IMultiValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IMultiValueConverter) | Converts multi-binding inputs to a final value. |
| [IValueConverter](http://reference.avaloniaui.net/api/Avalonia.Data.Converters/IValueConverter) | Converts a binding value. |

