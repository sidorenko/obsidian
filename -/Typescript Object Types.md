#typescript 
```table-of-contents
```
#### Interface

Интерфейсы в TypeScript используются для определения контракта (формы) для сложных типов.

```typescript
interface IPoint {
  x: number;
  y: number;
}

function logPoint(point: IPoint) {
  console.log(`x: ${point.x}, y: ${point.y}`);
}
```

#### Type vs Interface
В TypeScript, `type` и `interface` используются для объявления новых типов. Они очень похожи, но есть некоторые различия в их использовании и поведении.

##### Interface
- Применяется в основном для описания формы объектов.
- Может быть реализован классом (класс может реализовать множество интерфейсов).
- Может расширять другой интерфейс (также может расширять несколько интерфейсов).
- Интерфейсы объединяются с одноименным интерфейсом.

```ts
interface Point {
  x: number;
  y: number;
}

class MyPoint implements Point{
  x = 10;
  y = 20;
}
```
##### Type
- Может представлять более разнообразный набор типов - примитивные, объединенные типы, пересечение типов, кортежи и т.д.
- Не может быть реализовано классом и не может расширять другой `type`. Однако вы можете использовать пересечение типов для комбинации типов.
- Не объединяются с одноименным типом.

```ts
type PointType = {
  x: number;
  y: number;
};

type D3Point = PointType & { z: number };
```

В зависимости от сценария, вы можете выбрать между `type` и `interface`, но для представления формы объектов и классов предпочтительней использовать `interface`.
#### Class

Классы в TypeScript не только предоставляют синтаксическое удобство, ориентированное на объекты, но также были расширены, чтобы включить такие возможности, как интерфейсы и модификаторы доступа.

```typescript
class Point {
  constructor(public x: number, public y: number) {}
}

let point = new Point(1, 2);
```

#### Enum

Enum в TypeScript позволяют давать понятные имена наборам числовых значений.

```typescript
enum Color {
  Red,
  Green,
  Blue
}

let color: Color = Color.Green;
```

#### Arrays 

Массивы в TypeScript могут быть определены двумя способами.

```typescript
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];
```

#### Tuples

Кортежи позволяют выражать массив, в котором известен тип фиксированного числа элементов, но типы не обязательно должны совпадать.

```typescript
let tuple: [string, number];
tuple = ["hello", 10]; // Ок
tuple = [10, "hello"]; // Ошибка
```