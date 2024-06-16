# User DM Editor

## Simple use

Below is a simple sample of loading and saving data

```typescript
import {registerDefaultWidgets, DMEditorRefType} from 'dmeditor';


registerDefaultWidgets(); //note: it's a good practise to put initialization to a separate file. eg. initDMEditor.ts

export App = ()=>{
  const editorRef = useRef<DMEditorRefType>(null);

  const data= [
    {
      id: `N-LAQWihvfZv1SmUAPoQx`,
      data: {
        value: 'This is a heading',
        level: 2,
        settings: {
          align: 'left',
          // value: '',
        },
      },
      type: 'heading',
    }]

  const initData = ()=>{
    const editor = editorRef.current;
    if (editor) {
      editor.setData(data);
    }
  };

  useEffect(() => {
    initData();
  }, []);

  const save(data)=>{
     console.log(data);
     window.alert('Saved');
  }

return (
    <div>
      <DMEditor ref={editorRef} onSave={save} />
    </div>
  );
}
```

## Save data

## Edit options
