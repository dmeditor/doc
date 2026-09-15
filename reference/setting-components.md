## Widget setting components

Use these identifiers in a widget setting's `settingComponent`. Bind the value with `property` (for example `'.value'` or `'settings.color'`), except for settings that do not store data, such as [help-link](#help-link).

| Identifier   | Description                                                                 | Parameters                                                                               |
| ------------ | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| align        | Align left, center, right                                                   | See [align](#align)                                                                      |
| button-group | Buttons as group                                                            | See [button-group](#button-group)                                                        |
| checkbox     | Checkbox. Value is true/false                                               | See [checkbox](#checkbox)                                                                |
| color        | Color                                                                       | See [color](#color)                                                                      |
| date         | Date input, optionally with time                                            | See [date](#date)                                                                        |
| help-link    | Help link in the setting panel. Opens a URL in a new tab or a popup dialog. | See [help-link](#help-link)                                                              |
| image        | Image with browse button                                                    | See [image](#image)                                                                      |
| input        | Text input                                                                  | See [input](#input)                                                                      |
| link         | Link with browse button                                                     | See [link](#link)                                                                        |
| number       | Number input                                                                | See [number](#number)                                                                    |
| padding      | Padding, with optional top, bottom, left, right separately                  | See [padding](#padding)                                                                  |
| range        | Slider                                                                      | See [range](#range)                                                                      |
| rich-text    | Rich text                                                                   | See [rich-text](#rich-text)                                                              |
| select       | Dropdown select                                                             | See [select](#select)                                                                    |
| switch       | On/off switch. Value is true/false                                          | See [switch](#switch)                                                                    |

### align

Left, center, and right alignment buttons. Clicking the selected value again clears it.

Value: `'left' | 'center' | 'right'`

```javascript
{
  name: 'Text align',
  settingComponent: 'align',
  property: 'settings.align',
}
```

### button-group

A group of toggle buttons. One option is selected at a time.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| options | `Array<{ text: string, value: string }>` | | Buttons to show |
| defaultSelected | `string` | | Used when the property has no value yet |

```javascript
{
  name: 'Modal size',
  settingComponent: 'button-group',
  property: '.modalSize',
  parameters: {
    options: [
      { text: 'Small', value: 'small' },
      { text: 'Medium', value: 'medium' },
      { text: 'Large', value: 'large' },
    ],
  },
}
```

### checkbox

A checkbox. Value is `true` or `false`.

```javascript
{
  name: 'Open new tab',
  settingComponent: 'checkbox',
  property: 'settings.linkNewTab',
}
```

### color

A color picker using the editor color palette, plus a custom color chooser. Click the current color to unset it.

If `colors` is set, that list is used. Otherwise colors come from `dmeConfig.editor.colors[colorGroup]`.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| colorGroup | `string` | `'default'` | Palette key in editor color config, e.g. `'text'`, `'border'`, `'background'` |
| colors | `Array<{ color: string, name?: string }>` | | Override the palette with an explicit list |

```javascript
{
  name: 'Text color',
  settingComponent: 'color',
  property: 'settings.color',
  parameters: {
    colorGroup: 'text',
  },
}
```

### date

A date input. The stored value is `{ date: string, time: string }`, where `date` is `YYYY-MM-DD` and `time` is `HH:mm`.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| withTime | `boolean` | `false` | Also show a time input |

```javascript
{
  name: 'From date',
  settingComponent: 'date',
  property: 'settings.date',
  parameters: {
    withTime: true,
  },
}
```

### help-link

!!! note "This feature is available since version 1.0.4"

Shows a help action in the setting panel. It does not bind to a widget property. `name` is used as the button text.

If `openIn` is `link`, the URL opens in a new tab. If `openIn` is `popup`, the URL is shown in a dialog iframe, with a help icon before the text.

`link` is a locale map. The current editor language is used when present, otherwise `default`.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| openIn | `'link' \| 'popup'` | `'link'` | Open the URL in a new tab, or in a popup dialog |
| showAs | `'text' \| 'button'` | `'text'` | `text` is a text button. `button` is an outlined button with a white background |
| link | `{ default: string, [locale: string]: string }` | | Locale URLs, e.g. `{ default: 'http://www.google.com', 'nor-NO': 'http://www.google.no' }` |

```javascript
{
  name: 'Help',
  settingComponent: 'help-link',
  custom: true,
  parameters: {
    openIn: 'link',
    showAs: 'text',
    link: {
      default: 'http://www.google.com',
      'nor-NO': 'http://www.google.no',
    },
  },
}
```

### image

Image preview with a browse button. The stored value is the image `src` string. Browsing uses the editor [image callback](./callbacks.md).

```javascript
{
  name: 'Image',
  settingComponent: 'image',
  property: '.src',
}
```

### input

A text field. Other MUI `TextField` attributes can be passed through `parameters`.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| updateOnUnfocus | `boolean` | `false` | If true, update the value on blur instead of on every change |

```javascript
{
  name: 'Text',
  settingComponent: 'input',
  property: '.value',
}
```

### link

A URL field with a browse button. Browsing uses the editor [link callback](./callbacks.md).

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| urlOnly | `boolean` | `false` | Only allow a URL in the chooser |
| showDialogWhenEmpty | `boolean` | `false` | Open the chooser automatically when the value is empty |
| context | `unknown` | | Passed through to the link chooser |

```javascript
{
  name: 'Link',
  settingComponent: 'link',
  property: '.link',
  parameters: { urlOnly: true },
}
```

### number

A number field. The stored value is an integer, or unset when the field is empty.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| min | `number` | | Minimum value |
| max | `number` | | Maximum value |

```javascript
{
  name: 'Items per page',
  settingComponent: 'number',
  property: '.itemsPerPage',
  parameters: { min: 0, max: 50 },
}
```

### padding

Padding as a single value, or separately for top, right, bottom, and left. A single number is stored when all sides are equal; otherwise an array `[top, right, bottom, left]`.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| min | `number` | `0` | Minimum |
| max | `number` | `100` | Maximum |
| step | `number` | `1` | Step |

```javascript
{
  name: 'Padding',
  settingComponent: 'padding',
  property: 'settings.general.padding',
  parameters: { min: 0, max: 100 },
}
```

### range

A slider. The stored value is a number.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| min | `number` | `1` | Minimum |
| max | `number` | `5` | Maximum |
| step | `number` | `1` | Step |
| showInput | `boolean` | `false` | Show a number input next to the slider |
| reverse | `boolean` | `false` | Reverse the slider direction |
| labelFormat | `string` | | Label pattern, e.g. `'H{value}'` |

```javascript
{
  name: 'Level',
  settingComponent: 'range',
  property: '.level',
  parameters: { min: 1, max: 5, reverse: true, labelFormat: 'H{value}' },
}
```

### rich-text

A rich text editor (headings, marks, lists, alignment, links, images). The stored value is Slate JSON.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| initHeight | `number` | | Editor height in pixels |

```javascript
{
  name: '',
  settingComponent: 'rich-text',
  property: '.value',
  parameters: { initHeight: 400 },
}
```

### select

A dropdown. Options can be set directly, or loaded from editor config with `optionsFrom`.

| Parameter | Type | Default | Description |
| --------- | ---- | ------- | ----------- |
| options | `Array<{ value: string \| number, label: string }>` | | Dropdown options |
| defaultValue | `string \| number` | | Initial value when none is set |
| optionsFrom | `string` | | Config path to load options from, e.g. `'widgets/content-view/views'` |

```javascript
{
  name: 'Type',
  settingComponent: 'select',
  property: '.type',
  parameters: {
    options: [
      { label: 'Text input', value: 'text' },
      { label: 'Select', value: 'select' },
    ],
  },
}
```

### switch

An on/off switch. Value is `true` or `false`.

```javascript
{
  name: 'Expanded',
  settingComponent: 'switch',
  property: '.expanded',
}
```
