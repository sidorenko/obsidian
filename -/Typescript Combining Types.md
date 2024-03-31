#typescript 
```table-of-contents
```
#### Union Types

Union Types используются для объединения нескольких типов в один. Синтаксис состоит в использовании вертикальной черты `|` между типами.

```typescript
let value: string | number;

value = 'Hello';  // Допустимо
value = 42;       // Допустимо
value = true;     // Ошибка: 'boolean' не может быть присвоен типу 'string | number'
```
  
#### Intersection Types

Intersection Types используются для комбинирования нескольких типов в один. В результате вы имеете тип, который обладает всеми свойствами всех объединенных типов. Для этого используется символ `&`.

```typescript
interface Part1 { a: number; }
interface Part2 { b: string; }

type Combined = Part1 & Part2;

let value: Combined = { a: 42, b: 'Hello' };  // Допустимо
```

#### Type Aliases

Type Aliases позволяют создавать новые имена для типов. Type Aliases полезны для создания "шаблонов" для сложных типов и для обеспечения лучшей читаемости кода.

```typescript
type StringOrNumber = string | number;
let value: StringOrNumber;  // Используем алиас вместо объединения типов
```

#### keyof operator

Оператор `keyof` в TypeScript представляет индексный тип — субсет `symbol | string | number`, представляющий все возможные ключи для объекта.

```typescript
interface Person {
  name: string;
  age: number;
}

type PersonKeys = keyof Person;  // "name" | "age"

function getPropertyValue(person: Person, key: PersonKeys): string | number {
  return person[key];
}

const person: Person = {name: 'John', age: 25};
console.log(getPropertyValue(person, 'name'));  // John
```