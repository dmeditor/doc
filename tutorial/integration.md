DM Editor supports intergration with your system, typically like your own system or general systems like CMS.

We are consistently working on implementing/co-implementing standardized CMS integration, so when you choose a CMS, it can work directly with DM Editor with little configuration.

Below shows how to do you own integration.

!!! note "MUI"

    DM Editor internally use MUI for interaction so you can use MUI components directly. Of course you can also use other component like Boostrap react or others.

## Browse images

Browse images show image assets and allows user to select one or multi image(s).

```javascript
const BrowseImage = (props: {
  value: BrowseImageCallbackParams,
  onChange: (value: BrowseImageCallbackParams) => void,
  multiple?: boolean,
}) => {
  //render image list
  return <div></div>;
};

setDMEditorCallback({
  browseImage: BrowseImage,
});
```

[Here](https://github.com/dmeditor/dmeditor/blob/main/samples/dev/callbacks/browse-image.tsx) is an example of browsing image. It shows like below.

<img src="../../assets/browse-images.jpg" width="600px">

## Browse for link

Browse for link typicall browse article, page, or image assets to get link to.

```javascript
const BrowseLink = (props: {
  value: BrowseLinkCallbackParams,
  onChange: (value: BrowseLinkCallbackParams) => void,
}) => {
  //render link list
  return <div></div>;
};

setDMEditorCallback({
  browseLink: BrowseLink,
});
```

[Here](https://github.com/dmeditor/dmeditor/blob/main/samples/dev/callbacks/browse-link.tsx) is a simple example of browsing for link, which only list hard coded links.
<img src="../../assets/browse-links.jpg" width="600px">

## Browse Data source

Plan to come in 0.2.1

## Blocks

It's useful for editor to save blocks and reuse them. They can be saved to project database, or a centeralized place crossing projects (just make sure widgets/styles are there).

### Fetch saved blocks

Below example shows how to get saved blocks of widget. The blocks can be fetched remotely from database.

```javascript
const getSavedBlocks = (widget: string) => {
  switch (widget) {
    case "heading":
      return [
        {
          name: "Big heading",
          savedData: {
            id: nanoid(),
            type: "heading",
            style: { type: "title1" },
            data: {
              level: 2,
              value: "Heading",
              settings: {},
            },
          },
        },
      ];
    default:
      return [];
  }
};

setDMEditorCallback({
  getSavedBlocks: getSavedBlocks,
});
```

### Save blocks

[Here](https://github.com/dmeditor/dmeditor/blob/33ca2ae3100a52313ffc75daa257d657a5a27d00/samples/dev/SaveBlock.tsx#L25) implemented a sample of showing saving block dialog. Below is how to configure to DM Editor.

```javascript
setDMEConfig({
  plugins: {
    blockSettingActions: [SaveBlock],
  },
});
```
