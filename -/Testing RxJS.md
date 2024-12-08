#rxjs

Тестирование RXJS операторов может включать в себя проверку результатов трансформации, фильтрации или комбинации потоков данных. Для тестирования может быть использован пакет `rxjs/testing`, который предоставляет удобный способ тестирования временных интервалов и асинхронных операций с помощью виртуального времени и мраморных диаграмм.

### Пример: Тестирование с использованием `TestScheduler`

Допустим, мы хотим протестировать следующий `RxJS` код, который использует оператор `map` для умножения каждого значения на 10:

```javascript
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

const source$ = of(1, 2, 3).pipe(
  map(x => x * 10)
);
```

Теперь давайте напишем тест для этого потока:

```javascript
import { TestScheduler } from 'rxjs/testing';
import { of } from 'rxjs';
import { map } from 'rxjs/operators';

describe('RXJS Operator Test', () => {
  let testScheduler;

  beforeEach(() => {
    // Создаём TestScheduler с функцией сравнения двух значений
    testScheduler = new TestScheduler((actual, expected) => {
      expect(actual).toEqual(expected);
    });
  });

  it('should multiply by 10 each value', () => {
    testScheduler.run((helpers) => {
      const { cold, expectObservable } = helpers;
      // Создаём "холодный" observable с мраморной диаграммой
      const sourceMarble = 'a-b-c|';
      const sourceValues = { a: 1, b: 2, c: 3 };
      const expectedMarble = 'x-y-z|';
      const expectedValues = { x: 10, y: 20, z: 30 };

      // Используем map оператор
      const source$ = cold(sourceMarble, sourceValues).pipe(
        map(value => value * 10)
      );

      // Проверяем ожидаемые результаты
      expectObservable(source$).toBe(expectedMarble, expectedValues);
    });
  });
});
```

**Объяснение кода:**
- **TestScheduler**: Это специальный планировщик, который используется для проверки операторов RxJS. Он позволяет писать тесты с использованием "мраморных" диаграмм, где каждый символ представляет временную точку.
- **cold**: Функция для создания холодного Observable. `a-b-c|` означает, что Observable испускает значения 'a', 'b', 'c', затем завершается.
- **expectObservable**: Функция для проверки ожидаемого Observable. `x-y-z|` означает что мы ожидаем значения 'x', 'y', 'z', после чего Observable завершается.

### Заключение

Используя `TestScheduler` и мраморные диаграммы, можно написать чёткие и контролируемые тесты для RxJS операторов, проверяя изменения потоков данных и убеждаясь, что все асинхронные операции выполняются правильно. Этот подход снижает сложность тестирования асинхронных и временно-зависимых операций в RxJS.