#typescript 
```table-of-contents
```
#### Type Guards / Narrowing

Type Guards в TypeScript позволяют сузить тип переменной в определенном блоке кода. Это может быть полезно при работе с объединенными типами, когда вам нужно быть увереным, что переменная имеет определенный тип.
Type Guards в TypeScript позволяют сузить тип переменной в определенном блоке кода. Это может быть полезно, когда вы работаете с объединенными типами или когда вы работаете с типами, которые могут быть следствием некоторых условий.

#### typeof

Оператор `typeof` может использоваться в guard выражении, чтобы сузить тип внутри блока if:

```typescript
let value: string | number;

if (typeof value === "string") {
  console.log(value.toUpperCase()); // Теперь TypeScript знает, что value - это строка
} else {
  console.log(value.toFixed(2)); // Теперь TypeScript знает, что value - это число
}
```

#### instanceof

Оператор `instanceof` используется для сужения типов при работе с классами:

```typescript
class Song {
  constructor(public title: string, public duration: string | number) {}
}

class Playlist {
  constructor(public name: string, public songs: Song[]) {}
}

function getItemDuration(item: Song | Playlist) {
  if (item instanceof Song) {
    return item.duration; // Теперь TypeScript знает, что item - это Song
  } else {
    return item.songs.length; // Теперь TypeScript знает, что item - это Playlist
  }
}
```

#### User-defined Type Guards

Вы можете определить свои собственные функции type guard, которые проверяют определенные условия и сужают типы:

```typescript
interface Fish {
  swim: () => void;
}

interface Bird {
  fly: () => void;
}

function isFish(pet: Fish | Bird): pet is Fish {
  return (pet as Fish).swim !== undefined;
}

let pet: Fish | Bird;

if (isFish(pet)) {
  pet.swim(); // Теперь TypeScript знает, что pet - это Fish
} else {
  pet.fly(); // Теперь TypeScript знает, что pet - это Bird
}
```

В примере выше, isFish является функцией типа guard, которая проверяет, может ли объект плавать. Если это так, то он сужает тип до Fish. Если не так, то он должен быть Bird.

#### instanceof

Оператор `instanceof` проверяет, является ли объект экземпляром конкретного класса.

```typescript
class Car {
  drive() {
    console.log('Driving...');
  }
}

let vehicle: Car;

if (vehicle instanceof Car) {
  vehicle.drive();  // Now TypeScript knows that vehicle is a Car
}
```

#### typeof

Оператор `typeof` используется для определения типа значения.

```typescript
let value: string | number;

if (typeof value === "string") {
  value.toUpperCase();  // Now TypeScript knows that value is a string
} else {
  value.toFixed(2);  // Now TypeScript knows that value is a number
}
```

#### Equality

Проверка на равенство также может работать как Type Guard.

```typescript
let value: string | string[];

if (value === "string") {
  value.toLowerCase();  // Now TypeScript knows that value is a string
} else {
  value.push("another string");  // Now TypeScript knows that value is a string[]
}
```

#### Truthiness

Булевы проверки могут сузить тип переменной с `null` или `undefined`.

```typescript
let value: string | null | undefined;

if (value) {
  value.toLowerCase();  // Now TypeScript knows that value is a string
}
```

#### Type Predicates

Type predicates – это функции, которые получают значение и проверяют, соответствует ли оно определенному типу.

```typescript
function isNumber(value: any): value is number {
  return typeof value === "number";
}

let value: string | number;

if (isNumber(value)) {
  value.toFixed(2);  // Now TypeScript knows that value is a number
}
```