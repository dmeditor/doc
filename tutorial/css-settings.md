## Intro

DM Editor can work with all mainstream CSS/react frameworks, eg. bootstrap, css-in-js(emotion, mui), tailwind, etc.

## Tailwind

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
