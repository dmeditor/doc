Use DM Editor for view
=========

```typescript

export const View = ()=>{
   const data = [[
    {
      id: `N-LAQWihvfZv1SmUAPoQx`,
      style: { _: 'big-space' },
      data: {
        value: 'This is a heading',
        level: 2,
        settings: {
          align: 'left',
          // value: '',
        },
      },
      type: 'heading',
    }];

   return <div><DMEditorView data={data} /></div>;
}

```
