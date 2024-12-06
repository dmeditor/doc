WidgetRenderProps is the props type when implementing a widget render, both in edit mode and view mode.

## WidgetRenderProps with generics

| Name         | Type                                    | Description                                             |
| ------------ | --------------------------------------- | ------------------------------------------------------- |
| blockNode    | `DMEData.Block<WidgetEntityType, Node>` | See blockNode type sample below                         |
| styleClasses | `Record<string, string>`                | Style string generated                                  |
| active       | `boolean`                               | Whether the block is active. Always false in view mode. |
| path         | `number[]`                              | Block path under 'children', eg. [0,1,1]                |

### blockNode type:

blockNode is the block data (`DMEData.Block`) whose data property uses generics from `WidgetRenderProps`.

Example of image widget's rendering:

```typescript
// in Image.tsx
export const Image = (props: DME.WidgetRenderProps<ImageEntity>) => {
  const { blockNode, styleClasses } = props;
  const {
    data: { src, settings, description }, //here src is defined in ImageEntity
  } = blockNode;

  //...
};

//in entity.ts
export interface ImageEntity {
  src: string;
  description?: string;
  settings: {
    borderWidth?: number;
    borderColor?: string;
    general?: DMEData.GeneralSettingType;
  };
}
```
