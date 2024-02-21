Widget style keys
----------

A style key is defined by structual widgets used in widget styles. Eg. in table there is key `tr` for row, so developer can use 
```javascript
//css classes
{
cssClasses: {tr: 'bg-gray-100'}
}

//inline css style
{
cssStyle: {
.dme-w-tr{
  height: 15px;
}
}
```

Common key: `root` - the root element of a widget

| Widget | Key | Description |
|--------|-----|-------------|
|   Heading |    |             |
|   Table   |  `tr`   |     Table row        |
|        |    `td` |       Table cell      |
|        |   `th`  |   Table head          |
|   Tabs     |     |             |
|   Accordion     |     |             |
|        |     |             |
