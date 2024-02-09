Widget reference
==========

Definition
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
|  settingComponent    |  `string`    |    `true`      |    Setting component provided by DM Editor         |    See [Widget setting components](./setting-types.md)  |
|  property    |  `string`    |    `true`      |     Property of this setting. Support `setting.<property>`, eg. `'value'`, `'settings.color'`        |     |
|  parameters    |  `string`    |    `false`      |   Parameters for this setting component. The specific property depends on setting type. <br><br> Eg. in `range` setting component, you can set `{min: 1, max: 10}` as parameter.         |  See [Widget components](./setting-type.md) to get parameters    |



### Events

| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  createBlock    |  () => `object`    | true |  Invoked when creating this widget's block. Need to return an entity object(defined in `entity.ts`)      |             |

Widget Render
-----
### WidgetRenderProps

| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  blockNode    |  `DMEData.Block<Type>`    |    `true`      |             |      |
|  active    |  `boolean`    |    `true`      |             |      |


### DMEData.Block\<Type\>
| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  id    |  `string`    |    `false`      |             |      |
|  type    |  `boolean`    |    `true`      |             |      |
|  data    |  `DMEData.DefaultDataType` \| customized entity    |    `true`      |             |      |
|  children    |  `Array<DMEData.Block>`    |    `false`      |             |      |



Setting Component
--------
### SettingComponentProps


| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  property    |  `string`    |    `true`      |    Property identifier. eg.  `level`. <br /> Note: it supports `.` for mulit-level object access(max 2 levels, meaning one `.`). eg. `settings.value` means `value` property under `settings`       |      |
|  name    |  `string`    |    `true`      |    Label of the setting.         |      |
|  custom    |  `boolean`    |    `false`      |       Is custom component or not. If `true`, `name`, `property`, `value` will be ignored.      |      |
|  settingComponent    |  `string`    |    `true`      |     Registered setting component identifier, eg.'color'        |      |
|  category    |  `string`    |    `false`      |   Category of this setting.  Support `setting`(if not set)|`style` for now.      |      |
|  value    |  `unknown`    |    `false`      |     Value of the setting. The value of 'property'     |      |
|  parameters    |  `{[key: string]: unknown;}`    |    `false`      |     Parameters to the setting component. Eg. `Range` can be used for setting with different 'min' &   `max` parameter.     |      |

