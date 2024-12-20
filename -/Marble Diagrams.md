#rxjs 

Мраморные диаграммы (Marble Diagrams) — это визуальное представление, широко используемое в реактивном программировании, особенно с библиотеками вроде RxJS, для концептуализации и иллюстрации работы потоков (Observables) и операторов во времени. Эти диаграммы помогают разработчикам лучше понять и спроектировать реактивные системы, показывая поведение и трансформацию потоков данных.

### Компоненты мраморной диаграммы

- **Временная шкала:** Горизонтальная линия, представляющая течение времени слева направо.
- **Мраморки (шарики):** Представляют собой значения, испускаемые Observable. Они обычно изображаются в виде кружков или символов (таких как числа или буквы), размещенных над временной шкалой.
- **Операторы:** Представлены между двумя временными шкалами, чтобы показать, как они преобразуют входящий Observable (выше) в исходящий Observable (ниже).
- **Завершение:** Точка на временной шкале, которая обозначает, когда Observable завершил свою работу. Обычно это показывается в виде вертикальной черты.
- **Ошибка:** Обычно обозначается символом "X" или другим символом, указывающим на наличие ошибки в потоке.

### Как читать мраморные диаграммы

Представьте, что каждый шарик или значение на диаграмме представляет собой данные, которые испускаются Observable в определенный момент времени. Операторы могут преобразовывать эти значения, комбинировать их или фильтровать, что отображается на второй временной шкале под первой.

#### Пример

Пусть есть оператор `filter`, который извлекает только четные числа:

```
--1--2--3--4--5--6--->
      filter(isEven)
--2--4--6--->
```

В этом примере:

- Входящий поток `--1--2--3--4--5--6--->` проходит через фильтр.
- Оператор `filter` убирает нечетные числа, и в результате на выходе получается `--2--4--6--->`.

Мраморные диаграммы очень полезны для визуализации реактивных операций и могут быть инструментом при проектировании и отладке реактивных приложений.