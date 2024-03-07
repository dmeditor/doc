How to make a widget
======

A widget can be simple like a button, or complex like intractive form. 

Conceptally a widget is a React component with customize settings. To simplify settings(eg. color, sliding, padding) we provide some setting component(eg. `color`) which can be configured and the setting will work automatially, so the developer can focus on the widget rendering.

### Sample widget
Click [this](https://github.com/dmeditor/dmeditor/tree/main/samples/dev/SampleWidget) to see our widget sample.

### Widget development overview

A typical widget(eg. `heading`) needs below information:

1. [A definition object](#1-widget-definition), which defines widget's name, type, settings, etc
2. [An entity(optional)](#2-entity), which defines data model of this widget. If not defined, the default data model will be used.
3. [A render component](#3-render-component) which is a react component rendering the widget's data

You will need to [register](#4-register-your-widget) 1. and 3. using `registerWidget` function.

In addition, you may need to create your [customized setting component](#5-customized-setting) if our built-in setting components don't fit your need.


### 1. Widget definition
A definition defines 'meta data' of a widget, and other information like settings, methods (eg, return data after user create a block from this widget). Below is the meta data information:
```javascript
{
  // Name of the widget
  name: 'Heading',

  // Type of the widget, unique identifier for this widget.
  // Only allow small case, -, numbers, starting from letter
  type: 'heading', 
  category: 'widget',
  icon: 'TextFormatOutlined',
  settings: [
        {
          name: 'Background Color',
          settingComponent: 'color',
          category: 'settings',
          property: 'settings.backgroundColor',
        },
        {
          name: 'Width',
          settingComponent: 'setting_input',
          category: 'settings',
          property: 'settings.width',
        },
      ],
}
```
Note:  `setting_input` is a customized setting component, see [Customized setting](#4-customized-setting) for implementation.

See our [definition reference](../reference/widget.md) for full properties and explaination.


### 2. Entity
An entity defines data model. It's recommanded to define a model so the widget data manipulation is easier. The saved json will be same as entity definition.
```javascript
export interface EntitySampleWidget{
    settings: {
      width: number;
      backgroundColor?: string;
    };
  }
```

### 3. Render component

#### Render 
Below is a render component sample to render:

Note `EntitySampleWidget` is the Entity definition.
```javascript
export const SampleWidget = (props: DME.WidgetRenderProps<EntitySampleWidget>) => {
const {
    blockNode: {
      data: { settings },
    },
  } = props;
...
return (
    <div>    
      <div
        style={{ width: width }}
        className={css`
          height: 300px;
          background: ${settings.backgroundColor ?? '#ffe3e3'};
        `}
      >
      </div>
    </div>
}
```

#### Change data
```javascript
const { updateSelectedBlock } = useEditorStore();
  const updateWidth = (e, v) => {
    //update data with entity
    updateSelectedBlock<EntitySampleWidget>((data) => {
      data.settings.width = v as number;
    });
  };
```

### 4. Register your widget
```javascript
registerWidget(
{
   type: 'sample',
   name: 'Sample widget',
   ...
  },
  {render:SampleWidget}
)
```

### 5. Customized setting
Implementation:
```javascript
const SettingInput = (props: DME.SettingComponentProps) => {
  const { property, value } = props;
  const { getSelectedBlock, updateSelectedBlockProps } = useEditorStore();

  //Get block data
  const blockData = getSelectedBlock<EntitySampleWidget>();

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    //update data with dynamic property
    updateSelectedBlockProps(property, e.target.value);
  };

  return (
    <div>
      <TextField onChange={handleChange} value={value} />
      {/* Show background color instead */}
      Color: {blockData?.data.settings.backgroundColor}
    </div>
  );
};
```

Registration the setting component:
```javascript
registerSettingComponent('setting_input', SettingInput);
```

### 6. SSR data fetching
Sometimes widget needs to convert data before Server Side Render. For example, a widget shows top 10 article list under a folder. The data needs to fetched dynamically when requesting.

Below is an example of getting image url, while the widget only stores image id. Implement the converting and register the function on `onServerSideLoad`.


```javascript

const onServerLoad = async (blockData, context)=>{
    const imageID = blockData.settings.imageID;
    fetch('/api/image/'+imageID).then((res)=>res.json()).then((data)=>{
      blockData.url = data.url;
    })
}

registerWidget(
{
   type: 'sample',
   name: 'Sample widget',
   ...
  },
  {render:SampleWidget,
   onServerSideLoad: onServerLoad
}
)
```



