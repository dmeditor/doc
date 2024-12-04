# Widget definition & registration reference

## Definition

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

## Register widget

### registerWidget

```javascript
registerWidget(<widget definition object>,
   {render: <widget render component>,
    onServerSideLoad: <server side load function>
   })
```

| Name             | Type                                                 | Required | Description                                                                         | Comment               |
| ---------------- | ---------------------------------------------------- | -------- | ----------------------------------------------------------------------------------- | --------------------- |
| render           | `render component`                                   | `true`   | The render implemenation of a widget                                                |                       |
| onServerSideLoad | `(data: DMEData.Block, serverParameters: any)=>void` | `false`  | Implemention of server side load before using DMEditorView or just data converting. | Used typically in SSR |
