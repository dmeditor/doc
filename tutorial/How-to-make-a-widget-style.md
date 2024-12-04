## How to make widget style

A widget style is 'configured csses' for a widget, where there are style options the user can select.

There are 2 type of styles: categorized(eg. button size, button color) or pre-defined(eg. main button, which includes size and color). Below is categorized styles(color):

<img src="../../assets/button-colors.png" width="300" />

!!! sample

    For button, there are categorized styles like button type(`primary`, `cancel`), button style(`fill`, `outline`), button size(`small`, `medium`, `large`) etc. Also button icons(eg. download, go to, arrow right) can be defined in style.

    Pre-defined widget styles where a develop can set everything inside one widget style, eg. for buttons developer can define `butotn-primary` / `butotn-normal` / `butotn-cancel` for a project.

### Css classes or inline css?

There are 2 ways to develop a style: css class and inline-css. Css classes way is quite handy if you use utility based css style eg. Tailwind. Note inline-css uses css-in-js way so nested css are support see [Sample in emotion](https://emotion.sh/docs/nested).

Below is an example of inline css:

```javascript
//css style
...
{
  identifier:'big-margin',
  name:'Big',
  cssStyle: `
     margin-top: 50px;
     margin-bottom: 50px;
  `,
  icon: ''
}
      `
//css class
{
    identifier: 'primary',
    name: 'Primary',
    cssClasses: { root: 'bg-blue-500 hover:bg-blue-700 text-white py-2 px-4 rounded' },
    cssStyle: '',
  }

```

### Style option Keys

A style option is not only defining the widget's root element, but children elements. eg. in table you can define classes in multiple level.

```javascript
//use classes
classes:{'root':'', tr: '', td: ''}

//use inline css
{
background: #cccccc;

.dme-w-table-tr{

}
.dme-w-table-td{
}

}

```

Note: `root` is always applied to the root element of a widget.

See full [widget style keys references](../../reference/widget-style-keys).

### How to register a style

Using below code to register categorized style and predefined style:

```javascript

//Register categorized style: icon:
registerWidgetStyle("button", {
    identifier: "icon",
    name: "Icon",
    display: "dropdown",
    options: [
      {
        name: "Go to",
        identifier: "goto",
        cssClasses: { "after-icon": "button-after-space bi bi-arrow-right" },
        cssStyle: `

        `,
      },
      {
        name: "Download",
        identifier: "download",
        cssClasses: { "after-icon": "button-after-space bi bi-download" },
        cssStyle: `

        `,
      }
      ]
   }


  //Register predefined-style submit where icon is included
  //Basically it registers style options with empty style identifier.
  registerWidgetStyleOption("button", [
    {
      name: "Submit",
      identifier: "submit",
      cssClasses: { button: "btn btn-success",
                    "after-icon": "button-after-space bi bi-send" },
      cssStyle: `
      `,
    }] )
```

See [Register style reference](../../reference/styles).

### How to register option on existing style

Add style option to an existing style.

```javascript
registerWidgetStyleOption(
  "heading",
  [
    {
      identifier: "small-margin",
      name: "Small",
      cssStyle: `
       margin-top: 10px;
       margin-bottom: 10px;      
    `,
      icon: "",
    },
  ],
  "margin"
);
```

### Set settting from style option

Sometimes you want to choose a style with possible to change setting value in settings panel.

!!! sample

    For example, define a style which has margin top 50 and you can still change in margin top setting.

```javascript
registerWidgetStyleOption(
  "heading",
  [
    {
      identifier: "small-margin",
      name: "Small",
      //here is to set settings
      settings: {
        "settings.general.padding": { value: 5 },
      },
      cssStyle: `
       margin-top: 10px;
       margin-bottom: 10px;
    `,
    },
  ],
  "margin"
);
```
