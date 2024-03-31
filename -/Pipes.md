#angular 
```table-of-contents
```
Angular pipe, или просто **фильтр**, нужен для преобразования данных прямо в HTML-шаблоне. Например, отображение даты и времени в желаемом формате или задание формата вывода числового значения.
В Angular, пайпы используются для трансформации данных в шаблонах.
#### Встроенные пайпы
В Angular имеется ряд встроенных фильтров, но также предусмотрена возможность создания собственных.

Рассмотрим пример использования встроенного date pipe.

``` typescript
@Component({
    selector: 'date-pipe-example',
    template: `
        <p>
            Transformed date:
            {{ exampleDate | date: 'dd.MM.yyyy' }}
        </p>
    `,
})
export class DatePipeExampleComponent {
    exampleDate = new Date(2000, 12, 12);
}

```
Как видно из примера, наименование Angular pipe указывается после символа `|`, следующим за значением, которое необходимо преобразовать.

Существуют два типа пайпов: Pure и Impure.

Использование фильтров второго типа требуется в том случае, если фильтру передается массив или объект, изменение структуры или данных которых должно инициировать повторную обработку.
#### <font color="#f79646">Pure</font> (best)
(лучше для производительности) 
Pure пайпы <font color="#4bacc6">автоматически</font> обновляют вывод, когда изменяются входные значения. Это происходит на каждом цикле change detection Angular. Если входные данные не изменились, pure пайп не будет выполнен.

Пример pure pipe:

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'mypipe',
  pure: true
})
export class MyPipe implements PipeTransform {
  transform(value: any): any {
    // Transform your data here.
  }
}
```
#### <font color="#f79646">Impure</font> 
Impure pipes: Impure пайпы <font color="#4bacc6">выполняются на каждом</font> цикле обнаружения изменений, даже когда входные значения не изменяются. Применение impure пайпов может снизить производительность, и они должны использоваться с осторожностью.

Пример impure pipe:

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'mypipe',
  pure: false
})
export class MyPipe implements PipeTransform {
  transform(value: any): any {
    // Transform your data here.
  }
}
```

В большинстве случаев рекомендуется использовать pure пайпы, поскольку они эффективнее с точки зрения производительности. В некоторых специфических случаях, когда необходимо отслеживать изменения вне входных значений пайпа, можно использовать impure пайпы.