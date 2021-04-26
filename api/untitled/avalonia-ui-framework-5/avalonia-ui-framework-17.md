# Avalonia.Controls.Primitives.PopupPositioning

## Struct Types <a id="StructTypes"></a>

| Struct | Summary |
| :--- | :--- |
| [PopupPositionerParameters](http://reference.avaloniaui.net/api/Avalonia.Controls.Primitives.PopupPositioning/PopupPositionerParameters) | The IPopupPositioner provides a collection of rules for the placement of a a popup relative to its parent. Rules can be defined to ensure the popup remains within the visible area's borders, and to specify how the popup changes its position, such as sliding along an axis, or flipping around a rectangle. These positioner-created rules are constrained by the requirement that a popup must intersect with or be at least partially adjacent to its parent surface. |

## Enum Types <a id="EnumTypes"></a>

| Enum | Summary |
| :--- | :--- |
| [PopupPositionerConstraintAdjustment](http://reference.avaloniaui.net/api/Avalonia.Controls.Primitives.PopupPositioning/PopupPositionerConstraintAdjustment) | The constraint adjustment value define ways how popup position will be adjusted if the unadjusted position would result in the popup being partly constrained. Whether a popup is considered 'constrained' is left to the positioner to determine. For example, the popup may be partly outside the target platform defined 'work area', thus necessitating the popup's position be adjusted until it is entirely inside the work area. |
| [PopupPositioningEdge](http://reference.avaloniaui.net/api/Avalonia.Controls.Primitives.PopupPositioning/PopupPositioningEdge) |  |

## Interface Types <a id="InterfaceTypes"></a>

## Class Types <a id="ClassTypes"></a>

