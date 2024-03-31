#typescript 
```table-of-contents
```
#### Mapped Types

Mapped Types в TypeScript позволяют создавать новые типы на основании старых, трансформируя в процессе каждое свойство в оригинальном типе.

```typescript
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
}

type Flags = {
  option1: boolean;
  option2: boolean;
}

let readOnlyFlags: Readonly<Flags> = {
  option1: true,
  option2: false
};
```
  
#### Conditional Types

Conditional Types позволяют выражать нетривиальные отношения между типами:

```typescript
type TypeName<T> =
  T extends string ? "string" :
  T extends number ? "number" :
  T extends boolean ? "boolean" :
  T extends undefined ? "undefined" :
  T extends Function ? "function" :
  "object";

type T0 = TypeName<string>;  // "string"
type T1 = TypeName<"a">;  // "string"
```

#### Literal Types

Literal Types позволяют создать тип, который принимает только определенное значение:

```typescript
type Direction = "north" | "south" | "east" | "west";

let sampleDirection: Direction;
sampleDirection = "north"; // Допустимо
sampleDirection = "northwest"; // Недопустимо
```

#### Template Literal Types

Template Literal Types в TypeScript позволяют использовать строки шаблонов в качестве типов, сочетая их с другими типами.

```typescript
type World = "world";

type Greeting = `hello ${World}`;  // "hello world"
```

#### Recursive Types

Recursive Types представляют собой типы, которые ссылаются на себя в своем определении.

```typescript
interface TreeNode<T> {
  value: T;
  left: TreeNode<T>;
  right: TreeNode<T>;
}
```

В примере выше `TreeNode<T>` это рекурсивный тип, поскольку его свойства `left` and `right` обратно ссылаются на `TreeNode<T>`.