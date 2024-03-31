#reactjs 
Portals в React - это способ рендеринга дочерних компонентов в DOM-узел, который существует вне DOM-иерархии родительского компонента.

Порталы обычно используются для компонентов, которым нужно "выходить за рамки" их родительских элементов, таких как модальные окна, всплывающие подсказки, уведомления и другие элементы, которые должны отображаться поверх остального контента.

Вот пример использования `ReactDOM.createPortal`:

```jsx
class Modal extends React.Component {
  constructor(props) {
    super(props);
    this.el = document.createElement('div');
  }

  componentDidMount() {
    // Вставляем элемент в DOM в момент монтирования компонента
    document.body.appendChild(this.el);
  }

  componentWillUnmount() {
    // Удаляем элемент из DOM при размонтировании
    document.body.removeChild(this.el);
  }

  render() {
    // Используем ReactDOM.createPortal для рендера children в созданный div
    return ReactDOM.createPortal(
      this.props.children,
      this.el
    );
  }
}
```

В этом примере `Modal` компонент создает новый `div`, который добавляется в `body`. Затем, с помощью `ReactDOM.createPortal`, все дочерние элементы `Modal` рендерятся в этот новый `div`, а не как дочерние элементы `Modal` в основной иерархии React DOM. Это позволяет `Modal` визуализироваться поверх других элементов на странице, поскольку его DOM-элемент прямо внутри `body`.