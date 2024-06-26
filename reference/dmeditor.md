## DMEditor, DMEditorView, dmeServerSideLoad

### DMEditor

```javascript
import {DMEditor} from 'dmeditor';

...
 <DMEditor />

...
```

### DMEditorView

DMEditorView is used for viewing DM Editor data. It's basically 'view mode' of DMEditor. It can be used in both client and server side.

```javascript
import {DMEditorView} from 'dmeditor';

...
 <DMEditorView data={data} theme="blue" />

...
```

Below are properties:

| Name  | Type            | Required | Description                                                                | Comment |
| ----- | --------------- | -------- | -------------------------------------------------------------------------- | ------- |
| data  | `Array<object>` | `true`   | A json data from saved DM Editor data or converted by `dmeServerSideLoad`. |         |
| theme | `string`        | `false`  | Theme of the page                                                          |         |

### dmeServerSideLoad

`dmeServerSideLoad` asynchronically iterates all block data and invoke widgets' [`onServerSideLoad`](./widget.md#registerwidget) implementation and return udpated data.

Note: It's typical to invoke this function before page is loaded, eg. in `getServerSideProps` in nextjs.

**_Parameters_**

| Name    | Type            | Required | Description                                              | Comment |
| ------- | --------------- | -------- | -------------------------------------------------------- | ------- |
| data    | `Array<object>` | `true`   | Data saved from DM Editor                                |         |
| context | `object`        | `true`   | Context of the request, server info, content object, etc |         |

**return**

It returns updated data.
