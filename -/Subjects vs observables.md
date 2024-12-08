#rxjs 
[project](https://stackblitz.com/edit/promise-vs-observable-example-kba756?file=src%2Fapp%2Fapp.component.ts)

вы передаете объект с помощью метода next и complete. Вы вызываете next и complete в теле функции. В обоих случаях тело функции не выполняется до тех пор, пока вы не вызовете source.subscribe() или просто вызовете функцию напрямую как source() в другом примере. Это потому, что observables — это просто специализированные функции. 

------------------

[habr](https://habr.com/ru/post/568064/)

``` js
const observable = Rx.Observable.create((observer) => {
  let r = Math.random();
  console.log(r);
    observer.next(1);  
    observer.next(2);  
});  
// subscription 1  
observable.subscribe((data) => {  
  console.log(data);   
});  
// subscription 2  
observable.subscribe((data) => {  
   console.log(data);   
});  
```

``` js

/**
 * A simple object with a `next` and `complete` callback on it.
 */
interface Observer<T> {
  next: (value: T) => void;
  complete: () => void;
}
 
/**
 * A function that takes a simple object with callbacks
 * and does something them.
 */
const source = (subscriber: Observer<number>) => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  subscriber.complete();
};
 
// Usage
console.log('start');
source({
  next: console.log,
  complete: () => console.log('done'),
});
console.log('stop');

```


### Subjects vs Observables в RxJS

В RxJS как Subjects, так и Observables являются фундаментальными концепциями, используемыми для обработки асинхронных и основанных на событиях программ с помощью последовательностей наблюдений. Понимание различий между ними и знание, когда использовать каждый из них, помогает эффективно управлять потоком данных в приложении.

#### Observables
**Описание:**
- Observables — это основной тип в RxJS. Они представляют собой ленивые коллекции для передачи множества значений. Они передают данные или события со временем и определяют, как данные будут произведены.

**Ключевые особенности:**
- **Ленивая оценка:** Observables являются ленивыми, т.е. код, который генерирует значения, выполняется только при создании подписки.
- **Юникаст:** Каждый подписчик имеет независимый экземпляр выполнения observable. Observables по умолчанию не делят выполнение и побочные эффекты между несколькими подписчиками.

**Примеры использования:**
Вот пример использования базового observable в RxJS:

```javascript
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  setTimeout(() => {
    subscriber.next(4);
    subscriber.complete();
  }, 1000);
});

console.log('Перед подпиской');

observable.subscribe({
  next(x) { console.log('получено значение ' + x); },
  error(err) { console.error('произошла ошибка: ' + err); },
  complete() { console.log('завершено'); }
});

console.log('После подписки');
```

**Плюсы и минусы:**
- **Плюс:** Настраиваемый и мощный для создания сложных асинхронных последовательностей.
- **Минус:** Не переиспользуем после завершения или ошибки.

#### Subjects
**Описание:**
- Subjects одновременно являются и Observable, и Observer. Это позволяет Subjects рассылать данные множеству наблюдателей, то есть они могут как излучать данные, так и подписываться на них.

**Ключевые особенности:**
- **Мультикаст:** Subjects поддерживают мультикаст. Они делят один путь выполнения между несколькими подписчиками.
- **Интерфейс Observer:** Subjects могут выступать в роли производителей данных, вызывая `.next(value)`, что делает их полезными для императивной передачи данных.
- **Типы Subjects:** Существуют различные варианты, такие как `BehaviorSubject`, `ReplaySubject` и `AsyncSubject`, которые обеспечивают дополнительную настройку поведения.

**Примеры использования:**
Пример с использованием простого Subject:

```javascript
import { Subject } from 'rxjs';

const subject = new Subject();

subject.subscribe({
  next: (value) => console.log(`Наблюдатель A: ${value}`)
});

subject.subscribe({
  next: (value) => console.log(`Наблюдатель B: ${value}`)
});

subject.next(1);
subject.next(2);
```

**Плюсы и минусы:**
- **Плюс:** Хорош для вещания значений или событий множеству наблюдателей.
- **Минус:** Иногда может быть сложно обеспечить правильное состояние завершения для предотвращения утечек памяти.

### Заключение
- **Когда использовать Observables:** Используйте, когда вам нужен одиночный, неделящийся поток данных, где подписчики должны независимо оперировать передаваемыми данными. Идеально подходит для обработки HTTP-запросов, ввода пользователей или других индивидуально обрабатываемых асинхронных событий.
- **Когда использовать Subjects:** Используйте, когда вам нужен мультикаст или когда управление событиями должно контролироваться императивно, особенно хорошо для обработки событий или вещания, когда нескольким подписчикам нужен одновременный доступ к обновлениям данных.

И Observables, и Subjects являются мощными конструкциями в RxJS, каждый из которых выполняет уникальные и иногда перекрывающиеся роли в управлении потоками данных в реактивном программировании.