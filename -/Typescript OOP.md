#typescript 
В TypeScript, как и в других объектно-ориентированных языках, наследование дает возможность создавать новые классы, которые наследуют свойства и методы существующих классов. 

Основной синтаксис выглядит так:

```typescript
class BaseClass {
    // код класса
}

class SubClass extends BaseClass {
    // код подкласса
}
```

Ключевое слово `extends` указывает на то, что `SubClass` наследует от `BaseClass`. После этого `SubClass` имеет доступ ко всем свойствам и методам `BaseClass`.

Если вы хотите переопределить метод или свойство в подклассе, вы можете просто определить его заново:

```typescript
class BaseClass {
    greet() {
        console.log("Hello from BaseClass");
    }
}

class SubClass extends BaseClass {
    greet() {
        console.log("Hello from SubClass");
    }
}

let myClass = new SubClass();
myClass.greet();  // Выведет "Hello from SubClass"
```

Ключевое слово `super` можно использовать для обращения к методам и свойствам родительского класса:

```typescript
class BaseClass {
    greet() {
        console.log("Hello from BaseClass");
    }
}

class SubClass extends BaseClass {
    greet() {
        super.greet();  // вызывает метод greet родительского класса
        console.log("Hello from SubClass");
    }
}

let myClass = new SubClass();
myClass.greet();  
// Выведет "Hello from BaseClass"
// а затем "Hello from SubClass"
```
Для вызова конструктора родительского класса, также используется ключевое слово `super`:

```typescript
class BaseClass {
    constructor() {
        console.log("BaseClass constructor");
    }
}

class SubClass extends BaseClass {
    constructor() {
        super();
        console.log("SubClass constructor");
    }
}

let myClass = new SubClass();  
// Выведет "BaseClass constructor"
// а затем "SubClass constructor"
```