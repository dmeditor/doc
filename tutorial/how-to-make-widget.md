How to make a widget
======

A widget can be simple like a button, or complex like intractive form. 

Conceptally a widget is a React component with customize settings. To simplify settings(eg. color, sliding, padding) we provide some setting component(eg. `color`) which can be configured and the setting will work automatially, so the developer can focus on the widget rendering.

### Sample widget
Click [this](./) to see our widget sample.

### Widget development overview

A typical widget(eg. `heading`) needs below information:

1. A definition object, which defines widget's name, type, settings, etc
2. An entity(optional), which defines data model of this widget. If not defined, the default data model will be used.
3. A render component which is a react component rendering the widget's data

You will need to register 1. and 3. using `registerWidget` function.

In addition, you may need to create your customized setting component if our built-in setting components don't fit your need.


### 1. Definition file
A definition define 'meta data' of a widget, and other information like settings, methods (eg, return data after user create a block from this widget). Below is the meta data information:
```javascript
{
  // Name of the widget
  name: 'Heading',

  // Type of the widget, unique identifier for this widget.
  // Only allow small case, -, numbers, starting from letter
  type: 'heading', 
  category: 'widget',
  icon: 'TextFormatOutlined',
}
```
See our [definition reference](../reference/widget.md) for full properties and explaination.


### 2. Entity

### 3. Render


### 4. Setting


### Register your widget

