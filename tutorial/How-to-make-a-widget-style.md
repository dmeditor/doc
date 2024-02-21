How to make widget style
---
A widget style is configured csses for a widget, and there is style option the user can select. 

For example for button, there are styles like button type(primary, cancel), button style(fill, outline), button size(small, media, large) etc. Also there are pre-defined widget styles where a develop can set everything inside one widget style, eg. for buttons developer can define site-primary / site-noral / site-cancel for a project.

There are 2 ways to develop a style: css class and inline-css. Css classes way is quite handy if you use utility based css style eg. Tailwind. Note inline-css uses css-in-js way so nested css are support see [Sample in emotion](https://emotion.sh/docs/nested).


### 1. How to register a style

Using below code to register style

```javascript
registerWidgetStyle('heading', {
    identifier:'margin',
    name:'Margin',
    display:'inline-block',
    options:[{
      identifier:'big-margin',
      name:'Big',
      cssStyle: `
         margin-top: 50px;
         margin-bottom: 50px;
      `,
      icon: ''  
    }]
})
```

### 2. How to register option on existing style

Add style option to an existing style.

```javascript
registerWidgetStyleOption('heading', 
[{
    identifier:'small-margin',
    name:'Small',
    cssStyle: `
       margin-top: 10px;
       margin-bottom: 10px;      
    `,
    icon: ''  
}], 'margin')
```

### 3. How to register pre-defined style

Registering pre-define style is almost same as registering a normal style, just with empty style name.

For instance, you want to register a site related heading to heading:
```javascript
registerWidgetStyleOption('heading', [{
        identifier:'theme',
        name:'Theme-heading',
        cssStyle: `
        margin-top: 10px;
        margin-bottom: 10px;
        color: green;
     `}]
    );

```
