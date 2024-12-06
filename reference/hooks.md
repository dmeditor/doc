## Hook useEditorStore

`useEditorStore` is a global state management hook where widget developer can get/add/update/delete block data. Below is how to get member from the hook.

```typescript
const { updateBlockByPath } = useEditorStore();
```

Below are functions in the hook:

### getSelectedBlock

Return selected block.

```typescript
getSelectedBlock: () => DMEData.Block;
```

### updateBlockByPath

Update block by path.

```typescript
updateBlockByPath: <Type = DMEData.DefaultDataType>(
    path: Array<number>,
    callback: (blockData: Type, block?: any) => void,
  ) => void;



//use in widget render:
const handleChange = (value: DME.ImageInfo) => {
    updateBlockByPath<ImageEntity>(blockPath, (blockData) => {
      blockData.src = value.src;
    });
  };
```

### updateBlockPropsByPath

Update block by path with property dynamically, eg. `'.settings.general.background'`

```typescript
updateBlockPropsByPath: (
    path: Array<number>,
    propName: string, //eg. '.settings.general.background'
    propValue: undefined | string | number | boolean | Array<unknown>,
  ) => void;
```

### removeByPath

Remove a block by path.

```typescript
removeByPath: (path: Array<number>) => void;
```

### startAddBlock

Start adding block - show adding panel.

```typescript
 startAddBlock: (
    context: Array<number>,
    index: number,
    position: AddBlockPosition,
    extraParams: { types?: Array<string> | string; isEmbed?: boolean },
  ) => void;
```

## Hook useDevice

`useDevice` is used in client to detect current device using screen width. In SSR it alway return `''` but will reexecute in client - meaning it can have refresh but not much noticable.

It's useful if you want to render differently using javascript as condition - not css.

!!! sample

    An good example is put picture on top in mobile regardless if it's in left or right in desktop. If the picture on on right, it's hard to put to top (using flex can do but what if it's 3 columns and the image is in middle). using this hook can just render to top when it's in mobile.

Below is a simple sample:

```jsx
//return "" | "mobile" | "tablet";
const device = useDevice();

return <div>{device==='mobile'&&<img .../>}
        <div>
        <div>1</div>
        {device!=='mobile'&&<div><img ... /></div>}
        </div>
<div>
```
