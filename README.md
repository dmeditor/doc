# DM Editor documentation


⚠️ this documentation is for 0.2.x

## Installation
```shell
npm install dmeditor
```


## First use
```typescript
import {registerDefaultWidgets, DMEditor} from 'dmeditor';

registerDefaultWidgets();

const App = () => {
  return <div>
      <DMEditor />
    </div>;
}
```

Use DM Editor
-------
[Use DM Editor](./tutorial/use-dmeditor.md)

[Use DM Editor for view & SSR](./tutorial/use-dmeditor-view.md)

Develop widget, style
-------
[How to make a local widget](./tutorial/how-to-make-widget.md)

[How to make widget style](./tutorial/How-to-make-a-widget-style.md)

Develop remote widget

API Reference
--------
Use DM Editor

[DMEditor, DMEditorView & dmeServerSideLoad](./reference/dmeditor.md)

[DM Editor configuration](./reference/configuration.md)

Develop widget

[Hook useEditorStore](./tutorial/useEditorStore.md)

[Widget definition & registration](./reference/widget.md)

[Widget setting components](./reference/setting-components.md)

[Widget style keys](./reference/widget-style-keys.md)

[CSS variables](./reference/css-variables.md)

[Data format](./#)

[Utility components](./reference/utility.md)

Intergrate with backend system

[Callbacks](./reference/callbacks.md)

