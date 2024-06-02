Install DM Editor
=========

## Installation
```shell
npm install dmeditor
```


## First use
```typescript
import {registerDefaultWidgets, DMEditor} from 'dmeditor';

registerDefaultWidgets();

const App = () => {
  return <div>
      <DMEditor />
    </div>;
}
```
