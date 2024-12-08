#rxjs 
```table-of-contents
```
В RxJS операторы позволяют трансформировать, комбинировать, фильтровать и управлять потоками данных в Observable. Ниже представлены примеры различных категорий операторов: фильтрации, лимитирования скорости, трансформации и комбинации.

### 1. Операторы фильтрации (Filtering Operators)
Фильтруют значения в потоке данных, основываясь на некотором условии.

**Пример с `filter`:**
```javascript
import { of } from 'rxjs';
import { filter } from 'rxjs/operators';

const source$ = of(1, 2, 3, 4, 5);
const filtered$ = source$.pipe(
  filter(num => num % 2 === 0)
);

filtered$.subscribe(data => console.log(data)); // Выводит 2, 4
```

### 2. Операторы лимитирования скорости (Rate-limiting Operators)
Ограничивают скорость испускания значений.

**Пример с `throttleTime`:**
```javascript
import { fromEvent } from 'rxjs';
import { throttleTime } from 'rxjs/operators';

const clicks$ = fromEvent(document, 'click');
const throttledClicks$ = clicks$.pipe(
  throttleTime(1000)
);

throttledClicks$.subscribe(() => console.log('Click!'));
```
В этом примере события кликов будут обрабатываться не чаще одного раза в секунду.

### 3. Операторы трансформации (Transformation Operators)
Трансформируют элементы потока данных.

**Пример с `map` и `scan`:**
```javascript
import { of } from 'rxjs';
import { map, scan } from 'rxjs/operators';

const source$ = of(1, 2, 3, 4);
const transformed$ = source$.pipe(
  map(x => x * 10),
  scan((acc, value) => acc + value, 0)
);

transformed$.subscribe(data => console.log(data)); // Выводит 10, 30, 60, 100
```
`map` умножает каждое значение на 10, а `scan` суммирует текущее значение с аккумулированным.

### 4. Операторы комбинации (Combination Operators)
Комбинируют несколько потоков данных в один поток.

**Пример с `combineLatest`:**
```javascript
import { interval } from 'rxjs';
import { combineLatest, map } from 'rxjs/operators';

const interval1$ = interval(1000);
const interval2$ = interval(500);

const combined$ = combineLatest([interval1$, interval2$]).pipe(
  map(([val1, val2]) => `Interval1: ${val1}, Interval2: ${val2}`)
);

combined$.subscribe(data => console.log(data));
```
В этом примере значения из двух интервалов комбинируются, и каждый раз выводится последнее значение от каждого Observable.

Эти примеры демонстрируют мощь и гибкость операторов RxJS в обработке и комбинации потоков данных. Они позволяют создавать сложные асинхронные и реактивные программы с чистым и понятным кодом.