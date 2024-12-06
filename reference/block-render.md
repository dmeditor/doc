BlockRender and BlockListRender can be used in widget to render other widgets inside. (Specially useful in non-basic widget like layouts, list container).

!!! tip

    Try to use `children` in data format if you want to render other widgets inside your widget, then DM Editor can do the saving for you using `updatePropsByPath`.

## BlockRender

Here is example of using BlockRender to render a block:

```typescript
<BlockRender mode={blockMode} path={path} data={blockData} />
```

Here are properties:

| Name | Type             | Required | Description |
| ---- | ---------------- | -------- | ----------- |
| data | `DMEData.Block`  | true     | Block data  |
| path | `Array<number>`  | true     | Block path  |
| mode | `'edit'\|'view'` | true     | Render mode |

## BlockListRender

BlockListRender renders a list of blocks (children).

```typescript
<BlockRender mode={mode} blockData={children} path={path} />
```

Here are properties:

| Name         | Type                         | Required                             | Description                       |
| ------------ | ---------------------------- | ------------------------------------ | --------------------------------- |
| blockData    | `DMEData.BlockList`          | true                                 | Block list                        |
| path         | `Array<number>`              | true                                 | Block path                        |
| mode         | `'edit'\|'view'`             | true                                 |                                   |
| allowedTypes | `string[] \| string`         | false                                | Allowed type when adding          |
| isEmbed      | boolean                      | false                                | Is embeded. Used in mixed widget. |
| direction    | `"vertical" \| "horizontal"` | By default vertical if not set.false |                                   |
