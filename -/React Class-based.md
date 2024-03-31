#reactjs 
React поддерживает <font color="#f79646">два</font> основных типа компонентов: Классовые (Class-based) и Функциональные.
**Классовые компоненты:** Классовые компоненты определяются как классы ES6, которые наследуют методы и свойства из React.Component. Они имеют полный набор возможностей, таких как жизненные циклы компонентов, state (состояние) и refs. Классовые компоненты объявляют метод render(), который возвращает то, что вы хотите отрендерить. Пример классового компонента React:

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