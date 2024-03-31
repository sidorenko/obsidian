#reactjs 
```table-of-contents
```
#### REST (Representational State Transfer)
REST описывает стиль архитектуры программного обеспечения, который определяет набор правил для создания веб-сервисов. Web services, которые следуют стилю проектирования REST, часто называются RESTful API. Большинство современных веб- и мобильных приложений используют RESTful APIs за их простоту, надежность и производительность.

Компонент React, который использует RESTful API для получения данных, может выглядеть так:

```jsx
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function App() {
  const [data, setData] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      const response = await axios.get('http://example.com/api/data');
      setData(response.data);
    };

    fetchData();
  }, []);

  return (
    <div>
      {data && <div>{data.title}</div>}
    </div>
  );
}
```

#### SWR (Stale-While-Revalidate) в React
SWR - это библиотека, разработанная Vercel, для загрузки данных в приложении React. Стратегия Stale-While-Revalidate подразумевает немедленное использование кэшированных (устаревших) данных (если они доступны), а затем отправку запроса на обновление этих данных. Если запрос успешно выполнился, кэшированные данные обновляются.

Пример использования SWR в React:

```jsx
import useSWR from 'swr';

function Profile() {
  const { data, error } = useSWR('/api/user', fetch);

  if (error) return <div>Failed to load</div>;
  if (!data) return <div>Loading...</div>;

  return <div>Hello {data.name}!</div>;
}
```

SWR автоматически обрабатывает множество вещей: кэширование, повторные запросы, обработку ошибок, обновления данных и многое другое. Именно поэтому библиотека стала популярной для работы с асинхронными данными в React.