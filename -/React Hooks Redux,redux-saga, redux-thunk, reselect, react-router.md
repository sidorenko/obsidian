#reactjs 
```table-of-contents
```
#### Hooks Redux
Redux стал интегрирован в Hook-парадигму React, предлагая свои собственные хуки для работы с Redux Store.

- `useDispatch`: Этот хук дает доступ к функции `dispatch` из Redux Store:

```jsx
const dispatch = useDispatch();
dispatch({ type: 'ACTION_NAME', payload: 'data' });
```

- `useSelector`: Этот хук позволяет извлекать данные из состояния Store, предоставляя доступ к части данных, которые вам необходимы.

```jsx
const data = useSelector(state => state.data);
```
#### Redux-Saga
Redux-Saga - это библиотека, которая целиком идет на это: сделать сайд-эффекты(Promise, setTimeout и т. д.) более управляемыми и эффективными. Он использует генераторы JavaScript для упрощения работы с асинхронным кодом.

```jsx
import { put, takeEvery } from 'redux-saga/effects'

function* fetchUser(action) {
   try {
      const user = yield call(Api.fetchUser, action.payload.userId);
      yield put({type: "USER_FETCH_SUCCEEDED", user: user});
   } catch (e) {
      yield put({type: "USER_FETCH_FAILED", message: e.message});
   }
}

function* mySaga() {
  yield takeEvery("USER_FETCH_REQUESTED", fetchUser);
}
```
#### Redux-Thunk
Redux-Thunk - это промежуточное ПО (middleware), позволяющее обрабатывать асинхронные действия в Redux. Действия в Redux по умолчанию синхронны, и это расширение позволяет вам вместо этого возвращать функцию.

```jsx
const asyncAction = () => (dispatch) => {
  setTimeout(() => {
    dispatch({ type: 'ACTION_TYPE', payload: 'data' });
  }, 1000);
};
```

**Redux-Thunk** — это промежуточное программное обеспечение (middleware) для Redux, которое позволяет вам писать действия (actions), возвращающие функцию вместо объекта. Это особенно полезно для обработки асинхронных операций, таких как запросы к серверу или задержанные вычисления, что не возможно сделать с обычными синхронными действиями в Redux.

Основные особенности и преимущества Redux-Thunk:

- **Асинхронное взаимодействие:** Позволяет легко работать с асинхронным кодом внутри действий, например, API запросы.
- **Доступ к `dispatch` и `getState`:** Внутри thunk-функций у вас есть доступ к методам `dispatch` и `getState`, что позволяет вам отправлять другие действия и получать текущее состояние хранилища.
- **Простота использования:** Redux-Thunk не требует большого изменения в архитектуре вашего приложения для начала работы, и его легко интегрировать в существующий проект Redux.
#### Reselect
Reselect - это библиотека для вычисления производных данных (селекторов), позволяющая вам мемоизировать вычисления. Комбинирование множественных селекторов вместе и мемоизация результата обеспечивает эффективность и уменьшает перерасчеты.

```jsx
import { createSelector } from 'reselect'

const shopItemsSelector = state => state.shop.items
const taxPercentSelector = state => state.shop.taxPercent

const subtotalSelector = createSelector(
  shopItemsSelector,
  items => items.reduce((acc, item) => acc + item.value, 0)
)

const taxSelector = createSelector(
  subtotalSelector,
  taxPercentSelector,
  (subtotal, taxPercent) => subtotal * (taxPercent / 100)
)

const totalSelector = createSelector(
  subtotalSelector,
  taxSelector,
  (subtotal, tax) => ({ total: subtotal + tax })
)
```

#### React-Router
— это стандартное решение для маршрутизации в приложениях React. Он позволяет вам обрабатывать навигацию между разными компонентами вашего приложения, управляя состоянием URL в браузере. Это помогает создать чувство навигации по страницам, не теряя преимуществ одностраничных приложений (SPA).

Основные особенности и преимущества React-Router:

- **Декларативная маршрутизация:** React-Router использует декларативный подход к конфигурации маршрутизации, что делает его хорошо интегрируемым с остальным React кодом.
- **Динамическая маршрутизация:** Маршрутизация настраивается динамически при выполнении приложения, что дает большую гибкость в управлении навигацией.
- **Поддержка нескольких видов истории:** Поддерживает разные виды истории браузера (browser, hash, memory), что позволяет вам адаптировать поведение маршрутизации под разные среды и требования.

Как используются вместе: Во многих современных React приложениях, особенно тех, которые имеют сложные взаимодействия данных и навигации, Redux и React-Router часто используются вместе. Redux управляет глобальным состоянием приложения, а React-Router управляет маршрутизацией, изменяя URL и отображая соответствующие компоненты в зависимости от текущего пути в URL. Это сочетание помогает разработчикам эффективно разделять управление состоянием и управление навигацией, делая код более модульным и удобным для тестирования.