## DM Editor Configuration

Use `setDMEditorConfig()` to set DM Editor configuration. Example:

```javascript
setDMEditorConfig({
  editor: {
    defaultTheme: "my-project",
  },
  widgets: {
    heading: { defaultStyle: { _: "big-space" } },
  },
});
```

### `general`

### `editor`

| Name              | Type                                                   | Example                                                                             | Description                                                                                                                                                                                                                                                              |
| ----------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| defaultTheme      | `string`                                               | 'my-project'                                                                        | Theme when there is not theme data in page. Useful in creating page or edting page without need to theme                                                                                                                                                                 |
| favouriteWidgets  | `Array<string>`                                        |                                                                                     | Favourite widgets list.                                                                                                                                                                                                                                                  |
| categories        | `Array<{identifier:string, name:string}>`              | `[{ identifier: "myproject", name: "My project" }]`                                 | Extra widget categories.                                                                                                                                                                                                                                                 |
| defaultStyle      | `{[widget:string]:{[styleIdentifier:string]: string}}` | `{tabs: { _: "_default" }, button: { color: "primary" }, table: { _: "_default" }}` | Default selected style when a new block of a widget is added. <br /> The sample uses primary color when a button is added.                                                                                                                                               |
| ui                |                                                        |                                                                                     |                                                                                                                                                                                                                                                                          |
| zIndex            | `number`                                               |                                                                                     |                                                                                                                                                                                                                                                                          |
| enableEditControl | `boolean`                                              |                                                                                     | Enable edit control(can set block to "full edit", "view only" or "can edit but not delete"). A kind of access control on block level - only on frontend for now. <br />Need to set [canEditControl](../../reference/callbacks) callback first                            |
| projectStyles     | {default:string}                                       | `` projectStyles: { default:`background: white; `} ``                               | Inline css for all elements. It's useful to set this common css here for frontend and admin (and only appied to dm editor blocks), since sometimes it's not easy to share css file both in frontend and backend(nextjs's css needs to be from global.css not component). |

### `widgets`

Here is an example of widgets configuration. Key is the widget identifier, the settings of a widget varyies on specific widget, but there are some common properties.

```javascript
widgets: {
  text: {
          fonts: ['Arial', 'Times new man']
      },
 }
```

**Common properties:**

| Name         | Type     | Example                                                 | Description                                                | Comment |
| ------------ | -------- | ------------------------------------------------------- | ---------------------------------------------------------- | ------- |
| defaultStyle | `object` | `{_:'primary'}` <br /> `{type:'primary', size:'large'}` | Default style when creating a new block based on a widget. |         |

#### `text`

| Name  | Type            | Example                        | Description               | Comment |
| ----- | --------------- | ------------------------------ | ------------------------- | ------- |
| fonts | `Array<string>` | `['Arial', 'Times new roman']` | Font list in text widget. |         |

#### `heading`

#### `image`

### `plugins`

Note: here plugins is actually more close to callbacks.

```typescript
{
    plugins:{
    imageHandlers?: Array<
      React.ComponentType<{ image: DME.ImageInfo; onChange: (imageInfo: DME.ImageInfo) => void }>
    >;
    blockSettingActions?: Array<React.ComponentType<{ blockData: DMEData.Block }>>;
}
}
```

| Name                | Description                                                                                                                     |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| imageHandlers       | A component which handle image, eg. image editor. It should show a button first and all image actions can be in pop up.         |
| blockSettingActions | An array of components which are shown in setting panel when a block is selected. It can be eg. save a block, import to a block |
