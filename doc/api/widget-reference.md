# Widget Reference

This document provides a comprehensive reference for all widgets available in the MCP UI DSL.

## Widget Categories

- [Layout Widgets](#layout-widgets)
- [Display Widgets](#display-widgets)
- [Input Widgets](#input-widgets)
- [List Widgets](#list-widgets)
- [Navigation Widgets](#navigation-widgets)
- [Utility Widgets](#utility-widgets)

## Common Properties

All widgets support these base properties:

| Property | Type | Description | Default |
|----------|------|-------------|---------|
| `type` | string | **Required.** The widget type | - |
| `visible` | boolean/string | Widget visibility. Can be a binding | true |
| `key` | string | Unique identifier for the widget | null |
| `testKey` | string | Key for widget testing | null |

## Layout Widgets

### Linear

Arranges children in a single direction (vertical or horizontal).

```json
{
  "type": "linear",
  "direction": "vertical",
  "alignment": "center",
  "distribution": "start",
  "spacing": 8,
  "children": []
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `direction` | string | **Required.** Layout direction | `vertical`, `horizontal` |
| `alignment` | string | Cross-axis alignment | `start`, `center`, `end`, `stretch` |
| `distribution` | string | Main-axis distribution | `start`, `center`, `end`, `space-between`, `space-around`, `space-evenly` |
| `spacing` | number | Spacing between children | 0 |
| `children` | array | Child widgets | [] |

For horizontal arrangement:

```json
{
  "type": "linear",
  "direction": "horizontal",
  "alignment": "center",
  "distribution": "space-between",
  "children": []
}
```

Properties are identical to vertical linear layout but apply horizontally.

### Box

A box with optional decoration, padding, and constraints.

```json
{
  "type": "box",
  "width": 200,
  "height": 100,
  "padding": 16,
  "margin": 8,
  "alignment": "center",
  "decoration": {
    "color": "#FFFFFF",
    "borderRadius": 8,
    "border": {
      "color": "#000000",
      "width": 1
    },
    "boxShadow": [
      {
        "color": "#00000033",
        "blurRadius": 4,
        "offset": {"dx": 0, "dy": 2}
      }
    ]
  },
  "child": {}
}
```

| Property | Type | Description |
|----------|------|-------------|
| `width` | number | Container width |
| `height` | number | Container height |
| `padding` | number/object | Inner spacing |
| `margin` | number/object | Outer spacing |
| `alignment` | string | Child alignment |
| `decoration` | object | Visual decoration |
| `child` | object | Single child widget |

### Stack

Overlays children on top of each other.

```json
{
  "type": "stack",
  "alignment": "topLeft",
  "fit": "loose",
  "children": []
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `alignment` | string | Default alignment for children | `topLeft`, `topCenter`, `topRight`, `centerLeft`, `center`, `centerRight`, `bottomLeft`, `bottomCenter`, `bottomRight` |
| `fit` | string | How to size the stack | `loose`, `expand`, `passthrough` |

### Center

Centers its child widget.

```json
{
  "type": "center",
  "child": {}
}
```

### Expanded

Expands to fill available space in a Row/Column.

```json
{
  "type": "expanded",
  "flex": 1,
  "child": {}
}
```

| Property | Type | Description | Default |
|----------|------|-------------|---------|
| `flex` | number | Flex factor | 1 |

### SizedBox

A box with specific dimensions.

```json
{
  "type": "sizedBox",
  "width": 100,
  "height": 50,
  "child": {}
}
```

### Padding

Adds padding around a child.

```json
{
  "type": "padding",
  "padding": 16,
  "child": {}
}
```

| Property | Type | Description |
|----------|------|-------------|
| `padding` | number/object | Padding amount |

Padding object format:
```json
{
  "left": 8,
  "right": 8,
  "top": 16,
  "bottom": 16
}
```

### Conditional

Renders different widgets based on a condition.

```json
{
  "type": "conditional",
  "condition": "{{user.isAuthenticated}}",
  "then": {
    "type": "text",
    "content": "Welcome, {{user.name}}!"
  },
  "else": {
    "type": "button",
    "label": "Sign In",
    "click": {
      "type": "navigation",
      "action": "push",
      "route": "/login"
    }
  }
}
```

| Property | Type | Description |
|----------|------|-------------|
| `condition` | string/boolean | **Required.** Condition to evaluate |
| `then` | object | **Required.** Widget to render when condition is true |
| `else` | object | Optional widget to render when condition is false |

## Display Widgets

### Text

Displays text with optional styling.

```json
{
  "type": "text",
  "content": "Hello {{name}}",
  "style": {
    "fontSize": 16,
    "fontWeight": "bold",
    "color": "#333333",
    "fontFamily": "Roboto",
    "decoration": "underline",
    "letterSpacing": 1.2,
    "wordSpacing": 2.0,
    "height": 1.5
  },
  "textAlign": "center",
  "maxLines": 2,
  "overflow": "ellipsis"
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `content` | string | **Required.** Text content (supports bindings) | - |
| `style` | object | Text styling | See style properties |
| `textAlign` | string | Text alignment | `left`, `right`, `center`, `justify` |
| `maxLines` | number | Maximum lines | null (unlimited) |
| `overflow` | string | Overflow behavior | `clip`, `fade`, `ellipsis`, `visible` |

### RichText

Displays formatted text with multiple styles.

```json
{
  "type": "richText",
  "spans": [
    {
      "text": "Hello ",
      "style": {"fontWeight": "normal"}
    },
    {
      "text": "{{name}}",
      "style": {"fontWeight": "bold", "color": "#FF0000"}
    }
  ]
}
```

### Image

Displays an image from various sources.

```json
{
  "type": "image",
  "source": "https://example.com/image.png",
  "width": 200,
  "height": 200,
  "fit": "cover",
  "placeholder": "assets/placeholder.png",
  "errorWidget": {
    "type": "icon",
    "icon": "error",
    "color": "#FF0000"
  }
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `source` | string | **Required.** Image URL or asset path | - |
| `width` | number | Image width | null |
| `height` | number | Image height | null |
| `fit` | string | How to fit the image | `fill`, `contain`, `cover`, `fitWidth`, `fitHeight`, `none`, `scaleDown` |
| `placeholder` | string | Loading placeholder | null |
| `errorWidget` | object | Widget shown on error | null |

### Icon

Displays an icon.

```json
{
  "type": "icon",
  "icon": "home",
  "size": 24,
  "color": "#000000"
}
```

| Property | Type | Description | Default |
|----------|------|-------------|---------|
| `icon` | string | **Required.** Icon name | - |
| `size` | number | Icon size | 24 |
| `color` | string | Icon color | Theme default |

### CircularProgressIndicator

Shows a circular loading indicator.

```json
{
  "type": "circularProgressIndicator",
  "value": 0.7,
  "color": "#2196F3",
  "backgroundColor": "#E0E0E0",
  "strokeWidth": 4
}
```

| Property | Type | Description | Default |
|----------|------|-------------|---------|
| `value` | number | Progress (0.0-1.0), null for indeterminate | null |
| `color` | string | Progress color | Theme primary |
| `backgroundColor` | string | Background track color | Transparent |
| `strokeWidth` | number | Line thickness | 4.0 |

### LinearProgressIndicator

Shows a linear loading bar.

```json
{
  "type": "linearProgressIndicator",
  "value": 0.5,
  "color": "#4CAF50",
  "backgroundColor": "#E0E0E0",
  "minHeight": 4
}
```

## Input Widgets

### Button

A clickable button with various styles.

```json
{
  "type": "button",
  "label": "Click Me",
  "variant": "elevated",
  "icon": "add",
  "enabled": true,
  "click": {
    "type": "tool",
    "tool": "handleClick"
  }
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `label` | string | **Required.** Button text | - |
| `variant` | string | Button variant | `elevated`, `filled`, `outlined`, `text`, `icon` |
| `icon` | string | Optional icon | Icon name |
| `enabled` | boolean/string | Whether enabled (can be binding) | true |
| `click` | object | Click action | Action object |
| `double-click` | object | Optional double-click action | Action object |
| `long-press` | object | Optional long-press action | Action object |

### TextInput

Single or multi-line text input field.

```json
{
  "type": "textInput",
  "label": "Username",
  "value": "{{username}}",
  "placeholder": "Enter username",
  "enabled": true,
  "obscureText": false,
  "maxLength": 50,
  "keyboardType": "text",
  "validation": {
    "required": true,
    "minLength": 3,
    "pattern": "^[a-zA-Z0-9_]+$",
    "errorMessage": "Invalid username"
  },
  "change": {
    "type": "state",
    "action": "set",
    "binding": "username",
    "value": "{{event.value}}"
  }
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `label` | string | Field label | - |
| `value` | string | Current value (supports binding) | - |
| `placeholder` | string | Placeholder text | - |
| `enabled` | boolean | Whether enabled | true |
| `obscureText` | boolean | Hide text (passwords) | false |
| `maxLength` | number | Maximum characters | null |
| `maxLines` | number | Maximum lines (1 for single-line) | 1 |
| `keyboardType` | string | Keyboard type | `text`, `number`, `email`, `phone`, `url` |
| `validation` | object | Validation rules | - |
| `change` | object | Change action | - |

### Checkbox

A toggleable checkbox.

```json
{
  "type": "checkbox",
  "value": "{{agreedToTerms}}",
  "label": "I agree to terms",
  "tristate": false,
  "enabled": true,
  "change": {
    "type": "state",
    "action": "toggle",
    "binding": "agreedToTerms"
  }
}
```

| Property | Type | Description | Default |
|----------|------|-------------|---------|
| `value` | boolean/string | Current value (supports binding) | false |
| `label` | string | Checkbox label | - |
| `tristate` | boolean | Allow null state | false |
| `enabled` | boolean | Whether enabled | true |
| `change` | object | Change action | - |

### Switch

A toggle switch.

```json
{
  "type": "switch",
  "label": "Enable notifications",
  "bindTo": "notificationsEnabled",
  "enabled": true,
  "onChange": {
    "type": "tool",
    "tool": "updateSettings",
    "params": {"notifications": "{{notificationsEnabled}}"}
  }
}
```

Properties are similar to Checkbox.

### Slider

A value slider.

```json
{
  "type": "slider",
  "bindTo": "volume",
  "min": 0,
  "max": 100,
  "divisions": 10,
  "label": "{{volume}}",
  "enabled": true,
  "onChange": {
    "type": "stateAction",
    "action": "set",
    "binding": "volumePercent",
    "value": "{{volume / 100}}"
  }
}
```

| Property | Type | Description | Default |
|----------|------|-------------|---------|
| `bindTo` | string | **Required.** State binding | - |
| `min` | number | Minimum value | 0.0 |
| `max` | number | Maximum value | 1.0 |
| `divisions` | number | Discrete divisions | null (continuous) |
| `label` | string | Current value label | null |

### DropdownButton

A dropdown selection.

```json
{
  "type": "dropdownButton",
  "bindTo": "selectedCountry",
  "items": [
    {"value": "us", "label": "United States"},
    {"value": "uk", "label": "United Kingdom"},
    {"value": "ca", "label": "Canada"}
  ],
  "placeholder": "Select a country",
  "enabled": true,
  "onChange": {
    "type": "tool",
    "tool": "loadStates",
    "params": {"country": "{{selectedCountry}}"}
  }
}
```

### NumberField

Specialized input field for numeric input.

```json
{
  "type": "numberField",
  "label": "Quantity",
  "value": "{{form.quantity}}",
  "min": 1,
  "max": 100,
  "step": 1,
  "decimalPlaces": 0,
  "format": "decimal",
  "prefix": "$",
  "thousandSeparator": ",",
  "change": {
    "type": "state",
    "action": "set",
    "binding": "form.quantity",
    "value": "{{event.value}}"
  }
}
```

### ColorPicker

Widget for color selection.

```json
{
  "type": "colorPicker",
  "value": "{{theme.primaryColor}}",
  "showAlpha": true,
  "showLabel": true,
  "pickerType": "wheel",
  "enableHistory": true,
  "change": {
    "type": "state",
    "action": "set",
    "binding": "theme.primaryColor",
    "value": "{{event.value}}"
  }
}
```

### RadioGroup

Radio button group for single selection.

```json
{
  "type": "radioGroup",
  "value": "{{settings.language}}",
  "options": [
    {"value": "en", "label": "English"},
    {"value": "es", "label": "Español"},
    {"value": "fr", "label": "Français"}
  ],
  "orientation": "vertical",
  "change": {
    "type": "state",
    "action": "set",
    "binding": "settings.language",
    "value": "{{event.value}}"
  }
}
```

### CheckboxGroup

Checkbox group for multiple selection.

```json
{
  "type": "checkboxGroup",
  "value": "{{form.interests}}",
  "options": [
    {"value": "sports", "label": "Sports"},
    {"value": "music", "label": "Music"},
    {"value": "reading", "label": "Reading"}
  ],
  "orientation": "vertical",
  "change": {
    "type": "state",
    "action": "set",
    "binding": "form.interests",
    "value": "{{event.value}}"
  }
}
```

### DateField

Field for date input.

```json
{
  "type": "dateField",
  "label": "Birth Date",
  "value": "{{user.birthdate}}",
  "format": "yyyy-MM-dd",
  "firstDate": "1900-01-01",
  "lastDate": "{{today}}",
  "mode": "calendar",
  "change": {
    "type": "state",
    "action": "set",
    "binding": "user.birthdate",
    "value": "{{event.value}}"
  }
}
```

### TimeField

Field for time input.

```json
{
  "type": "timeField",
  "label": "Notification Time",
  "value": "{{settings.notificationTime}}",
  "format": "HH:mm",
  "use24HourFormat": true,
  "mode": "spinner",
  "change": {
    "type": "state",
    "action": "set",
    "binding": "settings.notificationTime",
    "value": "{{event.value}}"
  }
}
```

## List Widgets

### List

A scrollable list of widgets.

```json
{
  "type": "list",
  "items": "{{items}}",
  "spacing": 8,
  "orientation": "vertical",
  "emptyMessage": "No items to display",
  "itemTemplate": {
    "type": "card",
    "margin": {"vertical": 4},
    "child": {
      "type": "listTile",
      "title": {
        "type": "text",
        "content": "{{item.name}}"
      },
      "subtitle": {
        "type": "text",
        "content": "{{item.description}}"
      },
      "click": {
        "type": "navigation",
        "action": "push",
        "route": "/detail",
        "params": {"id": "{{item.id}}"}
      }
    }
  }
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `items` | string/array | **Required.** Data array (supports binding) | - |
| `orientation` | string | List orientation | `vertical`, `horizontal` |
| `spacing` | number | Spacing between items | 0 |
| `emptyMessage` | string | Message when list is empty | null |
| `itemTemplate` | object | **Required.** Widget template for items | - |
| `virtual` | boolean | Enable virtual scrolling for large lists | false |
| `cacheExtent` | number | Cache extent for virtual scrolling | 250 |

### ListTile

A standard list item widget.

```json
{
  "type": "listTile",
  "leading": {
    "type": "icon",
    "icon": "person"
  },
  "title": {
    "type": "text",
    "content": "John Doe"
  },
  "subtitle": {
    "type": "text",
    "content": "john.doe@example.com"
  },
  "trailing": {
    "type": "icon",
    "icon": "chevron_right"
  },
  "click": {
    "type": "tool",
    "tool": "selectUser"
  }
}
```

### Grid

A scrollable grid of widgets.

```json
{
  "type": "grid",
  "crossAxisCount": 2,
  "mainAxisSpacing": 8,
  "crossAxisSpacing": 8,
  "padding": 16,
  "itemCount": "{{products.length}}",
  "itemTemplate": {
    "type": "box",
    "child": {
      "type": "linear",
      "direction": "vertical",
      "children": [
        {
          "type": "image",
          "source": "{{products[index].image}}"
        },
        {
          "type": "text",
          "value": "{{products[index].name}}"
        }
      ]
    }
  }
}
```

## Navigation Widgets

### HeaderBar

Application header/toolbar typically at the top.

```json
{
  "type": "headerBar",
  "title": {
    "type": "text",
    "content": "My App"
  },
  "actions": [
    {
      "type": "button",
      "variant": "icon",
      "icon": "search",
      "click": {
        "type": "navigation",
        "action": "push", 
        "route": "/search"
      }
    }
  ],
  "backgroundColor": "#2196F3"
}
```

### BottomNavigation

Bottom navigation bar for switching between views.

```json
{
  "type": "bottomNavigation",
  "currentIndex": "{{currentTab}}",
  "items": [
    {
      "icon": "home",
      "label": "Home"
    },
    {
      "icon": "search",
      "label": "Search"
    },
    {
      "icon": "person",
      "label": "Profile"
    }
  ],
  "change": {
    "type": "state",
    "action": "set",
    "binding": "currentTab",
    "value": "{{event.index}}"
  }
}
```

### Drawer

Side navigation drawer.

```json
{
  "type": "drawer",
  "child": {
    "type": "linear",
    "direction": "vertical",
    "children": [
      {
        "type": "box",
        "padding": {"all": 16},
        "decoration": {
          "color": "#F5F5F5"
        },
        "child": {
          "type": "text",
          "content": "Menu",
          "style": {"fontSize": 20, "fontWeight": "bold"}
        }
      },
      {
        "type": "listTile",
        "title": {"type": "text", "content": "Home"},
        "leading": {"type": "icon", "icon": "home"},
        "click": {
          "type": "navigation",
          "action": "push",
          "route": "/home"
        }
      }
    ]
  }
}
```

## Utility Widgets

### ScrollView

Scrollable container for content that exceeds viewport.

```json
{
  "type": "scrollView",
  "direction": "vertical",
  "scrollBehavior": "auto",
  "padding": {"all": 16},
  "showScrollbar": "auto",
  "child": {
    "type": "linear",
    "direction": "vertical",
    "children": []
  }
}
```

### Card

A material design card.

```json
{
  "type": "card",
  "elevation": 4,
  "margin": 8,
  "child": {
    "type": "padding",
    "padding": 16,
    "child": {}
  }
}
```

### Divider

A horizontal line separator.

```json
{
  "type": "divider",
  "height": 1,
  "thickness": 1,
  "color": "#E0E0E0",
  "indent": 16,
  "endIndent": 16
}
```

### Spacer

Flexible space that expands.

```json
{
  "type": "spacer",
  "flex": 1
}
```

### Visibility

Conditionally shows/hides a child.

```json
{
  "type": "visibility",
  "visible": "{{showDetails}}",
  "child": {
    "type": "text",
    "value": "Details..."
  },
  "replacement": {
    "type": "text",
    "value": "Hidden"
  }
}
```

## Custom Widgets

You can register custom widgets:

```dart
runtime.widgetRegistry.register('myCustomWidget', MyCustomWidgetFactory());
```

Then use in definitions:

```json
{
  "type": "myCustomWidget",
  "customProperty": "value"
}
```

## Widget Binding Context

When inside list/grid item templates, additional context variables are available:

- `{{item}}` - Current item
- `{{index}}` - Current item index
- `{{isFirst}}` - Boolean, true if first item
- `{{isLast}}` - Boolean, true if last item
- `{{isEven}}` - Boolean, true if index is even
- `{{isOdd}}` - Boolean, true if index is odd

Example:
```json
{
  "type": "list",
  "items": "{{users}}",
  "itemTemplate": {
    "type": "box",
    "padding": {"all": 8},
    "decoration": {
      "color": "{{isEven ? '#F5F5F5' : '#FFFFFF'}}"
    },
    "child": {
      "type": "text",
      "content": "{{item.name}} ({{index + 1}} of {{users.length}}){{isLast ? ' - Last item' : ''}}"
    }
  }
}
```
## Advanced Widgets

### Chart

Data visualization widget for displaying charts.

```json
{
  "type": "chart",
  "chartType": "line",
  "data": {
    "labels": ["Jan", "Feb", "Mar", "Apr"],
    "datasets": [{
      "label": "Sales",
      "data": [100, 200, 150, 300],
      "borderColor": "#2196F3",
      "backgroundColor": "rgba(33, 150, 243, 0.2)"
    }]
  },
  "options": {
    "responsive": true,
    "animation": {"duration": 1000},
    "scales": {
      "y": {
        "beginAtZero": true
      }
    }
  }
}
```

| Property | Type | Description | Values |
|----------|------|-------------|---------|
| `chartType` | string | **Required.** Type of chart | `line`, `bar`, `pie`, `scatter`, `gauge` |
| `data` | object | **Required.** Chart data | Chart data object |
| `options` | object | Chart configuration options | Chart options object |

### Table

Widget for displaying tabular data.

```json
{
  "type": "table",
  "columns": [
    {"key": "id", "label": "ID", "width": 100},
    {"key": "name", "label": "Name", "sortable": true},
    {"key": "status", "label": "Status", "align": "center"}
  ],
  "rows": "{{items}}",
  "selectable": true,
  "rowClick": {
    "type": "navigation",
    "action": "push",
    "route": "/detail/{{row.id}}"
  }
}
```

### Draggable

Widget that can be dragged by the user.

```json
{
  "type": "draggable",
  "data": "{{item.id}}",
  "feedback": {
    "type": "box",
    "padding": {"all": 8},
    "decoration": {
      "color": "#2196F3",
      "borderRadius": 8
    },
    "child": {
      "type": "text",
      "content": "{{item.name}}",
      "style": {"color": "#FFFFFF"}
    }
  },
  "child": {
    "type": "card",
    "child": {
      "type": "listTile",
      "title": "{{item.name}}",
      "subtitle": "{{item.description}}"
    }
  }
}
```

### DragTarget

Drop area that can receive dragged widgets.

```json
{
  "type": "dragTarget",
  "drop": {
    "type": "tool",
    "tool": "moveItem",
    "params": {
      "itemId": "{{event.data}}",
      "targetId": "{{targetId}}"
    }
  },
  "canDrop": "{{canAcceptItem}}",
  "builder": {
    "type": "box",
    "padding": {"all": 16},
    "decoration": {
      "color": "{{hoveredTargetId == targetId ? '#E3F2FD' : '#F5F5F5'}}",
      "borderRadius": 8,
      "border": {
        "color": "{{hoveredTargetId == targetId ? '#2196F3' : '#E0E0E0'}}",
        "width": 2,
        "style": "dashed"
      }
    },
    "child": {
      "type": "center",
      "child": {
        "type": "text",
        "content": "Drop here"
      }
    }
  }
}
```

## Dialog Widgets

### AlertDialog

Shows a modal dialog with title, content, and actions.

```json
{
  "type": "dialog",
  "dialog": {
    "type": "alert",
    "title": "Confirm Action",
    "content": "Are you sure you want to proceed?",
    "dismissible": false,
    "actions": [
      {
        "label": "Cancel",
        "action": "close"
      },
      {
        "label": "Confirm",
        "action": {
          "type": "batch",
          "actions": [
            {
              "type": "tool",
              "tool": "deleteItem",
              "params": {"id": "{{item.id}}"}
            },
            {
              "type": "dialog",
              "action": "close"
            }
          ]
        },
        "primary": true
      }
    ]
  }
}
```

### SimpleDialog

Shows a dialog with a list of options.

```json
{
  "type": "dialog",
  "dialog": {
    "type": "simple",
    "title": "Choose an option",
    "options": [
      {
        "label": "Option 1",
        "value": "option1",
        "icon": "check"
      },
      {
        "label": "Option 2",
        "value": "option2",
        "icon": "close"
      }
    ],
    "onSelect": {
      "type": "state",
      "action": "set",
      "binding": "selectedOption",
      "value": "{{event.value}}"
    }
  }
}
```

### BottomSheet

Shows a modal bottom sheet.

```json
{
  "type": "dialog",
  "dialog": {
    "type": "bottomSheet",
    "dismissible": true,
    "enableDrag": true,
    "child": {
      "type": "linear",
      "direction": "vertical",
      "padding": {"all": 16},
      "children": [
        {
          "type": "text",
          "content": "Share via",
          "style": {"fontSize": 18, "fontWeight": "bold"}
        },
        {
          "type": "list",
          "items": [
            {"icon": "email", "label": "Email"},
            {"icon": "message", "label": "Message"},
            {"icon": "share", "label": "Other apps"}
          ],
          "itemTemplate": {
            "type": "listTile",
            "leading": {"type": "icon", "icon": "{{item.icon}}"},
            "title": {"type": "text", "content": "{{item.label}}"}
          }
        }
      ]
    }
  }
}
```
EOF < /dev/null