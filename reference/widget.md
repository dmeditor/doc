Widget reference
==========

Definition file
-------

| Name | Type | Required | Description | Note |
|------|------|----------|-------------|------|
|  type    |  `string`    |    `true`      |  widget type. Needs to be unique, and widget folder should have same name as type here.  eg.  `heading`        |   Only allow small case, -, numbers, starting from letter    |
|  name    |  `string`    |    `true`      |   Widget name          |      |
|  icon    |  `string`    |    `true`      |             |      |
|  category    |  `string`    |   `true`       |             |      |
|  settings    |  `Array<WidgetSetting>`    |   `true`       |             |      |



WidgetSetting


| Name | Type | Required | Description | Note |
|------|------|----------|-------------|------|
|  name    |  `string`    |    `true`      |             |      |
|  custom    |  `boolean`    |    `true`      |             |      |
|  settingType    |  `string`    |    `true`      |             |      |
|  parameters    |  `string`    |    `false`      |             |      |
