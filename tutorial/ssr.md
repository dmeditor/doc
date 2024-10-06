
SSR
=========

## SSR

SSR is similar to [DM Editor for view](use-dmeditor-view), but with prefetched data.

DM Editor has been tested on next.js.


### Invoke server load for each widget

Below code will iterate all widgets of this page and invoke `onServerSideLoad` of those widgets.

```javascript

import {dmeServerSideLoad } from "dmeditor";

const body = content.body;

await dmeServerSideLoad( body || [], context );
```

### Widget onServerSideLoad
