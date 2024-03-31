#reactjs 
Emotion - это библиотека для работы со стилями в React. Она предоставляет мощный и гибкий подход к созданию и применению <font color="#f79646">CSS с использованием JavaScript</font>. Styled Components – это одна из основных возможностей Emotion, она позволяет объявлять компоненты со встроенными стилями.

Основное преимущество данного подхода в том, что вы можете напрямую управлять своими стилями из JavaScript, включая динамическое изменение стилей на основе props компонентов.

Пример создания стилизованного компонента с помощью Emotion:

```jsx
/** @jsxImportSource @emotion/react */
import { css } from '@emotion/react'

const Button = ({ children, primary }) => (
  <button
    css={css`
      padding: 32px;
      background-color: ${primary ? 'hotpink' : 'turquoise'};
      font-size: 24px;
      border-radius: 4px;
      color: black;
      font-weight: bold;
      &:hover {
        color: white;
      }
    `}
  >
    {children}
  </button>
)

export default function App() {
  return (
    <div className="App">
      <Button primary={true}>Primary Button</Button>
      <Button primary={false}>Secondary Button</Button>
    </div>
  )
}
```

В этом примере `Button` компонент придает каждой кнопке различные цвета в зависимости от `primary` prop. Обратите внимание, что css прописывается прямо в render функции компонента, что делает стили переиспользуемыми и обеспечивает более удобный доступ к пропсам.