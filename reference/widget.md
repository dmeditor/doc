Widget reference
==========

Definition file
-------

| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  type    |  `string`    |    `true`      |  widget type. Needs to be unique, and widget folder should have same name as type here.  eg.  `'heading'`        |   Only allow small case, -, numbers, starting from letter    |
|  name    |  `string`    |    `true`      |   Widget name. eg. `"Heading"`, `"Image text"`          |      |
|  icon    |  `string`    |    `true`      |   Icon of the widget. Support base64 image or url          |      |
|  category    |  `widget\|layout`    |   `false`       |    By default `widget`         |      |
|  settings    |  `Array<WidgetSetting>`    |   `true`       |    For setting panel, see [WidgetSetting](#widgetsetting)         |      |
|  events    |  [object](#events)    |    `false`      |     Callback methods        |      |



### WidgetSetting


| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  name    |  `string`    |    `true`      |             |      |
|  custom    |  `boolean`    |    `false`      |   If this setting is a custom setting. If yes, all the other properties' value will be ignored.          |  See [Create a custom setting](./)    |
|  settingType    |  `string`    |    `true`      |             |    See [Widget setting types for setting types](./setting-types.md)  |
|  parameters    |  `string`    |    `false`      |   Parameters for this setting type. The specific property depends on setting type. <br><br> Eg. in `range` setting type, you can set `{min: 1, max: 10}` as parameter.         |  See [Widget setting types for parameters](./setting-type.md)    |



### Events

| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  createBlock    |  () => `object`    | true |  Invoked when creating this widget's block. Need to return an entity object(defined in `entity.ts`)      |             |
