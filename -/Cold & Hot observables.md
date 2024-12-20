#rxjs 
```table-of-contents
```
**Cold Observable** — это поток, источник данных которого создается <font color="#f79646">внутри</font> конструктора Observable.

**Hot Observable** — это поток, источник данных которого создается <font color="#f79646">снаружи</font> конструктора Observable.

Observable(наблюдаемый) — это объект-передатчик потока данных, их существует 2 типа:
<font color="#f79646">Cold</font> — начинает потоковую передачу данных после вызова subscribe().
<font color="#f79646">Hot</font> — передается сразу после его создания, даже если ни один подписчик не заинтересован в данных. То есть все данные у всех одинаковы.

можно только <font color="#f79646">Cold to Hot</font>

https://habr.com/ru/companies/tinkoff/articles/729808/

В RxJS существуют два типа Observable: холодные (Cold) и горячие (Hot). Различие между ними заключается в их поведении и в том, как они делают доступными данные для подписчиков.

### Холодные Observable (Cold Observables)
**Описание:**
- Холодные Observable начинают генерировать данные только когда на них подписываются, и данные создаются заново для каждой подписки.
- Они не начинают испускать элементы до тех пор, пока не получат подписчика.
- Каждый подписчик имеет свой собственный набор данных – данный поток не делится между подписчиками.

**Пример:**
```javascript
import { Observable } from 'rxjs';

const coldObservable = new Observable(subscriber => {
  const producer = Math.random();
  console.log(`Producer: ${producer}`);
  subscriber.next(producer);
});

coldObservable.subscribe(value => console.log(`Subscriber A: ${value}`));
coldObservable.subscribe(value => console.log(`Subscriber B: ${value}`));
```
В этом примере каждый подписчик получает своё уникальное значение, потому что Observable создаёт новое значение для каждой подписки (генерирует случайное число), что типично для холодных Observable.

### Горячие Observable (Hot Observables)
**Описание:**
- Горячие Observable начинают генерировать данные независимо от подписок, и они могут делать это до момента подписки.
- Все подписчики разделяют один и тот же источник данных и получают значения, испускаемые после их подписки.
- Примеры горячих Observable: события DOM, состояние веб-сокета.

**Пример:**
```javascript
import { fromEvent } from 'rxjs';

const button = document.createElement('button');
button.textContent = 'Click me';
document.body.appendChild(button);

const hotObservable = fromEvent(button, 'click');

hotObservable.subscribe(event => console.log(`Subscriber A: event time ${event.timeStamp}`));
setTimeout(() => {
  hotObservable.subscribe(event => console.log(`Subscriber B: event time ${event.timeStamp}`));
}, 5000);
```
В этом случае оба подписчика подписываются на один и тот же источник события (клики по кнопке). Второй подписчик подключается через 5 секунд и начнёт получать данные только после своей подписки. Оба подписчика получают данные, испущенные после их подписки, и делят один поток событий.

### Заключение
Выбор между холодными и горячими Observable зависит от сценария использования:
- **Холодные Observable** идеально подходят когда каждый подписчик должен получить данные с начала или когда нужно гарантировать, что данные не будут потеряны или пропущены.
- **Горячие Observable** лучше использовать для широковещательных уведомлений или когда данные поступают из внешних источников, которые не зависят от подписчиков (например, тикеры времени, события пользовательского интерфейса).

Понимание этих концепций поможет в оптимизации потоков данных в вашем приложении и предотвратит возможные ошибки управления данными.