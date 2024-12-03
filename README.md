# DM Editor documentation

Useful resources:

- [Simple Demo](https://demo.dmeditor.io)
- [Github Repo](https://github.com/dmeditor/dmeditor)
- [Follow our roadmap](https://github.com/orgs/dmeditor/projects/1)
- [Discussions on Github](https://github.com/dmeditor/dmeditor/discussions)

## Concepts & principles

See [DM Editor concepts and principles](./tutorial/concepts.md) to use DM Editor better.

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

Sample projects:

- [React project](https://github.com/dmeditor/dmeditor-sample/)
- [Nextjs sample](https://github.com/dmeditor/dmeditor-server/)
- Monorepo sample (on the way)

## Tutorial

Use DM Editor

- [Use DM Editor for edit and view](./tutorial/use-dmeditor.md)
- [DM Editor configuration to customize editing and viewing](./tutorial/dmeditor-configuration.md)
- [SSR prefetch](./tutorial/ssr.md)
- [System integration, like image browsing, saving block](./tutorial/integration.md)

Develop a widget

- [Make a basic widget](./tutorial/how-to-make-widget.md)
- [Make a mixed widget with other widget(s) inside](./tutorial/how-to-make-mixed-widget.md)
- [Style a widget](./tutorial/How-to-make-a-widget-style.md)

## API Reference

#### Use DM Editor

| API                                                     | Comment                                     |
| ------------------------------------------------------- | ------------------------------------------- |
| [DMEditor](./reference/dmeditor.md)                     | DMEditor, DMEditorView, dmeServerSideLoad   |
| [setDMEditorConfig](./reference/configuration.md)       | Set configurations like predefined colors   |
| [Callback configs](./reference/callbacks.md)            | Eg. for integrate with image library        |
| [CSS variables & classes](./reference/css-variables.md) | DM Editor defined css variables and classes |

#### Develop widget and style

| API                                                     | Comment                                                        |
| ------------------------------------------------------- | -------------------------------------------------------------- |
| [registerWidget](./reference/widget.md)                 | Register a widget                                              |
| [registerStyle](./reference/styles.md)                  | Resister style, style options                                  |
| [Hooks](./reference/hooks.md)                           | useEditorStore, useDevice                                      |
| [Setting components](./reference/setting-components.md) | Setting component like input, checkbox, width, etc             |
| [Widget style keys](./reference/widget-style-keys.md)   | Style keys on built in widgets                                 |
| [Utility components](./reference/utility.md)            | Utility component useful for creatint widget, eg. MiniRichText |
| [util functions](./reference/utils.md)                  | Util functions like converting json data to html               |

## Extra resources

Code as default settings/styles in project.

|                         | Comment                                |
| ----------------------- | -------------------------------------- |
| Default styles          | Built in widget styles using css-in-js |
| Default tailwind styles | Built in widget styles using tailwind  |
