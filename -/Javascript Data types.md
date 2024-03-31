#javascript 
```table-of-contents
```

#### Prototypal Inheritance

Prototypal Inheritance является механизмом наследования в JavaScript и TypeScript, который основан на прототипах. Каждый объект имеет свойство `__proto__`, которое указывает на его прототип — объект, от которого он наследует свойства и методы.

```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

Car.prototype.start = function() {
  console.log("Car started");
}

let myCar = new Car("Toyota", "Corolla");
myCar.start(); // "Car started"
```

В примере выше, `myCar` изначально не имеет метод `start`, но объект может получить доступ к нему через свойство `__proto__`, потому что этот метод определен на прототипе `Car.prototype`.

TypeScript упрощает использование прототипного наследования посредством классов и ключевого слова `extends`.

```typescript
class Vehicle {
  constructor(public make:string, public model:string) {}

  start() {
    console.log("Vehicle started");
  }
}

class Car extends Vehicle {}

let myCar = new Car("Toyota", "Corolla");
myCar.start();
```

#### Object Prototype

В JavaScript и, следовательно, TypeScript, каждый объект имеет `prototype` (прототип). Когда JavaScript ищет свойство объекта и не находит его, он затем ищет в объекте `prototype`. Это создает цепочку прототипов, которая в конечном счете ведет к `Object.prototype`.

```typescript
let obj = { prop: "Hello, World!" };

console.log(obj.toString()); // "[object Ojbect]"
```

В коде выше, `.toString()` не является свойством объекта `obj`. Однако, так как `Object.prototype` находится в цепочке прототипов `obj`, мы можем получить доступ к методу `.toString()`.