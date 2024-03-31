#reactjs 
CSS Modules - это стиль написания CSS, который позволяет изолировать стили класса к определенному компоненту. Каждый файл стилей, который используется с CSS Modules, ограничен его областью видимости; на другие компоненты результата он не влияет.

React поддерживает CSS Modules из коробки, если вы используете Create React App или подобные сборщики проектов.

Вот пример использования CSS Modules:

1. Создайте CSS-файл `Example.module.css` в той же папке, где и ваш React-файл:

```css
/* Example.module.css */
.example {
  color: red;
}
```

2. Затем импортируйте этот файл CSS в ваш React-файл:

```jsx
import React from 'react';
import styles from './Example.module.css';

export function Example() {
  return <div className={styles.example}>This is red.</div>;
}
```

Здесь наименование класса из CSS-файла используется в компоненте React. Во время построения проекта имя класса будет заменено на уникальное имя в глобальной области видимости, чтобы избежать конфликтов стилей.

Важно отметить, что чтобы использовать CSS Modules, файл CSS должен заканчиваться на `.module.css` (это указано в конфигурации webpack по умолчанию, если вы используете Create React App).