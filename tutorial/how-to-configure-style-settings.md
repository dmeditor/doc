# How to configure style settings

Developer can configure available settings and widget styles, based on context (root widget, level, self widget, root widget's style, etc). This gives flexibility for developer to `tune` DM Editor to fit project's need, more importantly doesn't give too much unneeded settings to editor.

!!! note "This feature is avaiable after 0.2.3"

## Sample

In below's code, it allows padding and background color only for the hero-text's image (hero image), and hides all style options.

```javascript
{
    path: 'hero',
    rootType: 'hero-text',
    config: {
        settings: ['container-padding', 'container-background-color'],
        styles:{}
    }
}
```

## Set up

Here is an sample of style configuration: [full sample](./styleConfig.txt)

Set to DM Editor:

```javascript
setDMEditorConfig({
  //...
  editor: {
    configStyleSettings: styleConfig,
  },
});
```

## Configuration based on rule

Under `block` section, DM Editor trues to fix rule which matches the context. If the rule is matched it will use this rule, so the order matters - rule on top will have higher priority.

### Condition rule

The rule can be based on root type, eg. `hero-text` or `_` (page root), or path, which is the path under a `mixed widget` or page root. Here are the conditions:

| Key         | Type                 | Description          | Example                           |
| ----------- | -------------------- | -------------------- | --------------------------------- |
| `rootType`  | `string`             | Root type            | 'hero-text', '\_'                 |
| `rootStyle` | `string`             | Root block' styles   | '\_:\_default'                    |
| `path`      | `string`             | Path to 'root'       | 'hero' ,'list', 'list/0'          |
| `level`     | `number`             | level to 'root'      | 1, 2                              |
| `blockType` | `string`, `string[]` | current block's type | 'image', 'list',['image', 'text'] |

### Config value

See below code, where `settings` sets available settings and `styles` sets available widget styles(empty object will disable all styles).

```javascript
config:{
    settings: ['container-padding', 'container-background-color'],
    styles:{_:['_default', "big"]}
}
```

## Sample scenarios

Below are some scenarios.

### Setting for root list

```javascript
{
    rootType: '_',
    level: 1,
    config: {
        settings: defaultRootList,
    },
},
```

### Settings for hero text

```javascript
//hero-text
    {
      path: 'hero',
      rootType: 'hero-text',
      config: {
        settings: ['container-padding', 'container-background-color'],
      },
    },
    {
      path: 'list',
      rootType: 'hero-text',
      config: {
        settings: ['container-padding', 'container-background-color'],
        builtInSettings: ['list-item-gap'],
        styles: {},
      },
    },
    {
      level: 2,
      rootType: 'hero-text',
      config: {
        settings: ['container-padding', 'container-margin-top', 'container-background-color'],
      },
    },
```
