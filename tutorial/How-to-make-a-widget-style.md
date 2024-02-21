How to make widget style
---
A widget style is configured csses for a widget, and there is style option the user can select. eg. For a button, there are style type(primary, cancel), style(fill, outline), size(small, media, large) etc. Also there are pre-defined widget styles where a develop can set everything inside one widget style, eg. for button site-primary / site-noral / site-cancel for a project.



### How to register a style

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

### How to register option on existing style

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
