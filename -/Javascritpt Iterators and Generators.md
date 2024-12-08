#javascript 
```table-of-contents
```

В JavaScript итераторы и генераторы — это понятия, позволяющие работать с коллекциями данных, особенно при переборе элементов или выполнении последовательных операций. 

**Итераторы** в JavaScript — это объекты, которые предоставляют метод `next()`, возвращающий следующий элемент последовательности. С каждым вызовом метода `next()` итератор возвращает объект с двумя свойствами: `value` и `done`. Свойство `value` содержит значение текущего элемента коллекции, а `done` — булево значение, которое показывает, была ли коллекция полностью итерирована.

Пример работы с итератором:

```javascript
function makeRangeIterator(start = 0, end = Infinity, step = 1) {
    let nextIndex = start;
    let iterationCount = 0;

    const rangeIterator = {
       next: function() {
           let result;
           if (nextIndex < end) {
               result = { value: nextIndex, done: false };
               nextIndex += step;
               iterationCount++;
               return result;
           }
           return { value: iterationCount, done: true };
       }
    };
    return rangeIterator;
}

const it = makeRangeIterator(1, 10, 2);

let result = it.next();
while (!result.done) {
 console.log(result.value); // 1, 3, 5, 7, 9
 result = it.next();
}
```

**Генераторы** — это функции, которые можно выходить и снова входить, сохраняя при этом контекст их переменных между повторными входами. Генераторы обозначаются ключевым словом `function*` и используют оператор `yield` для передачи управления обратно коду, который вызвал `next()` на объекте генератора.

Пример работы с генератором:

```javascript
function* generateSequence(start, end, step) {
    for (let i = start; i <= end; i += step) {
        yield i;
    }
}

const gen = generateSequence(1, 10, 2);

let iterationResult = gen.next();
while (!iterationResult.done) {
 console.log(iterationResult.value); // 1, 3, 5, 7, 9
 iterationResult = gen.next();
}
```

Генераторы полезны, когда вам нужно генерировать последовательность значений «по требованию», не загружая всю последовательность в память. Они широко используются в JavaScript для управления асинхронным кодом и ленивой обработки данных.