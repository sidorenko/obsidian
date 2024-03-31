#angular 
NGXS - это библиотека управления состоянием для Angular, предоставляющая простые методы и инструменты для получения, обновления и слежения за состоянием приложения. В отличие от Redux или NgRx, которые используют концепцию "reducer" для обновления состояния, NGXS использует концепцию "actions".
![[Pasted image 20240309133442.png]]

Вот основные концепции, связанные с NGXS:

1. State: Состояние представляет часть данных в вашем приложении. Вы определяете классы состояний, которые аннотируются с помощью декоратора @State.

```typescript
@State<string>({
  name: 'message',
  defaults: 'Hello World'
})
class MessageState {}
```

2. Actions: Действия в NGXS - это команды, которые инициируют изменение состояния. Каждое действие представляет собой класс с именем и данными, которые должны быть переданы в состояние.

```typescript
class UpdateMessage {
  static readonly type = '[Message] Update';
  constructor(public payload: string) { }
}
```

3. Dispatch: Действия отправляются с использованием метода `dispatch()` на объекте `store`.

```typescript
this.store.dispatch(new UpdateMessage('Hello NGXS'));
```

4. Selectors: Selector-ы в NGXS - это функции, которые вы выбираете из состояния. Они могут быть использованы для получения каких-либо значений из состояния.

```typescript
@Selector()
static getMessage(state: string) { 
  return state; 
}

// Usage
this.store.select(MessageState.getMessage).subscribe(message => console.log(message));
```

NGXS - это отличная библиотека управления состоянием, особенно если вы ищете простое решение, которое легко поддерживать и тестировать.