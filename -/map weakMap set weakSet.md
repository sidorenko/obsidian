#javascript 
```table-of-contents
```
## Map
<font color="#f79646">Map</font>: Это объект в JavaScript, который можно использовать для хранения пар <span style="background:#9254de">"ключ-значение"</span>. <span style="background:#d4b106">В Map можно использовать объекты, а не только строки и символы, в качестве ключей</span>. Это уникальное свойство Map делает его решением для многих проблем, которые не могут быть решены с помощью обычных объектов.

```js
let map = new Map();

map.set('name', 'John');
map.set('age', 30);

console.log(map.get('name')); // John
console.log(map.get('age')); // 30
```

## WeakMap
<font color="#f79646">WeakMap</font>: это специальный тип Map, который не предотвращает сборку мусора, когда на объект есть ссылка из WeakMap. WeakMap <span style="background:#d4b106">принимает только объекты</span> и не принимает примитивные значения как ключи.

```js
let weakMap = new WeakMap();
let obj = {};

weakMap.set(obj, 'John');
console.log(weakMap.get(obj)); // John

obj = null; 
console.log(weakMap.get(obj)); // undefined
```

## Set
<font color="#f79646">Set</font>: Это объект в JavaScript, который позволяет хранить <span style="background:#d4b106">уникальные элементы </span>любого типа, будь то примитивные значения или сами объекты.

```js
let set = new Set();

set.add(1);
set.add(2);
set.add(3);
set.add(1); // будет проигнорировано, так как 1 уже есть в наборе

console.log(set); // Set { 1, 2, 3 }
```

## WeakSet
<font color="#f79646">WeakSet</font>: Этот тип данных похож на Set, но его <span style="background:#d4b106">элементы могут быть только объекты и ссылки</span> на эти объекты слабые - то есть, если все сильные ссылки на объект были удалены, объект собирается сборщиком мусора даже если он содержится в WeakSet.

```js
let weakSet = new WeakSet();
let obj = {};
let obj2 = {};

weakSet.add(obj);
weakSet.add(obj2);

console.log(weakSet.has(obj)); // true

obj = null; 
console.log(weakSet.has(obj)); // false
```