How to make a widget
======

A widget can be simple like a button, or complex like intractive form. 

Basically a widget can be treated as a React component with customize settings. We provide some setting component(eg. color) so the developer only need some configuration and the setting will be there.

A typical widget needs below information

1. A definition file, which defines widget's name, type, icons, etc
2. An entity, which define data model of this widget
3. A main render which is a react component rendering the widget's data
4. Settings. Can be setting configuration and/or customized setting component.

At last you need to register your widget into dmeditor.

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


### 2. Entity

### 3. Render


### 4. Setting
--------

Register widget folder
----
