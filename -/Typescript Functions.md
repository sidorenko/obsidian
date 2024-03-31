#typescript 
```table-of-contents
```
#### Typing Functions

В TypeScript вы можете типизировать как параметры функции, так и возвращаемое значение функции. Это позволяет гарантировать, что функция возвращает ожидаемый тип значения и принимает правильные аргументы.

```typescript
function greet(name: string): string {
  return `Hello, ${name}`;
}

// Функция принимает один аргумент типа string и возвращает string.
```

#### Function Overloading

Перегрузка функций в TypeScript позволяет объявить несколько вариантов типов для функции, каждый из которых предоставляет различное поведение.

```typescript
function greeter(name: string): void;
function greeter(age: number): void;
function greeter(arg: string | number): void {
  if (typeof arg === 'string') {
    console.log(`Hello, ${arg}`);
  } else {
    console.log(`Age is ${arg}`);
  }
}

greeter('John');  // Hello, John
greeter(25);      // Age is 25
```

В приведенном выше примере функция `greeter` имеет перегруженные определения для сигнатур с разными типами аргументов. Компилятор TypeScript проверит каждую из перегрузок и использует первую совместимую определение при вызове функции. В реализации необходимо обрабатывать все возможные типы аргументов.