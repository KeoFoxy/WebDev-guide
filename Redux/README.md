# Redux Toolkit

### Store

Пример конфигурации стора с использованием **Redux Toolkit**.   

```ts
import { configureStore } from '@reduxjs/toolkit';

const store = configureStore({
    preloadedState: initialState,
    reducer: {
        // List of reducers
    }
})
```

Помимо конфигурации стора также можно экспортировать его тип, если используется TypeScript.

```ts
export type App
```


