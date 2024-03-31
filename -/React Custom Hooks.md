#reactjs 
Custom Hooks в React позволяют извлекать логику компонента во воспроизводимые функции.

<font color="#f79646">Custom Hook - это обычная JavaScript функция, имя которой начинается с "use", которая может вызывать другие хуки. Подобно встроенным хукам, они не работают внутри циклов, условий или вложенных функций.</font>

Давайте создадим Custom Hook, который отслеживает размер окна браузера, например:

```javascript
import React, { useState, useEffect } from 'react';

// Custom hook
const useWindowDimensions = () => {
  const [windowDimensions, setWindowDimensions] = useState({
    width: window.innerWidth,
    height: window.innerHeight
  });

  useEffect(() => {
    function handleResize() {
      setWindowDimensions({
        width: window.innerWidth,
        height: window.innerHeight
      });
    }

    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []); // Empty array ensures effect only runs on mount/unmount

  return windowDimensions;
}
```

Теперь вы можете использовать `useWindowDimensions` в любом компоненте, чтобы получить текущий размер окна:

```javascript
function MyComponent() {
  const { width, height } = useWindowDimensions();

  return (
    <div>
      Width: {width}, Height: {height}
    </div>
  );
}
```

Custom hooks предоставляют простой и эффективный способ повторного использования логики с состоянием и логики с side effects между различными компонентами.
