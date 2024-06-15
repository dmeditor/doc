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

| Name             | Type                                                   | Example      | Description                                                                                              | Comment |
| ---------------- | ------------------------------------------------------ | ------------ | -------------------------------------------------------------------------------------------------------- | ------- |
| defaultTheme     | `string`                                               | 'my-project' | Theme when there is not theme data in page. Useful in creating page or edting page without need to theme |         |
| favouriteWidgets | `Array<string>`                                        |              |                                                                                                          |         |
| categories       | `Array<{identifier:string, name:string}>`              |              |                                                                                                          |         |
| defaultStyle     | `{[widget:string]:{[styleIdentifier:string]: string}}` |              |                                                                                                          |         |
| ui               |                                                        |              |                                                                                                          |         |
| zIndex           | `number`                                               |              |                                                                                                          |         |

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

The configuration of a plugin will depend on specific plugin.

#### `tailwind`

#### `bootstrap`
