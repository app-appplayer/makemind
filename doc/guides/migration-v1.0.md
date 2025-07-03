# MCP UI DSL v1.0 Migration Guide

This guide helps you migrate your existing MCP UI applications to comply with the v1.0 specification.

## Overview of Breaking Changes

The MCP UI DSL v1.0 specification introduces several breaking changes to improve consistency and clarity across the platform. These changes affect widget types, property names, event handlers, and action types.

## Widget Type Changes

### Layout Widgets

#### Column/Row → Linear
The separate `column` and `row` widget types have been unified into a single `linear` widget type with a `direction` property.

**Before:**
```json
{
  "type": "column",
  "mainAxisAlignment": "center",
  "crossAxisAlignment": "start",
  "children": [...]
}
```

**After:**
```json
{
  "type": "linear",
  "direction": "vertical",
  "alignment": "start",
  "distribution": "center",
  "children": [...]
}
```

**Before:**
```json
{
  "type": "row",
  "mainAxisAlignment": "space-between",
  "crossAxisAlignment": "center",
  "children": [...]
}
```

**After:**
```json
{
  "type": "linear",
  "direction": "horizontal",
  "alignment": "center",
  "distribution": "space-between",
  "children": [...]
}
```

### Display Widgets

#### Label → Text
The `label` widget type has been renamed to `text` for consistency.

**Before:**
```json
{
  "type": "label",
  "value": "Hello World"
}
```

**After:**
```json
{
  "type": "text",
  "content": "Hello World"
}
```

### Input Widgets

#### TextField → TextInput
The `textField` widget type has been renamed to `textInput`.

**Before:**
```json
{
  "type": "textField",
  "value": "{{username}}",
  "placeholder": "Enter username"
}
```

**After:**
```json
{
  "type": "textInput",
  "value": "{{username}}",
  "placeholder": "Enter username"
}
```

## Property Name Changes

### Layout Properties

The layout properties for the `linear` widget have been standardized:

- `mainAxisAlignment` → `distribution`
- `crossAxisAlignment` → `alignment`

### Text Properties

- `value` → `content` (for text widgets)

### Button Properties

- `style` → `variant` (for button styling)

## Event Handler Changes

### Click Events

All click-related event handlers have been standardized to `click`:

- `onTap` → `click`
- `onClick` → `click`
- `onPressed` → `click`

**Before:**
```json
{
  "type": "button",
  "label": "Click Me",
  "onTap": {
    "type": "tool",
    "tool": "handleClick"
  }
}
```

**After:**
```json
{
  "type": "button",
  "label": "Click Me",
  "click": {
    "type": "tool",
    "tool": "handleClick"
  }
}
```

### Change Events

All change-related event handlers have been standardized to `change`:

- `onChange` → `change`
- `onChanged` → `change`
- `onValueChanged` → `change`

### Other Events

- `double-click` (new in v1.0)
- `long-press` (new in v1.0)

## Action Type Changes

### State Actions

The `stateAction` type has been simplified to `state`:

**Before:**
```json
{
  "type": "stateAction",
  "action": "set",
  "binding": "counter",
  "value": "{{counter + 1}}"
}
```

**After:**
```json
{
  "type": "state",
  "action": "set",
  "binding": "counter",
  "value": "{{counter + 1}}"
}
```

### Navigation Actions

The `navigate` action type has been renamed to `navigation`:

**Before:**
```json
{
  "type": "navigate",
  "route": "/profile"
}
```

**After:**
```json
{
  "type": "navigation",
  "action": "push",
  "route": "/profile"
}
```

## New Features in v1.0

### New Widgets

- `conditional` - Conditional rendering
- `numberField` - Numeric input field
- `colorPicker` - Color selection widget
- `radioGroup` - Radio button group
- `checkboxGroup` - Checkbox group
- `dateField` - Date input field
- `timeField` - Time input field
- `chart` - Data visualization
- `table` - Tabular data display
- `draggable` - Draggable widget
- `dragTarget` - Drop target for draggables

### New Action Types

- `batch` - Execute multiple actions in sequence
- `conditional` - Conditional action execution
- `dialog` - Show modal dialogs

### Dialog Widgets

- `AlertDialog` - Simple alert dialog
- `SimpleDialog` - Dialog with options
- `BottomSheet` - Modal bottom sheet

## Migration Checklist

1. **Update Widget Types**
   - [ ] Replace `column` with `linear` + `direction: "vertical"`
   - [ ] Replace `row` with `linear` + `direction: "horizontal"`
   - [ ] Replace `label` with `text`
   - [ ] Replace `textField` with `textInput`

2. **Update Property Names**
   - [ ] Replace `mainAxisAlignment` with `distribution`
   - [ ] Replace `crossAxisAlignment` with `alignment`
   - [ ] Replace `value` with `content` for text widgets
   - [ ] Replace `style` with `variant` for buttons

3. **Update Event Handlers**
   - [ ] Replace `onTap`, `onClick`, `onPressed` with `click`
   - [ ] Replace `onChange`, `onChanged` with `change`

4. **Update Action Types**
   - [ ] Replace `stateAction` with `state`
   - [ ] Replace `navigate` with `navigation`

5. **Test Your Application**
   - [ ] Verify all widgets render correctly
   - [ ] Test all user interactions
   - [ ] Check state management functionality
   - [ ] Ensure navigation works as expected

## Example Migration

Here's a complete example of migrating a simple counter component:

### Before (Pre-v1.0):
```json
{
  "type": "page",
  "content": {
    "type": "column",
    "mainAxisAlignment": "center",
    "children": [
      {
        "type": "label",
        "value": "Count: {{count}}"
      },
      {
        "type": "row",
        "mainAxisAlignment": "center",
        "children": [
          {
            "type": "button",
            "label": "Increment",
            "style": "elevated",
            "onTap": {
              "type": "stateAction",
              "action": "set",
              "binding": "count",
              "value": "{{count + 1}}"
            }
          }
        ]
      }
    ]
  }
}
```

### After (v1.0):
```json
{
  "type": "page",
  "content": {
    "type": "linear",
    "direction": "vertical",
    "distribution": "center",
    "children": [
      {
        "type": "text",
        "content": "Count: {{count}}"
      },
      {
        "type": "linear",
        "direction": "horizontal",
        "distribution": "center",
        "children": [
          {
            "type": "button",
            "label": "Increment",
            "variant": "elevated",
            "click": {
              "type": "state",
              "action": "set",
              "binding": "count",
              "value": "{{count + 1}}"
            }
          }
        ]
      }
    ]
  }
}
```

## Troubleshooting

### Common Issues

1. **Widget not rendering**: Check if you've updated the widget type correctly
2. **Layout issues**: Ensure you've updated `mainAxisAlignment` and `crossAxisAlignment` to the new property names
3. **Events not firing**: Verify event handler names have been updated
4. **State not updating**: Check that action types have been migrated

### Getting Help

If you encounter issues during migration:
1. Refer to the [MCP UI DSL v1.0 Specification](../specification/MCP_UI_DSL_v1.0_Specification.md)
2. Check the [Widget Reference](../api/widget-reference.md) for detailed widget documentation
3. Review the [Examples](../examples/) for v1.0-compliant code

## Summary

The v1.0 specification brings significant improvements to consistency and clarity. While the migration requires some effort, the result is a more maintainable and predictable UI system. Take advantage of the new features like conditional rendering, advanced input widgets, and dialog support to enhance your applications.