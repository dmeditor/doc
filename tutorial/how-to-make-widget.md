How to make a widget
======

A widget can be simple like a button, or complex like intractive form. 

Conceptally a widget is a React component with customize settings. To simplify settings(eg. color, sliding, padding) we provide some setting component(eg. `color`) which can be configured and the setting will work automatially, so the developer can focus on the widget rendering.

### Sample widget
Click [this](./) to see our widget sample.

### Widget development overview

A typical widget needs below information under widget folder(eg. `heading`):

1. A definition file(`definition.ts`), which defines widget's name, type, icons, etc
2. An entity(`entity.ts`), which defines data model of this widget
3. A main render(`render.tsx`) which is a react component rendering the widget's data
4. Settings. Can be setting configuration in `definition.ts` and/or customized setting component.

Then you need to register your widget into dmeditor.

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

