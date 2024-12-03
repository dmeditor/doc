## Widget setting components

| Identifier   | Description                                                                 | Parameters                                                                               |
| ------------ | --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| align        | Align left, center, right                                                   |                                                                                          |
| button-group | Buttons as group                                                            | `{ options: Array<{ text: string, value: string }> };`                                   |
| checkbox     | Checkbox                                                                    |                                                                                          |
| color        | Color                                                                       | `{colorGroup:string, colors:Array<{color:string, name?:string}>} `                       |
| image        | Image with browse button                                                    |                                                                                          |
| input        | Text input                                                                  | `{updateOnUnfocus?:boolean}`                                                             |
| link         | Link with browse button                                                     | `{urlOnly?:boolean}`                                                                     |
| number       | Number input                                                                | `{min?:number, max?:number}`                                                             |
| padding      | Padding setting with possibility to set top, botton, left, right separately | `{min?:number, max?:number, step?:number}` default min: 0, max: 100                      |
| range        | Slider                                                                      | `{min?:number, max?:number, step?:number}` default min:0, max: 5, step: 1                |
| rich-text    | Rich text                                                                   | `{initHeight?:number}`                                                                   |
| select       | Dropdown select                                                             | `{options:Array<{value:string \| number, label:string}>, defaultValue:string \| number}` |
| switch       | On off switch. value is true/false                                          |                                                                                          |
