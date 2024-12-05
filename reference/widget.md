registerWidget registers a widget to DM Editor.

## registerWidget

```typescript
registerWidget(
   def: DME.Widget,
   {render: ComponentType,
    onServerSideLoad?: (data: DMEData.Block, parameters: any) => Promise<void>
   }
);
```

| Name             | Type                                                 | Required | Description                                                                         | Comment               |
| ---------------- | ---------------------------------------------------- | -------- | ----------------------------------------------------------------------------------- | --------------------- |
| def              | `DME.Widget`                                         | `true`   | Definition of a widget                                                              |                       |
| render           | `render component`                                   | `true`   | The render implemenation of a widget                                                |                       |
| onServerSideLoad | `(data: DMEData.Block, serverParameters: any)=>void` | `false`  | Implemention of server side load before using DMEditorView or just data converting. | Used typically in SSR |

## Widget definition (DME.Widget)

| Name       | Type                        | Required | Description                                                                                                          | Comment                                                 |
| ---------- | --------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| type       | `string`                    | `true`   | widget type. Needs to be unique, and widget folder should have same name as type here. eg. `'heading'`               | Only allow small case, -, numbers, starting from letter |
| name       | `string`                    | `true`   | Widget name. eg. `"Heading"`, `"Image text"`                                                                         |                                                         |
| icon       | `string`                    | `true`   | Icon of the widget.                                                                                                  |                                                         |
| category   | `string`                    | `true`   | eg. `basic`                                                                                                          |                                                         |
| widgetType | `'widget'\|'list'\|'mixed'` | `false`  | Default is 'widget', `list` is for 'container'(eg. list/grid), `mixed` is for a widget which contains other widgets. |                                                         |
| settings   | `Array<WidgetSetting>`      | `true`   | For setting panel, see [WidgetSetting](#widgetsetting)                                                               |                                                         |
| events     | [object](#events)           | `false`  | Callback methods                                                                                                     |                                                         |

### WidgetSetting

| Name             | Type      | Required | Description                                                                                                                                                                    | Comment                                                             |
| ---------------- | --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| name             | `string`  | `true`   |                                                                                                                                                                                |                                                                     |
| custom           | `boolean` | `false`  | If this setting is a custom setting. If yes, all the other properties' value will be ignored.                                                                                  | See [Create a custom setting](./)                                   |
| settingComponent | `string`  | `true`   | Setting component provided by DM Editor                                                                                                                                        | See [Setting components](./setting-components.md)                   |
| property         | `string`  | `true`   | Property of this setting. Support `setting.<property>`, eg. `'value'`, `'settings.color'`                                                                                      |                                                                     |
| parameters       | `string`  | `false`  | Parameters for this setting component. The specific property depends on setting type. <br><br> Eg. in `range` setting component, you can set `{min: 1, max: 10}` as parameter. | See [Setting components](./setting-components.md) to get parameters |

### Events

| Name        | Type           | Required | Description                                                                                        | Comment |
| ----------- | -------------- | -------- | -------------------------------------------------------------------------------------------------- | ------- |
| createBlock | () => `object` | true     | Invoked when creating this widget's block. Need to return an entity object(defined in `entity.ts`) |         |

## render

`render` is a typical react component, and implement the render logic of widget, where edit and view are inside.

It uses props [WidgetRenderProps](./widget-render-props.md).

```typescript
//registerWidget(def, { render: Image });

export const Image = (props: DME.WidgetRenderProps<ImageEntity>) => {
  const { blockNode, styleClasses } = props;
  const {
    data: { src, settings, description },
  } = blockNode;

  return (
    <div>
      <img src={dmeConfig.general.imagePath(src)} />
    </div>
  );
};
```

## onServerSideLoad

onServerSideLoad is used in SSR. It's invoked before page is loaded.

!!! note

    Remember to set serverData `true` so the render can distiguish where the data is from.

```typescript
const onServerSideLoad = async (
  blockData: DMEData.Block<NewsListEntity>,
  parameters
) => {
  //fetch to list from server or remote server.
  blockData.data.list = list;
  blockData.serverData = true;
};
```
