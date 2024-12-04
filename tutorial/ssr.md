## Introduction

Using DM Editor viewing in SSR is same as [View DM Editor](../use-dmeditor#view-dm-editor-data), just need some extra work: prefetch data.

!!! sample "Some widgets need prefetch"

    For example in NewsList widget, the news list data needs to be fetched before page is loaded and it should be on server-side-fetch and widget can render on first visit, then SSO can work.

## Prefetch sample

Below code in NextJS iterates all widgets of this page and invoke `dmeServerSideLoad` of those widgets.

```javascript
import { dmeServerSideLoad } from "dmeditor";

export async function getServerSideProps(context) {
  // Get current content
  const body = content.body; //body stores dmeditor data as js object
  try {
    await dmeServerSideLoad(body || [], context);
  } catch (err) {
    //handle error
  }
  // ...
  // Set object to page props
}
```

`dmeServerSideLoad` invokes all widget's `onServerSideLoad` using concurrency way.

## Parameter to widget when prefetching

`dmeServerSideLoad` has second parameter, which will be passed to widget. In nextjs it's can be `context`, or merged context object, eg `{...context, siteName: siteName }`

Below is an example of NewsList widget's `onServerSideLoad`

```javascript
const onServerSideLoad = async (existingData, { query }) => {
  //get pagination from context's query
  let page = query.page ? parseInt(query.page) : 1;

  //get limit from settings
  const limit = existingData.data.settings.limit || 10;
  let offset = (page - 1) * limit;

  let bodyObj: any = `/*Fetch sql, graphql, etc*/`;
  const { list, count } = await serverFetch(bodyObj);

  //update widget data
  existingData.data = {
    ...existingData.data,
    list: list,
    count: count,
    page: page,
  };
  existingData.serverData = true;
};
```

See widget's [SSR Data fetching](../how-to-make-widget/#6-ssr-data-fetching)

## NextJS

Check out nextjs [sample project](https://github.com/dmeditor/dmeditor-server) .
