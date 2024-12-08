#reactjs 
```table-of-contents
```
React поддерживает <font color="#f79646">два</font> основных типа компонентов: <span style="background:#d4b106">Классовые (Class-based) и Функциональные.</span>
## Классовые компоненты

Классовые компоненты определяются как классы ES6, которые наследуют методы и свойства из React.Component. Они имеют полный набор возможностей, таких как жизненные циклы компонентов, state (состояние) и refs. Классовые компоненты объявляют метод render(), который возвращает то, что вы хотите отрендерить. Пример классового компонента React:

``` jsx
import React from 'react';

class MyClassComponent extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      counter: 0,
    };
  }

  handleClick = () => {
    this.setState({counter: this.state.counter + 1});
  }

  render() {
    return (
      <div>
        <h1>Click count: {this.state.counter}</h1>
        <button onClick={this.handleClick}>Increase</button>
      </div>
    );
  }
}

export default MyClassComponent;
```

Методы жизненного цикла в классовых компонентах React позволяют выполнять код в определенные моменты жизни компонента. Они полезны для различных задач, таких как выполнение подписок, запуск асинхронных запросов или управление ресурсами. Вот основные методы жизненного цикла, организованные по фазам их вызова:

### Фаза монтирования
Эти методы вызываются в следующем порядке при создании и вставке компонента в DOM.

#### 1. constructor(props)
   - Используется для инициализации состояния и привязки методов.
   - Пример:
     ```javascript
     constructor(props) {
       super(props);
       this.state = { count: 0 };
     }
     ```

#### 2. static getDerivedStateFromProps(props, state)
   - Вызывается перед рендером, как при монтировании, так и на последующих обновлениях. 
   - Используется редко, чаще всего для случаев, когда состояние зависит от изменения в пропсах.
   - Пример:
     ```javascript
     static getDerivedStateFromProps(props, state) {
       if (props.reset) {
         return { count: props.defaultCount };
       }
       return null;
     }
     ```

#### 3. render()
   - Чистая функция, которая должна возвращать элементы React, которые должны быть отрендерены.
   - Пример:
     ```javascript
     render() {
       return <div>Count: {this.state.count}</div>;
     }
     ```

#### 4. componentDidMount()
   - Осуществляет подписки и асинхронные запросы.
   - Вызывается один раз после первого рендеринга компонента.
   - Пример:
     ```javascript
     componentDidMount() {
       this.timerID = setInterval(this.tick, 1000);
     }
     ```

### Фаза обновления
Эти методы вызываются при обновлении компонента, обычно в результате изменений props или state.

#### 1. static getDerivedStateFromProps(props, state)
   - Аналогично использованию в фазе монтирования.

#### 2. shouldComponentUpdate(nextProps, nextState)
   - Позволяет оптимизировать производительность, предотвращая рендеринг.
   - Пример:
     ```javascript
     shouldComponentUpdate(nextProps, nextState) {
       return nextState.count !== this.state.count;
     }
     ```

#### 3. render()
   - Снова вызывает render для отрисовки UI.

#### 4. getSnapshotBeforeUpdate(prevProps, prevState)
   - Получает информацию из DOM перед возможными изменениями.
   - Пример:
     ```javascript
     getSnapshotBeforeUpdate(prevProps, prevState) {
       if (prevState.list.length < this.state.list.length) {
         const list = document.getElementById('list');
         return list.scrollHeight - list.scrollTop;
       }
       return null;
     }
     ```

#### 5. componentDidUpdate(prevProps, prevState, snapshot)
   - Выполняется после обновления компонента, можно использовать для выполнения сетевых запросов если пропсы изменились.
   - Пример:
     ```javascript
     componentDidUpdate(prevProps, prevState, snapshot) {
       if (snapshot !== null) {
         const list = document.getElementById('list');
         list.scrollTop = list.scrollHeight - snapshot;
       }
     }
     ```

### Фаза размонтирования
#### 1. componentWillUnmount()
   - Используется для очистки ресурсов (например, остановки таймеров или отмены подписок на события).
   - Пример:
     ```javascript
     componentWillUnmount() {
       clearInterval(this.timerID);
     }
     ```

Эти методы позволяют управлять поведением компонента на различных этапах его жизненного цикла, что является ключом к созданию эффективных и надежных React приложений.