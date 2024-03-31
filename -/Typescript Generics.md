#typescript 
```table-of-contents
```
#### Generic Types

Generic, или общие типы в TypeScript позволяют создавать функции, классы и интерфейсы, которые могут работать с несколькими типами, а не только с одним. Они обеспечивают способ создания "параметризованных" типов.

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("myString");  // тип аргумента явно указан
let output = identity("myString");  // тип аргумента выводится автоматически
```

В данном примере, `T` – это параметр типа, который определяет тип аргумента и возвращаемого значения функции `identity`.

#### Generic Constraints

В некоторых случаях вы можете захотеть ограничить возможные типы, используемые с обобщениями. Этого можно достичь с помощью ограничений на обобщения (generic constraints).

```typescript
interface Lengthwise {
  length: number;
}

function loggingIdentity<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);  // Теперь мы знаем, что у arg есть свойство .length, поэтому нет ошибки
  return arg;
}

loggingIdentity(3);  // Ошибка, число не имеет свойства .length
loggingIdentity({length: 10, value: 3});  // Допустимо, объект имеет свойство .length
```

Здесь `Lengthwise` – это интерфейс, который служит ограничением на параметр `T`. Он гарантирует, что любой тип, используемый вместо `T`, будет иметь свойство `length`.