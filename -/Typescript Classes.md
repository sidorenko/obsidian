#typescript 
```table-of-contents
```
#### Constructor Params
В TypeScript, параметры конструктора могут быть переданы непосредственно в конструктор класса при создании нового экземпляра этого класса. Эти параметры могут быть определены с помощью модификаторов доступа для упрощения кода:

```typescript
class MyClass {
  constructor(private param1: number, public param2: string) {}
}
```

#### Constructor Overloading
TypeScript не поддерживает перегрузку конструктора напрямую. Однако с использованием необязательных параметров и разных типов параметров можно имитировать перегрузку конструктора:

```typescript
class MyClass {
  constructor(param?: number | string) {
    if (typeof param === 'number') {
      console.log("Constructor with number param");
    } else if (typeof param === 'string') {
      console.log("Constructor with string param");
    } else {
      console.log("Constructor with no param");
    }
  }
}
```

#### Access Modifiers
Access Modifiers в TypeScript определяют, где свойства и методы класса могут быть доступны. Три ключевых модификатора доступа: `public` (доступно везде), `private` (доступно только внутри класса) и `protected` (доступно внутри класса и его подклассов).

#### Abstract Classes
Абстрактные классы служат базой для других классов. Они не могут быть инстанциированы напрямую, а используются для создания новых классов через наследование.

```typescript
abstract class MyBaseClass {
  abstract myMethod(): void; 
}

class MyClass extends MyBaseClass {
  myMethod() {
    console.log("Abstract method implementation");
  }
}
```

#### Inheritance vs Polymorphism
Наследование в объектно-ориентированном программировании относится к способности класса наследовать свойства и методы от базового класса. 

Полиморфизм - это способность объектов различных типов интерпретировать одни и те же команды по-разному.

В контексте объектно-ориентированного программирования и TypeScript:

##### Наследование (Inheritance)
Наследование относится к способности одного класса принимать свойства и методы другого класса. В этом случае один класс становится родительским (или "базовым") классом, а другой - производным (или "подклассом").

Это особенно полезно, когда вы хотите обобщить общие свойства и методы в родительском классе, а затем специализировать или расширять эти свойства и поведение в подклассах.

Пример на TypeScript:

```typescript
class Animal {
  eat() {
    console.log("Animal is eating");
  }
}

class Cat extends Animal {
  meow() {
    console.log("Meow");
  }
}

const myCat = new Cat();
myCat.eat(); // Animal is eating
myCat.meow(); // Meow
```

В этом коде, класс `Cat` наследуется от класса `Animal`, что позволяет `Cat` использовать метод `eat` родительского класса.

##### Полиморфизм (Polymorphism)
Полиморфизм в объектно-ориентированном программировании это способность объектов разных типов реагировать на одни и те же вызовы различными способами. Это часто реализуется с помощью переопределения методов в классах-наследниках.

Пример полиморфизма в TypeScript:

```typescript
class Animal {
  makeSound() {
    console.log("Generic animal sound");
  }
}

class Cat extends Animal {
  makeSound() {
    console.log("Meow");
  }
}

class Dog extends Animal {
  makeSound() {
    console.log("Woof");
  }
}

let myAnimal: Animal;

myAnimal = new Cat();
myAnimal.makeSound(); // Meow

myAnimal = new Dog();
myAnimal.makeSound(); // Woof
```

В этом коде `Dog` и `Cat` классы переопределяют `makeSound` метод базового класса `Animal`. При вызове `makeSound`, объект вызывает метод соответствующий его фактическому типу, даже если вызов выполняется через ссылку типа `Animal`. Это и есть полиморфизм.

#### Method Overriding
Переопределение методов, это функциональность, которая позволяет подклассам изменять реализацию метода, унаследованного от базового класса.

```typescript
class MyBaseClass {
  myMethod() {
    console.log("Base method");
  }
}

class MyClass extends MyBaseClass {
  myMethod() {
    console.log("Overridden method");
  }
}
```