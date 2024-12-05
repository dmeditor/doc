## DM Editor Configuration

Use `setDMEditorConfig()` to set DM Editor configuration. Example:

```javascript
setDMEditorConfig({
  editor: {
    settingPanelWidth: 400,
  },
});
```

### `general`

| Name          | Type                                                       | Example                                               | Description                                                                                                                                                                                                                                                              |
| ------------- | ---------------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| projectStyles | {default:string}                                           | `` projectStyles: { default:`background: white; `} `` | Inline css for all elements. It's useful to set this common css here for frontend and admin (and only appied to dm editor blocks), since sometimes it's not easy to share css file both in frontend and backend(nextjs's css needs to be from global.css not component). |
| imagePath     | ` (path: string, size?: 'thumbnail' \| string) => string;` |
| deviceWidth   | `{mobile: number; tablet: number; pc: number;}`            |

### `editor`

| Name              | Type                                                   | Example                                                                             | Description                                                                                                                                                                                                                                   |
| ----------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| defaultTheme      | `string`                                               | 'my-project'                                                                        | Theme when there is not theme data in page. Useful in creating page or edting page without need to theme                                                                                                                                      |
| favouriteWidgets  | `Array<string>`                                        |                                                                                     | Favourite widgets list.                                                                                                                                                                                                                       |
| categories        | `Array<{identifier:string, name:string}>`              | `[{ identifier: "myproject", name: "My project" }]`                                 | Extra widget categories.                                                                                                                                                                                                                      |
| defaultStyle      | `{[widget:string]:{[styleIdentifier:string]: string}}` | `{tabs: { _: "_default" }, button: { color: "primary" }, table: { _: "_default" }}` | Default selected style when a new block of a widget is added. <br /> The sample uses primary color when a button is added.                                                                                                                    |
| zIndex            | `number`                                               |                                                                                     |                                                                                                                                                                                                                                               |
| enableEditControl | `boolean`                                              |                                                                                     | Enable edit control(can set block to "full edit", "view only" or "can edit but not delete"). A kind of access control on block level - only on frontend for now. <br />Need to set [canEditControl](../../reference/callbacks) callback first |
| fontFamily        | `Array<{ value: string; label: string }> `             |                                                                                     | Font families in rich text editor.                                                                                                                                                                                                            |
| fontSize          | `Array<{ value: string; label: string }> `             |                                                                                     | Font sizes in rich text editor.                                                                                                                                                                                                               |
| characters        | `Array<string>`                                        |                                                                                     | Characters, can be emoji.                                                                                                                                                                                                                     |
| settingPanelWidth | `number`                                               |                                                                                     | Default width of setting panel.                                                                                                                                                                                                               |

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
