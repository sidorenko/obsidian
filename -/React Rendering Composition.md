#reactjs
В React, композиция - это основной подход для создания UI. Компоненты могут включать в себя другие компоненты, создавая иерархию, которая может представлять более сложную функциональность. Это обычно осуществляется путем включения одного компонента в JSX-рендеринг другого компонента.

Пример композиции:

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

В этом примере `App` компонент включает в себя несколько `Welcome` компонентов, каждый из которых приветствует разных людей. Здесь `App` компонент - это родительский компонент, а `Welcome` компоненты - дочерние.

Композиция часто используется вместе с `props.children`, чтобы вложить контент внутрь компонента. Например:

```jsx
function Card(props) {
  return (
    <div className='card'>
      {props.children}
    </div>
  );
}

function App() {
  return (
    <Card>
      <h2>Welcome!</h2>
      <p>This is a card component.</p>
    </Card>
  );
}
```

Композиция - это очень мощный паттерн в React, который позволяет создавать более сложные и модульные компоненты.