Use DM Editor for view
=========

## DMEditorView

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

## SSR

### NextJS
Check out nextjs [sample project](./#) .

### Tailwind
Tailwind's utility based approache gives high performance and good resuse of styles, thus is a very good match for DM Editor.

Put below in global css so some widget's full width can work (eg. nextjs+tailwind's globals.css): 

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

:root{
    --dme-container-width: 100vw;
}

/*optional to remove horizontal scrollbar*/
body{
    overflow-x: hidden;
}

@media screen(md) {
    :root{
        --dme-main-width: theme(screens.md);
    }
}

@media screen(lg) {
    :root{
        --dme-main-width: theme(screens.lg);
    }
}

@media screen(xl) {
    :root{
      --dme-main-width: theme(screens.xl);
    }
}


@media screen(2xl) {
    :root{
        --dme-main-width: theme(screens.2xl);
    }
}

```
