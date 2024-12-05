BlockRender and BlockListRender can be used in widget to render other widgets inside. (Specially useful in non-basic widget like layouts, list container).

!!! tip

    Try to use `children` in data format if you want to render other widgets inside your widget, then DM Editor can do the saving for you using `updatePropsByPath`.

## BlockRender

Here is example of using BlockRender to render a block:

```typescript
<BlockRender mode={blockMode} path={path} data={blockData} />
```

Here are properties:

```typescript
interface BlockRenderProps {
  data: DMEData.Block;
  path: Array<number>;
  mode: DME.Mode; //'edit'|'view'
```

## BlockListRender

BlockListRender renders a list of blocks (children).

```typescript
<BlockRender mode={mode} blockData={children} path={path} />
```

Here are properties:

```typescript
interface BlockListRenderProps {
  blockData: DMEData.BlockList;
  path: Array<number>;
  allowedTypes?: string[] | string;
  isEmbed?: boolean;
  direction?: "vertical" | "horizontal"; //by default vertical.
  mode: DME.Mode; //'edit'|'view'
}
```
