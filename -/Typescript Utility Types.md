#typescript 
```table-of-contents
```
#### `Partial<Type>`

Генератор типа `Partial<Type>` создает новый тип, в котором все свойства `Type` являются необязательными.

```typescript
interface Todo {
  title: string;
  description: string;
}

const updateTodo: Partial<Todo> = {
  title: "Updated title",
}; // допустимо, т.к. все свойства Todo являются необязательными в Partial<Todo>
```

#### `Pick<Type, Keys>`

`Pick<Type, Keys>` создает новый тип, выбирая набор свойств `Keys` из `Type`.

```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

type TodoPreview = Pick<Todo, "title" | "completed">;

const todo: TodoPreview = {
  title: 'Clean room',
  completed: false,
};
```

#### `Omit<Type, Keys>`

`Omit<Type, Keys>` создает новый тип, удаляя набор свойств `Keys` из `Type`.

```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

type TodoInfo = Omit<Todo, 'completed'>;

const todoInfo: TodoInfo = {
  title: 'Pick up kids',
  description: 'Pick up kids from school at 2pm',
};
```

#### `Readonly<Type>`

`Readonly<Type>` создает новый тип, в котором все свойства `Type` являются только для чтения.

```typescript
interface Todo {
  title: string;
}

const todo: Readonly<Todo> = {
  title: "Delete inactive users",
};

todo.title = "Hello"; // ошибка: Index signature in type 'Readonly<Todo>' only permits reading
```

#### `Record<Keys, Type>`

`Record<Keys, Type>` создает объектный тип, который отображает тип `Keys` to `Type`. Все свойства этого типа будут типом `Type` и необязательными.

```typescript
interface PageInfo {
  title: string;
}

type Page = "home" | "about" | "contact";

const nav: Record<Page, PageInfo> = {
  about: { title: "about us" },
  contact: { title: "contact us" },
  home: { title: "home page" },
};
```

#### `Exclude<Type, ExcludedUnion>`

`Exclude<Type, ExcludedUnion>` исключает из `Type` значения, которые назначены `ExcludedUnion`.

```typescript
type T0 = Exclude<"a" | "b" | "c", "a">;  // "b" | "c"
```

#### `Extract<Type, Union>`

`Extract<Type, Union>` создает новый тип, извлекая из `Type` все значения, которые назначаются `Union`.

```typescript
type T1 = Extract<"a" | "b" | "c", "a" | "f">;  // "a"
```

#### `NonNullable<Type>`

`NonNullable<Type>` исключает `null` и `undefined` из `Type`.

```typescript
type T2 = NonNullable<string | number | undefined>;  // string | number
```

#### `Parameters<Type>`

`Parameters<Type>` создает новый тип из списка параметров функции `Type`.

```typescript
declare function f1(arg: { a: number, b: string }): void;
type T3 = Parameters<typeof f1>;  // [{ a: number, b: string }]
```

#### `ReturnType<Type>`

`ReturnType<Type>` создает новый тип из типа, возвращаемого функцией `Type`.

```typescript
declare function f1(): { a: number, b: string };
type T4 = ReturnType<typeof f1>;  // { a: number, b: string }
```

#### `InstanceType<Type>`

`InstanceType<Type>` создает новый тип из конструктора класса `Type`.

```typescript
class C {
  x = 0;
  y = 0;
}

type T5 = InstanceType<typeof C>;  // C
```

#### `Awaited<Type>`

`Awaited<Type>` непосредственно ожидает `Type` (если `Type` является объектом `Promise`, объявляет его типом разрешения).

```typescript
type X = Promise<string>;
type Y = Promise<{ field: number }>;

type A = Awaited<X>;  // string
type B = Awaited<Y>;  // { field: number }
```