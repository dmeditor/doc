You can use DM Editor for edit in admin site and view in admin and frontend.

## Edit in DM Editor

Below is a sample code of loading and saving data in DM Editor.

```typescript
import {registerDefaultWidgets, DMEData, DMEditor, DMEditorRefType} from 'dmeditor';


registerDefaultWidgets(); //note: it's a good practise to put initialization to a separate file. eg. initDMEditor.ts

export App = ()=>{
  const editorRef = useRef<DMEditorRefType>(null);

  const data= [
    {
      id: `N-LAQWihvfZv1SmUAPoQx`,
      data: {
        value: 'This is a heading',
        level: 2,
        settings: {
          align: 'left',
        },
      },
      type: 'heading',
    }]

  const initData = ()=>{
    const editor = editorRef.current;
    if (editor) {
      editor.setData(data);
    }
  };

  useEffect(() => {
    initData();
  }, []);

  const save(data: DMEData.SavedData)=>{
     console.log(data);
     window.alert('Saved');
  }

  const cancel()=>{
    //redirect
  }

return (
    <div>
      <DMEditor ref={editorRef} onSave={save} onCancel={cancel} />
    </div>
  );
}
```

### onSave

OnSave is invoked when editor clicks 'Save' button. The parameter data contains 2 properties:

- data: an Array of blocks
- page: an object of page settings.

Below is an example of data in onSave callback:

```javascript
{
  data: [
    {
      id: `N-LAQWihvfZv1SmUAPoQx`,
      data: {
        value: "This is a heading",
        level: 2,
        settings: {
          align: "left",
        },
      },
      type: "heading",
    },
  ],
  page: {title:'New page', cover_image: 'https://test.com/sample.jpg'}
}
```

### onChange

Same parameter as onSave, just invoked when there is any change(eg. typing). It can be used for eg. autosaving. Use it carefully for performance reason since it's invoked quite frequently - on every change.

### onCancel

Invoked when cancel button is clicked.

### Set data

`editor.setData(data)` sets existing data to the editor.

### Page settings and data

It's possible to customize page settings like below.

!!! note

    `title` is always the first one, and there is no need to configure `title`.

```javascript
const pageSettings: Array<DME.PageSetting> = [
  { identifier: "cover_image", name: "Cover image", type: "image" },
  { identifier: "meta_key", name: "Meta key", type: "text" },
  {
    identifier: "meta_description",
    name: "Meta description",
    type: "multitext",
  },
];

editor.setPageSettings(pageSettings);

editor.setPageData({ title: "New page", cover_image: "" });
```

Page settings looks like this:

<img src="/doc/assets/page-settings.png" width="400px">

Supports types: `text`, `multitext`, `checkbox`, `image`

## Render DM Editor data

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

### SSR rendering

SSR view is same way using DMEditorView. Just need additional action: invoke DM Editor's api so widgets can fetch dynamic data before the page is loaded. Eg. a NewsList widget can fetch list data first in this case.

See [SSR prefetch](../ssr) for more.

!!! sample "Nextjs sample"

    Check out nextjs [sample project](https://github.com/dmeditor/dmeditor-server) .

### CSS Set up

It's needed to initial some css settings by set css variables.

**`--dme=container-width` and `--dme-main-width`**

A DMEditorView has a container and a rendering area, where container's width is set in css variable `--dme-container-width` and the actual block list width is set by `--dme-main-width`.

Some widgets rely on the 2 values to implement 'full screen width', eg. 'full screen width image', 'full screen width background', 'full screen width carousel'. Below illustrate the different width.

<img src="../../assets/dmeditor-widths.png" width="800px" />

Here is typical setting sample:

```css
:root {
  --dme-container-width: 100vw;
  --dme-main-width: 1200px;
}

.dme-viewmode-mobile,
.dme-viewmode-tablet {
  --dme-main-width: 100vw;
}
```

!!! note

     Both values should be absolute or calculated value (meaning value like `100%` is not allowed, but `100vw`, `1200px`, `calc(100vw * 0.8)` are allowed).

### Tailwind

!!! note "CSS frameworks"

    DM Editor can work with all mainstream CSS/react frameworks, eg. bootstrap, css-in-js(emotion, mui), tailwind, etc.

Tailwind's utility based approache gives high performance and good resuse of styles, thus is a very good match for DM Editor.

Put below in global css so some widget's full width can work (eg. nextjs+tailwind's globals.css):

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  --dme-container-width: 100vw;
}

/*optional to remove horizontal scrollbar*/
body {
  overflow-x: hidden;
}

@media screen(md) {
  :root {
    --dme-main-width: theme(screens.md);
  }
}

@media screen(lg) {
  :root {
    --dme-main-width: theme(screens.lg);
  }
}

@media screen(xl) {
  :root {
    --dme-main-width: theme(screens.xl);
  }
}

@media screen(2xl) {
  :root {
    --dme-main-width: theme(screens.2xl);
  }
}
```
