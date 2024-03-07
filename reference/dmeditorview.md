## DMEditorView & dmeditorServerSideLoad

### DMEditorView
DMEditorView is used for viewing DM Editor data. It's basically 'view mode' of DMEditor. It can be used in both client and server side.

```javascript
import {DMEditorView} from 'dmeditor';

...
 <DMEditorView data={data} theme="blue" />

...
```
Below are properties:

| Name | Type | Required | Description | Comment |
|------|------|----------|-------------|------|
|  data    |  `Array<object>`    |    `true`      |      A json data from saved/converted DM Editor data.       |      |
|  theme    |  `string`    |    `false`      | Theme of the page |      |

  
### dmeditorServerSideLoad

`dmeditorServerSideLoad` asynchronically iterate all block data and invoke widgets' [`onServerSideLoad`](./widget.md#registerwidget) implementation and return udpated data.

Note: It's typical to invoike this function before page is loaded, eg. in `getServerSideProps` in nextjs.
