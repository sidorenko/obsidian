#reactjs 
механизм, получение ссылок на нативные _dom элементы_ и _React компоненты_, обозначаемый как _рефы_ (_refs_).

``` typescript
import React, { Component, RefObject } from 'react';

class Сhecklist extends Component {
  private readonly formRef: RefObject<
    HTMLFormElement
  > = React.createRef<HTMLFormElement>();

  /**[4] */
  private resetForm() {
    /**[5] */
    this.formRef.current?.reset();
  }

  render() {
    return (
      /**[3] */
      <form ref={this.formRef}></form>
    );
  }
}

/**
 * [3] установка рефа react элементу.
 * [4] определение закрытого метода.
 * [5] необходимость применения опрератора
 * опциональной последовательности по причине
 * возможного отстутствия ссылки на нативный элемент.
 */
```