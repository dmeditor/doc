## Sample code

Here is an example of viewing DM Editor data - just use component `DMEditorView`

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

### Use cases

It can be used for viewing in admin and frontend.

!!! note SSR

    For SSR you will need additional api, which fetches data for widget which needs dynamic data before page is loaded. eg. a NewsList widget should fetch list data first in this case.

    See [SSR](./ssr) for more
