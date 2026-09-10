## Widget setting components

| Identifier   | Description                                                                 | Parameters                                                                               |
| ------------ | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| align        | Align left, center, right                                                   |                                                                                          |
| button-group | Buttons as group                                                            | `{ options: Array<{ text: string, value: string }> };`                                   |
| checkbox     | Checkbox                                                                    |                                                                                          |
| color        | Color                                                                       | `{colorGroup?:string, colors?:Array<{color:string, name?:string}>} `                     |
| help-link    | Help link in the setting panel. Opens a URL in a new tab or a popup dialog. | See [help-link](#help-link)                                                              |
| image        | Image with browse button                                                    |                                                                                          |
| input        | Text input                                                                  | `{updateOnUnfocus?:boolean}`                                                             |
| link         | Link with browse button                                                     | `{urlOnly?:boolean}`                                                                     |
| number       | Number input                                                                | `{min?:number, max?:number}`                                                             |
| padding      | Padding setting with possibility to set top, botton, left, right separately | `{min?:number, max?:number, step?:number}` default min: 0, max: 100                      |
| range        | Slider                                                                      | `{min?:number, max?:number, step?:number}` default min:0, max: 5, step: 1                |
| rich-text    | Rich text                                                                   | `{initHeight?:number}`                                                                   |
| select       | Dropdown select                                                             | `{options:Array<{value:string \| number, label:string}>, defaultValue:string \| number}` |
| switch       | On off switch. value is true/false                                          |                                                                                          |

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
