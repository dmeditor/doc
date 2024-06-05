# DM Editor documentation

⚠️ this documentation is for 0.2.x

## Installation

```shell
npm install dmeditor
```

## First use

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

## Tutorial

#### Concepts

[DM Editor concepts](./tutorial/concepts.md)

#### Use DM Editor

[Use DM Editor](./tutorial/use-dmeditor.md)

[Use DM Editor for view & SSR](./tutorial/use-dmeditor-view.md)

#### Develop widget, style

[Make a widget](./tutorial/how-to-make-widget.md)

[Style a widget](./tutorial/How-to-make-a-widget-style.md)

## API Reference

Use DM Editor in project

| Category                | API                                                                   | Comment                              |
| ----------------------- | --------------------------------------------------------------------- | ------------------------------------ |
| Use DM Editor           | [DMEditor, DMEditorView & dmeServerSideLoad](./reference/dmeditor.md) |                                      |
| Configuration           | [setDMEditorConfig](./reference/configuration.md)                     |                                      |
| Configuration callbacks | [Callbacks](./reference/callbacks.md)                                 | Eg. for integrate with image library |
| DM Editor css variables | [CSS variables](./reference/css-variables.md)                         |                                      |

Develop widget

| Category              | API                                                     | Comment |
| --------------------- | ------------------------------------------------------- | ------- |
| Widget implementation | [registerWidget](./reference/widget.md)                 |         |
| State management      | [Hook useEditorStore](./tutorial/useEditorStore.md)     |         |
| Setting components    | [setting components](./reference/setting-components.md) |         |
| Widget style          | [Widget style keys](./reference/widget-style-keys.md)   |         |
| Utility               | [Utility components](./reference/utility.md)            |         |

Data

| Category    | API                | Comment |
| ----------- | ------------------ | ------- |
| Data format | [Data format](./#) |         |
