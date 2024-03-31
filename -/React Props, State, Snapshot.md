#reactjs
```table-of-contents
```
Class Component имеет три параметра базового типа
```typescript
class Timer extends Component { 
	render() { 
		return null; 
		} 
	}
```

Component<**Props, State, Snapshot**>

#### Props (Свойства) 
В React `props` это короткое от слова properties (свойства). Это основной способ передачи данных от родительских компонентов к дочерним. Props являются "read-only", что означает, что дочерний компонент не может изменить пропсы, полученные от родительского компонента.

Пример использования props:

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return <Welcome name="Sara" />;
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```
##### default prop values
##### PropTypes typechecking
#### State (Состояние)
`State` - это объект, который содержит данные, специфические для компонента и которые могут изменяться в течение жизненного цикла компонента. В отличие от props, состояние полностью контролируется самим компонентом и может быть изменено.

Пример использования state в классовом компоненте:

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}
```

##### Initial state
В React "initial state" (начальное состояние) является состоянием компонента на момент его инициализации. Состояние в React используется для хранения данных, которые могут изменяться со времени или в ответ на взаимодействия пользователя.

В классовых компонентах React, начальное состояние устанавливается в конструкторе:

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0, // начальное состояние
    };
  }
  // ...
}
```

В функциональных компонентах начальное состояние устанавливается с помощью хука `useState`:

```jsx
import React, { useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0); // начальное состояние

  // ...
}
```

В каждом из этих примеров, мы устанавливаем начальное состояние `count` как `0`. В дальнейшем эту переменную `count` можно изменить вызывая `this.setState({ count: newValue })` в классовом компоненте или `setCount(newValue)` в функциональном компоненте. Компонент будет заново отрендерен, чтобы отразить новые данные.

Обратите внимание, что состояние является собственностью компонента и находится только внутри него. Все изменения состояния должны происходить внутри компонента, и не рекомендуется напрямую изменять `this.state` - всегда используйте `setState`.
##### setState
`setState` - это функция в React, используемая для обновления состояния компонента. Когда состояние изменяется, компонент повторно рендерится. Это один из способов вызвать обновление компонента в React. Эта функция встречается в классовых компонентах React.

Вот базовый пример:

```jsx
class MyClassComponent extends React.Component {
  constructor(props) {
    super(props);
    
    // Задаем начальное состояние
    this.state = {
      count: 0
    };
    
    // Привязываем обработчик события к контексту
    this.handleClick = this.handleClick.bind(this);
  }
  
  // Обработчик события, который вызывает setState
  handleClick() {
    this.setState({ count: this.state.count + 1 });
  }
  
  // Рендер компонента
  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={this.handleClick}>Click me</button>
      </div>
    );
  }
}
```

В этом примере при каждом клике на кнопку состояние `count` обновляется.

В функциональных компонентах, для обновления состояния используется хук `useState`:

```jsx
import React, { useState } from 'react';

function MyFunctionComponent() {
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

В этом примере, `useState(0)` возвращает массив из двух элементов: первый - текущее значение `count`, второй - функция `setCount`, которая обновляет `count` и вызывает перерендеринг компонента.
##### stateful vs stateless components

В React два типа компонентов - stateful и stateless. 

1. **Stateful Components (Компоненты со состоянием):**
Stateful компоненты, также известные как "классовые" компоненты или "умные" компоненты, имеют внутреннее состояние. Они отслеживают изменения в течение времени и могут содержать логику работы с состоянием. 

Пример Stateful компонента : 

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
       name: '',
    };
  }
  
  render() {
    return (
         <div>
        <input onChange={(e) => this.setState({ name: e.target.value })} />
        <p>{this.state.name}</p>
      </div>
    );
  }
}
```

2. **Stateless Components (Компоненты без состояния):**
Stateless Components, также известные как "функциональные" компоненты или "тупые" компоненты, являются простыми компонентами, которые не имеют своего внутреннего состояния и зависят от входных данных (props) для отображения своего вывода.

Пример Stateless компонента : 

```jsx
const App = (props) => {
  return (
    <div>
      <p>{props.name}</p>
    </div>
  );
}
```

Тем не менее, с введением React Hooks, фактически каждый функциональный компонент может теперь использоваться как stateful компонент, посредством использования хука `useState`.

```jsx
import React, { useState } from 'react';

const App = () => {
  const [name, setName] = useState("");
  
  return (
    <div>
      <input onChange={(e) => setName(e.target.value)} />
      <p>{name}</p>
    </div>
  );
}
```
#### Snapshot (снимок)
Snapshot обычно используется с методом жизненного цикла `getSnapshotBeforeUpdate`, чтобы захватить некоторые значения из DOM перед его обновлением. Значение, возвращаемое `getSnapshotBeforeUpdate`, передается в `componentDidUpdate`, где его можно использовать для обновления состояния или выполнения некоторых действий после обновления компонента.
