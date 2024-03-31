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