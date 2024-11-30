# DM Editor documentation

⚠️ Note: this documentation is still in making, final version should be ready before end of Nov 2024.

[Simple Demo](https://demo.dmeditor.io)

Useful resources:

- [Github Repo](https://github.com/dmeditor/dmeditor)
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

[Sample project](https://github.com/dmeditor/dmeditor-sample/)

## Documentation overview

### Tutorial

Concept

- [DM Editor concepts](./tutorial/concepts.md)

Use DM Editor

- [Edit in DM Editor](./tutorial/use-dmeditor.md)
- [View DM Editor data](./tutorial/use-dmeditor-view.md)
- [SSR](./tutorial/ssr.md)

Develop a widget

- [Make a widget](./tutorial/how-to-make-widget.md)
- [Make a mixed widget](./tutorial/how-to-make-mixed-widget.md)
- [Style a widget](./tutorial/How-to-make-a-widget-style.md)

Integration

- [Integration for assets, saving block](./tutorial/integration.md)

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
| util                  | [util functions](./reference/utils.md)                  |         |

#### Data

| Category    | API                | Comment |
| ----------- | ------------------ | ------- |
| Data format | [Data format](./#) |         |

### Resources

| Category                | API           | Comment                                |
| ----------------------- | ------------- | -------------------------------------- |
| Default styles          | [Styles](./#) | Built in widget styles using css-in-js |
| Default tailwind styles | [Styles](./#) | Built in widget styles using tailwind  |
