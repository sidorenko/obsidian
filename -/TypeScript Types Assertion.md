#typescript 
```table-of-contents
```
#### as const 
`as const` используется, чтобы привести выражение к read-only версии его самого, создавая таким образом `const`-снимок значений.

```typescript
let age = 10 as const; 

age = 20; // Ошибка: Не удается присвоить "20" для "age" из-за типа "readonly 10"
```
#### as type
Syntax `as type` используется для приведения типа. Он может быть использован для явного указания компилятору, что значение имеет указанный тип.

```typescript
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```
#### as any
`as any` используется для указания TypeScript, что любое значение может быть присвоено `any` типу.

```typescript
let value: number = "123" as any;

value = "Hello world"; // Допустимо
```
#### Non-null Assertion
Syntax `!` после любого выражения используется для принудительного удаления `null` и `undefined` из типов предшествующего выражения.

```typescript
// 'foo' имеет тип 'string | null'
let foo: string | null = "hello";

// Применяем Non-null Assertion
let bar: string = foo!; 

console.log(bar.substr(2)); // Используем bar как строка без проблем
```

В коде выше, `foo` имеет тип `string | null`, но TypeScript будет думать, что `foo` это только строка `string` в этом контексте во время выполнения.