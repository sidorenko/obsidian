#reactjs 
```table-of-contents
```
#### React Query
Это библиотека для управления, кэширования и синхронизации асинхронных данных (часто получаемых от сервера) в React-приложениях. React Query автоматически обновляет данные в фоновом режиме, управляет кэшированием, предоставляет функции для обработки изменения данных на сервере (мутаций) и многое другое.

```jsx
import { useQuery } from 'react-query';

const fetchPosts = async () => {
  const res = await fetch('/api/posts');
  return res.json();
};

export default function App() {
  const { data, status } = useQuery('posts', fetchPosts);
  
  // render based on the status
}
```

#### Axios
axios - это промис-базированный HTTP-клиент для браузера и Node.js. Используется для отправки HTTP-запросов и поддерживает Promise API по умолчанию. Axios предоставляет простой в использовании API со способностью к перехватыванию запросов и ответов, отмене запросов, преобразованию запросов и ответов JSON автоматически.

```jsx
import axios from 'axios';

axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

#### RTK Query (Redux Toolkit Query)
RTK Query - это библиотека для упрощения загрузки данных с сервера в Redux store. Она включена в Redux Toolkit и предоставляет set of utilities для работы с API и использования кэша для управления состоянием сервера, что упрощает обработку данных сервера.

RTK Query включает в себя механизмы для выполнения запросов на чтение (queries) и запись (mutations), и автоматически обновляет кэш в Redux store при изменении данных.

```jsx
import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react';

export const api = createApi({
  reducerPath: 'api',
  baseQuery: fetchBaseQuery({ baseUrl: '/api' }),
  endpoints: (builder) => ({
    getPosts: builder.query({
      query: () => 'posts',
    }),
  }),
});
```

Все эти инструменты могут быть использованы для работы с асинхронными данными и API, но они имеют разные возможности и подходы. Выбор между ними будет зависеть от вашего конкретного проекта и требований.