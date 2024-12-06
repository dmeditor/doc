##registerWidgetStyle, registerWidgetStyleOption

When we talk about widget styles, it's actually style options in detail. A style option defines all the css to a block.

`registerWidgetStyle` defines a style 'category' which contains style options, shown as dropdown, or button-group, etc.

`registerWidgetStyleOption` can register options to a style (a style category), but if style parameter is ignored it registers to `_`, which is kind of 'root category' - then the style is a pre-defined style.

```typescript
export function registerWidgetStyle(widget: string, style: DME.WidgetStyle) {}

export function registerWidgetStyleOption(
  widget: string,
  styleOptions: Array<DME.WidgetStyleOption>,
  style?: string
) {}
```

Below are type definitions of `WidgetStyle`, `WidgetStyleOption` and related.

```typescript
interface WidgetStyle {
  identifier: string;
  display?: Display; // 'dropdown' is default if not set. 'dropdown' | 'button-group' | 'radio' | 'inline-block'
  name: string; // style name if not set.
  options: WidgetStyleOption[];
}

interface WidgetStyleOption {
  identifier: string; //option identifier
  name: string; // name of the option
  icon?: string; //path of the icon
  cssClasses?: WidgetStyleClasses; //eg. {root:'p-10 bg-black'} where root is widget's style key.
  cssStyle: string; // CSS style using CSS-in-JS.

  //set block value. eg. {'setting.background': '#cccccc'}
  settings?: WidgetStyleOptionSettings;
}

export type WidgetStyleClasses = Record<string, string>;

export interface WidgetStyleOptionSettings {
  [key: string]: { value: any };
}
```

!!! tip "Can combine cssClasses with cssStyle"

    It's posssible to combine `cssClasses` with `cssStyle` in some cases, eg. in button
    ```javascript
    {
        //...
        cssClasses:{button:'btn-large custom-round'}
        cssStyle:`
            .custom-round{
                border-raidus: 10px;
            }
       `
       //...
    }
    ```
