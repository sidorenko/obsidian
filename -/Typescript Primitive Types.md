#typescript 
```table-of-contents
```
#### boolean

`boolean` - это простой тип данных, который используется для представления истины или лжи.

```typescript
let isDone: boolean = false;
```

#### number

`number` - это числовой тип данных. В TypeScript, как и в JavaScript, все числа являются числами с плавающей точкой.

```typescript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

#### string

`string` используется для работы с текстовыми данными или строками.

```typescript
let color: string = "blue";
color = 'red';
```

#### undefined

`undefined` - это значение, которое присваивается неинициализированным переменным.

```typescript
let u: undefined = undefined;
```

#### null

`null` - это значение, которое обозначает отсутствие значения или отсутствующий объект. 

```typescript
let n: null = null;
```

#### void 

`void` используется в качестве возвращаемого типа функций, которые не возвращают значение.

```typescript
function warnUser(): void {
    console.log("This is my warning!");
}
```

Обратите внимание, что `null` и `undefined` допустимы для всех этих типов данных. Тем не менее, при использовании флага `"strictNullChecks"` в вашем файле tsconfig.json, `null` и `undefined` присваиваются только самим себе и `void` для `undefined` только.