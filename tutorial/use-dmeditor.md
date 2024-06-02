User DM Editor
===

```typescript
import {registerDefaultWidgets, DMEditorRefType} from 'dmeditor';


registerDefaultWidgets();


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
      editor.setEditorJson(data);      
    }
  };

  useEffect(() => {
    initData();
  }, []);

return (
    <div>
      <DMEditor ref={editorRef} />
    </div>
  );
}
```
