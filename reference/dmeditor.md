## DMEditor, DMEditorView, dmeServerSideLoad

### Component DMEditor

#### Component props

```typescript
export interface DMEditorProps {
  projectStyle?: string;
  onSave?: (savedData: DMEData.SavedData) => void;
  onChange?: (savedData: DMEData.SavedData) => void;
  onCancel?: (callback: () => void) => void;
}
```

**projectStyle**

[Pre-configured project styles](../configuration/#general)' key. If not set, it uses `default`.

**onSave**

Invoked when a save button is clicked.

`savedData`:

```typescript
{
    data: Block[];
    page: Page;
}
```

`page`:

```typescript
{
    title: string;
    [index: string]: string | boolean | undefined;
}
```

**onChange**

Invoked when there is change when editing (eg. typing in rich text).

**onCancel**

Invoked when cancel button is clicked.

#### Ref object

Ref object allows developers to operate DMEditor reference.

```typescript
export interface DMEditorRefType {
  setData: (data: string | Array<DMEData.Block>) => void;
  setPageSettings: (settings: Array<DME.PageSetting>) => void;
  setPageData: (data: DMEData.Page) => void;
}
```

### DMEData.Block

DMEData.Block is a `node of block` and used everywhere, from saving, view, to widget rendering. Basically a DM Editor document is a list of `DMEData.Block` tree.

Here is the structure:

```typescript
{
 type: string;
 id?: string;
 style?: Record<string, string>;
 isEmbed?: boolean;
 serverData?: boolean; // Only set by server.
 allowedTypes?: Array<string>; // Used for list/grid/mixed-widget.
 data: unknown; //defined in entity
 children: Array<{id:string, data:unknow, children:<unknown>}> //children create a tree structure
 editControl?: number; // Edit control value.
}
```

**style**

Predefined style is set like this: `{_:'submit'}`, where `_` is reserved key for predefined styles.

Categorized style is set like this: `{color:'primary', size: 'large'}`

**data**

data is defined by widget in widget entity.

**children**
Children makes the block as a tree.

!!! note "Using `children` for parent-children strucutre so DM Editor can handles update"

    Using `updateBlockPropsByPath` DM Editor is able to save block to storage based on the `children` path(eg. `0/1/1` is the block first on root level, 2nd on fisrt level, 2nd on second level).

    See [updatePropsByPath](../hooks#updatepropsbypath).

### DMEditorView

DMEditorView is used for viewing DM Editor data. It's basically 'view mode' of DMEditor. It can be used in both client and server side.

```javascript
import {DMEditorView} from 'dmeditor';

...
 <DMEditorView data={data} theme="blue" />

...
```

Below are properties:

| Name  | Type                   | Required | Description                                                                | Comment |
| ----- | ---------------------- | -------- | -------------------------------------------------------------------------- | ------- |
| data  | `Array<DMEData.Block>` | `true`   | A json data from saved DM Editor data or converted by `dmeServerSideLoad`. |         |
| theme | `string`               | `false`  | Theme of the page                                                          |         |

### dmeServerSideLoad

`dmeServerSideLoad` asynchronically iterates all block data and invoke widgets' [`onServerSideLoad`](./widget.md#registerwidget) implementation and return udpated data.

Note: It's typical to invoke this function before page is loaded, eg. in `getServerSideProps` in nextjs.

**_Parameters_**

| Name    | Type                   | Required | Description                                              | Comment |
| ------- | ---------------------- | -------- | -------------------------------------------------------- | ------- |
| data    | `Array<DMEData.Block>` | `true`   | Data saved from DM Editor                                |         |
| context | `object`               | `true`   | Context of the request, server info, content object, etc |         |

**return**

Updated data on `Array<DMEData.Block>`.
