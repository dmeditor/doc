
SSR
=========

## SSR

SSR is similar to [DM Editor for view](use-dmeditor-view), but with prefetched data.

### NextJS
Check out nextjs [sample project](./#) .


### Invoke server load for each widget

Below code will iterate all widgets of this page and invoke `onServerSideLoad` of those widgets.

```javascript

import {dmeServerSideLoad } from "dmeditor";

const body = content.body;

await dmeServerSideLoad( body || [], context );
```

### Widget onServerSideLoad


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
