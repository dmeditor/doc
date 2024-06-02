Use DM Editor for view
=========

### DMEditorView

```typescript

import {registerDefaultWidgets, DMEditorView} from 'dmeditor';


registerDefaultWidgets(); //Note: it's a good practise to put initialization to a separate file. eg. initDMEditor.ts

export const View = ()=>{
   const data = [[
    {
      id: `N-LAQWihvfZv1SmUAPoQx`,
      data: {
        value: 'This is a heading',
        level: 2,
        settings: {
          align: 'left',
          // value: '',
        },
      },
      type: 'heading',
    }];

   return <div><DMEditorView data={data} /></div>;
}

```
