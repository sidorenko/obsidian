#typescript 
```table-of-contents
```
Decorators (Декораторы) — это специальный вид объявления, который может быть прикреплен к объявлениям классов, методам, аксессорам, свойствам или параметрам. 

Они используются для модификации поведения классов, методов и свойств. Декораторы применяются путем размещения `@` перед декоратором, который непосредственно следует за декорируемым элементом:

```typescript
class MyClass {
  @log
  myMethod(arg: string) { }
}

// Пример декоратора метода
// log используется как @log внутри класса MyClass
function log(target: Object, key: string, descriptor: TypedPropertyDescriptor<any>): any {
  let originalMethod = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.log(`Arguments: ${args}`);
    let result = originalMethod.apply(this, args);
    console.log(`Result: ${result}`);
    return result;
  }
  return descriptor;
}
```

В этом примере, мы используем декоратор `@log` для метода `myMethod`. Каждый раз, когда `myMethod` вызывается, декоратор `log` логирует аргументы и результат метода.

Обратите внимание, что для использования декораторов в вашем TypeScript коде, вы должны включить `"experimentalDecorators": true` в вашем tsconfig.json файле, так как декораторы являются экспериментальной функцией в TypeScript.

Декораторы могут быть очень мощными для расширения и модификации поведения классов и методов без изменения исходного кода.