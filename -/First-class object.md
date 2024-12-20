#js 

Термин "объект первого класса" (англ. first-class object) в контексте программирования описывает элементы языка программирования, которые могут быть переданы как аргументы функции, возвращены из функции, модифицированы и присвоены переменным. Это означает, что такие элементы обрабатываются как полноправные "граждане" в языке и могут использоваться без ограничений соответствующими возможностями языка.

В JavaScript функции считаются объектами первого класса. Вот пример:

```javascript
// Объявление функции
function exampleFunction() {
  console.log("Привет, мир!");
}

// Присваивание функции переменной
const myFunction = exampleFunction;

// Передача функции как аргумента другой функции
function executeFunction(fn) {
  fn();
}

executeFunction(myFunction); // Выведет: "Привет, мир!"

// Возвращение функции из другой функции
function returnFunction() {
  return function() {
    console.log("Функция возвращена");
  };
}

const newFunction = returnFunction();
newFunction(); // Выведет: "Функция возвращена"

// Хранение функции в структуре данных
const functionArray = [myFunction, newFunction];
functionArray[0](); // Выведет: "Привет, мир!"
functionArray[1](); // Выведет: "Функция возвращена"
```

В этом примере функции JavaScript используются именно как объекты первого класса, потому что они могут быть присвоены переменным, переданы как аргументы или возвращены из других функций. Это свойство функций делает JavaScript гибким и выразительным языком, который обеспечивает полную поддержку функционального стиля программирования.