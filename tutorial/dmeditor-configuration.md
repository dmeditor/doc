`setDMEditorConfig` can set from predefined colors, image wash, to plugins like image editing.

```javascript
setDMEditorConfig({});
```

## For edit and view

### Handle image

This is related to image handling. It's recommanded to store relative path and use image handling to get real image.

See [intergration](../integration) about how to save image

```javascript
 {
 general: {
    imagePath: (path: string, size?: string) => {
    const prefix = size==='thumbnail'? 'thumbnail/':'default/';
    return 'https://image.com/'+prefix+path;
 }
}
```

!!! note "size"

    size can be 'thumbnail' or others.

### Device width

DM Editor uses device width setting to get device and output related css classes.

```javascript
{
 general: {
    deviceWidth: {
        mobile: 560,
        tablet: 960,
        pc: 8000,
      }
 }
}
```

!!! note "useDevice hook"

    useDevice hook is useful to use JS instead of CSS @screen to render in mobile differently. Sometimes it's much more convenient to use this hook instead of pure css, eg. you have a picture in a grid, but want it on top in mobile regardless where it is in desktop, in this way just check if it's mobile and put to upper div.

    useDevice uses deviceWidth's values here to judge which device it is.

## For edit only

### Pre defined colors

Pre defined colors are colors shown directly in setting panel, without clicking color icon.

There are some color categories: text, border, background. Below is an example.

```javascript

{editor: {
      colors: {
        text: [
          { color: "#326f4b", name: "Green" },
          { color: "#A61C00", name: "Dark red" },
          { color: "#FF0000", name: "Red" },
          { color: "#1155CC", name: "Blue" },
          { color: "#9900FF", name: "Dark purple" },
          { color: "#FF00FF", name: "Light purple" },
          { color: "#ffffff", name: "White" },
        ],
        border: [
          { color: "#000000" },
          { color: "#333333" },
          { color: "#666666" },
          { color: "#999999" },
          { color: "#cccccc" },
          { color: "#ffffff" },
        ],
        background: [
          { color: "#F3F3F3", name: "Light white" },
          { color: "#D9EAD3", name: "Light green" },
          { color: "#F4CCCC", name: "Light red" },
          { color: "#FFF2CC", name: "Light yellow" },
          { color: "#198754", name: "Green" },
          { color: "#A61C00", name: "Dark red" },
          { color: "#434343", name: "Dark gray" },
        ],
      },
}

```

### Favourite widgets

```javascript
 {editor: {
      favouriteWidgets: [
        "text",
        "heading",
        "image",
        "table",
 }
 }
```

### Default style

### Edit area background color

```javascript
{
    editor:{
      ui: {
        "bg-editarea": "#646c71",
      }
  }
}

```

### Fonts in richtext

### Special characters/Emoji in richtext

```javascript
{editor: {
    characters: [
    "♠️",
    "♥️",
    "♣️",
    "♦️",
    "😃"]
}
```
