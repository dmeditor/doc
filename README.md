# DM Editor documentation

⚠️ this documentation is for 0.2.x

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
|                | [Integrate with project](./tutorial/integration.md)           | Integration with your project or CMS, eg. set project style, browse image, link, save data, save blocks |
|                | [DM Editor for viewing](./tutorial/use-dmeditor-view.md)      | View page/section in client or SSR                                                                      |
| Develop widget | [Make a widget](./tutorial/how-to-make-widget.md)             |                                                                                                         |
|                | [Make a mixed widget](./tutorial/how-to-make-mixed-widget.md) | Mixed widget is a widget containing other widgets                                                       |
|                | [Style a widget](./tutorial/How-to-make-a-widget-style.md)    | You can use css-in-js or utility way to style widget (eg. tailwind)                                     |

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

#### Data

| Category    | API                | Comment |
| ----------- | ------------------ | ------- |
| Data format | [Data format](./#) |         |

### Resources

| Category                | API           | Comment                                |
| ----------------------- | ------------- | -------------------------------------- |
| Default styles          | [Styles](./#) | Built in widget styles using css-in-js |
| Default tailwind styles | [Styles](./#) | Built in widget styles using tailwind  |
