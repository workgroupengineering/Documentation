# Controls & Layouts

### Controls <a id="controls"></a>

Avalonia provides many core controls. Here are some of the most common:

* Buttons: [`Button`](http://avaloniaui.net/docs/controls/button), [`RepeatButton`](http://avaloniaui.net/docs/controls/repeatbutton)
* Data Display: [`ItemsControl`](http://avaloniaui.net/docs/controls/itemscontrol), [`ItemsRepeater`](http://avaloniaui.net/docs/controls/itemsrepeater), [`ListBox`](http://avaloniaui.net/docs/controls/listbox), [`TreeView`](http://avaloniaui.net/docs/controls/treeview)
* Input: [`CheckBox`](http://avaloniaui.net/docs/controls/checkbox), [`ComboBox`](http://avaloniaui.net/docs/controls/combobox), [`RadioButton`](http://avaloniaui.net/docs/controls/radiobutton), [`Slider`](http://avaloniaui.net/docs/controls/slider), [`TextBox`](http://avaloniaui.net/docs/controls/textbox)
* Layout: [`Border`](http://avaloniaui.net/docs/controls/border), [`Canvas`](http://avaloniaui.net/docs/controls/canvas), [`DockPanel`](http://avaloniaui.net/docs/controls/dockpanel), [`Expander`](http://avaloniaui.net/docs/controls/expander), [`Grid`](http://avaloniaui.net/docs/controls/grid), [`GridSplitter`](http://avaloniaui.net/docs/controls/gridsplitter), [`Panel`](http://avaloniaui.net/docs/controls/panel), [`Separator`](http://avaloniaui.net/docs/controls/separator), [`ScrollBar`](http://avaloniaui.net/docs/controls/scrollbar), [`ScrollViewer`](http://avaloniaui.net/docs/controls/scrollviewer), [`StackPanel`](http://avaloniaui.net/docs/controls/stackpanel), [`Viewbox`](http://avaloniaui.net/docs/controls/viewbox), [`WrapPanel`](http://avaloniaui.net/docs/controls/wrappanel)
* Menus: [`ContentMenu`](http://avaloniaui.net/docs/controls/contextmenu), [`Menu`](http://avaloniaui.net/docs/controls/menu), [`NativeMenu`](http://avaloniaui.net/docs/controls/nativemenu)
* Navigation: [`TabControl`](http://avaloniaui.net/docs/controls/tabcontrol), [`TabStrip`](http://avaloniaui.net/docs/controls/tabstrip)
* User Information: [`ProgressBar`](http://avaloniaui.net/docs/controls/progressbar), [`TextBlock`](http://avaloniaui.net/docs/controls/textblock), [`ToolTip`](http://avaloniaui.net/docs/controls/tooltip)

### Input and Commands <a id="input-and-commands"></a>

Controls most often detect and respond to user input. The Avalonia [input system](http://avaloniaui.net/docs/input) uses both [direct and routed events](http://avaloniaui.net/docs/input/events) to support text input, focus management, and mouse positioning.

Applications often have complex input requirements. Avalonia provides a [command system](http://avaloniaui.net/docs/binding/binding-to-commands) that separates user-input actions from the code that responds to those actions.

### Layout <a id="layout"></a>

When you create a user interface, you arrange your controls by location and size to form a layout. A key requirement of any layout is to adapt to changes in window size and display settings. Rather than forcing you to write the code to adapt a layout in these circumstances, Avalonia provides a first-class, extensible layout system for you.

The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions. In addition, the layout system manages the negotiation between controls to determine the layout. The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.

The layout system is exposed to child controls through base Avalonia classes. For common layouts such as grids, stacking, and docking, Avalonia includes several layout controls:

* [`Panel`](http://avaloniaui.net/docs/controls/panel): Child controls are stacked on top of each other to fill the panel
* [`Canvas`](http://avaloniaui.net/docs/controls/canvas): Child controls provide their own layout
* [`DockPanel`](http://avaloniaui.net/docs/controls/dockpanel): Child controls are aligned to the edges of the panel
* [`Grid`](http://avaloniaui.net/docs/controls/grid): Child controls are positioned by rows and columns
* [`StackPanel`](http://avaloniaui.net/docs/controls/stackpanel): Child controls are stacked either vertically or horizontally
* [`WrapPanel`](http://avaloniaui.net/docs/controls/wrappanel): Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows

You can also create your own layouts by [deriving from the `Panel` class](http://avaloniaui.net/docs/layout/creating-a-panel).

