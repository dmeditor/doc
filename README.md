# DM Editor documentation

⚠️ Note: this documentation is still in making, final version should be ready before end of Nov 2024.

Useful resources:
- [Follow our roadmap](https://github.com/orgs/dmeditor/projects/1)
- [Discussions on Github](https://github.com/dmeditor/dmeditor/discussions)

## Installation

```shell
npm install dmeditor
```

## First example

```typescript
import { registerDefaultWidgets, DMEditor } from "dmeditor";

registerDefaultWidgets();

const App = () => {
  return (
    <div>
      <DMEditor />
    </div>
  );
};
```

## Sample projects

[See sample project](https://github.com/dmeditor/dmeditor-sample/)

## Documentation overview

### Tutorial

####

| Category       | Link                                                          | Comment                                                                                                 |
| -------------- | ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Concepts       | [DM Editor concepts](./tutorial/concepts.md)                  | Basic concepts of DM Editor                                                                             |
| Use DM Editor  | [DM Editor for editing](./tutorial/use-dmeditor.md)           | For editing                                                                                             |
|                | DM Editor for view in [client](./tutorial/use-dmeditor-view.md), [SSR](./tutorial/ssr.md)     | Render page in client or SSR or both.                                                                    |
| Develop widget | [Make a widget](./tutorial/how-to-make-widget.md)             |                                                                                                         |
|                | [Make a mixed widget](./tutorial/how-to-make-mixed-widget.md) | Mixed widget is a widget containing other widgets                                                       |
|                | [Style a widget](./tutorial/How-to-make-a-widget-style.md)    | You can use css-in-js or utility way to style widget (eg. tailwind)                                     |
|   Integration             | [Integration for assets, saving block](./tutorial/integration.md)           | Integration with your project or CMS, eg. set project style, browse image, link, save blocks |


### API Reference

#### Use DM Editor in project

| Category                | API                                                                   | Comment                              |
| ----------------------- | --------------------------------------------------------------------- | ------------------------------------ |
| Use DM Editor           | [DMEditor, DMEditorView & dmeServerSideLoad](./reference/dmeditor.md) |                                      |
| Configuration           | [setDMEditorConfig](./reference/configuration.md)                     |                                      |
| Configuration callbacks | [Callbacks](./reference/callbacks.md)                                 | Eg. for integrate with image library |
| DM Editor css variables | [CSS variables](./reference/css-variables.md)                         |                                      |

#### Develop widget

| Category              | API                                                     | Comment |
| --------------------- | ------------------------------------------------------- | ------- |
| Widget implementation | [registerWidget](./reference/widget.md)                 |         |
| State management      | [Hook useEditorStore](./tutorial/useEditorStore.md)     |         |
| Setting components    | [setting components](./reference/setting-components.md) |         |
| Widget style          | [Widget style keys](./reference/widget-style-keys.md)   |         |
| Utility               | [Utility components](./reference/utility.md)            |         |
| util               | [util functions](./reference/utils.md)            |         |

#### Data

| Category    | API                | Comment |
| ----------- | ------------------ | ------- |
| Data format | [Data format](./#) |         |

### Resources

| Category                | API           | Comment                                |
| ----------------------- | ------------- | -------------------------------------- |
| Default styles          | [Styles](./#) | Built in widget styles using css-in-js |
| Default tailwind styles | [Styles](./#) | Built in widget styles using tailwind  |
