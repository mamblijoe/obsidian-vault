`createRoot` позволяет создать корень для отображения компонентов React внутри узла DOM браузера.

```jsx
const root = createRoot(domNode, options?)
```

## `root.render(reactNode)`

Вызовите `root.render`, чтобы отобразить часть `JSX` в узле DOM браузера корня React.

>[!tip] Можно вызвать повторно `render` на том же самом `root`. `React` обновит компоненты и если дерево компонентов совпадает с предыдущим стейты сохранятся

```js
import { createRoot } from 'react-dom/client';
import './styles.css';
import App from './App.js';

const root = createRoot(document.getElementById('root'));

let i = 0;
setInterval(() => {
  root.render(<App counter={i} />);
  i++;
}, 1000);
```

## `root.unmount()`

Вызовите `root.unmount`, чтобы уничтожить визуализированное дерево внутри корня `React`.