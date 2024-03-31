#reactjs 
Error Boundaries в React - это компоненты, которые перехватывают ошибки JavaScript в любой части их дерева потомков, регистрируют эти ошибки и выводят запасной UI вместо того чтобы разрушить всё приложение.

Когда в компоненте происходит ошибка во время этапа рендеринга, методы жизненного цикла или конструктора, Error Boundary может отловить эту ошибку и отобразить запасной UI. Без Error Boundary, весь компонент-дерево будет размонтирован при возникновении ошибки.

Стоит отметить, что Error Boundaries не перехватывают ошибки в обработчиках событий, асинхронном коде (например, обратных вызовах setTimeout или requestAnimationFrame), в компонентах испускающих рендер, и в случаях, когда ошибка сгенерирована на сервере. 

Вот пример Error Boundary:

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Обновить состояние так, чтобы следующий вызов рендера показал запасной UI.
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // Можно также логировать ошибку в службу отчетов
    logErrorToMyService(error, errorInfo);
  }
  
  render() {
    if (this.state.hasError) {
      // Можно отрендерить запасной UI произвольного вида
      return <h1>Something went wrong...</h1>;
    }

    return this.props.children; 
  }
}
```

Вы можете использовать ErrorBoundary в своем приложении, обернув им потенциально "опасные" компоненты. При возникновении ошибки в дереве компонентов ErrorBoundary будет перехватывать эту ошибку и выводить запасной UI, предотвращая при этом падение всего приложения. 

```jsx
<ErrorBoundary>
  <MyWidget />
</ErrorBoundary>
```