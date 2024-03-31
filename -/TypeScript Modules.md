#typescript 
```table-of-contents
```
#### Namespaces

Namespaces используются в TypeScript для организации большого количества кода в группах. Они предоставляют модульность внутри единого файла TypeScript.
``` Typescript
namespace MyMath {
 const PI = 3.14;

 export function calculateCircumference(diameter: number) {
     return diameter * PI;
 }
}

console.log(MyMath.calculateCircumference(3));
```

#### Ambient Modules

Ambient Modules используются, когда вы хотите включить JavaScript-библиотеки в TypeScript- проект. Эти библиотеки требуют определения типа для поддержания проверки типов TypeScript. Вы можете написать свои собственные определения типов или использовать объявления типов от DefinitelyTyped (сообщество, которое публикует определения типов для JavaScript-библиотек).

``` Typescript
declare module "lodash" {
 export function chunk(array: any, size: number): any[][];
}
```

#### External Modules
External Modules в TypeScript связаны с кодом JavaScript, организованным в модульной структуре и использованием импорта и экспорта. В контексте TypeScript «внешний» означает «внешний по отношению к глобальной области видимости».

``` Typescript
// math.ts
export function add(x: number, y: number) {
  return x + y;
}

// main.ts
import { add } from './math';
console.log(add(2, 3));  // 5
```
#### Namespace Augmentation

Namespace Augmentation позволяет расширить существующие объявления в пространстве имен с дополнительными элементами. Это весьма полезно, когда вы хотите добавить свои собственные функции в существующую библиотеку.

```typescript
// Оригинальное пространство имен
namespace StringValidation {
  export function isText(text: string): boolean {
    return text.length > 0;
  }
}

// Дополнительная функция добавленная на этапе расширения
namespace StringValidation {
  export function hasNumbers(text: string): boolean {
    const numberRegexp = /[0-9]/;
    return numberRegexp.test(text);
  }
}
```

#### Global Augmentation

Global Augmentation позволяет добавить новые свойства в существующие глобальные объекты в JavaScript таких как `String`, `Number`, `Array` и так далее.

Например:

```typescript
interface String {
  prependHello(): string;
}

String.prototype.prependHello = function(): string {
  return `Hello, ${this}`;
};

console.log("World!".prependHello()); // Выведет: "Hello, World!"
```

В этом примере, мы расширяем встроенный тип `String` в JavaScript, добавляя новый метод `prependHello`.