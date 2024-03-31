#flashcards-js 
#### Output
``` js
(function (x, f=()=>x){
    var x;
    var y = x;
    x= 6;
    console.log(x,y,f())
})(3)
```
?
ответ код
``` js
6 3 3
```

#### Яка різниця між декларацією функції (<span style="background:#fdbfff">function declaration</span>) та функціональним виразом (<span style="background:#fdbfff">function expression</span>)?

#### Що таке <span style="background:#fdbfff">анонімна</span> функція?

#### Що таке і для чого використовують <span style="background:#fdbfff">IIFE</span> (Immediately Invoked Function Expression)?

#### Що таке <span style="background:#fdbfff">hoisting</span>, як він працює для змінних і функцій?

#### Що таке замикання (<span style="background:#fdbfff">closure</span>) і які сценарії його використання?

#### Output
``` js
var f = function() {
	console.log(1);
}

var execute = function(f) {
	setTimeout(f, 1000);
}

execute(f); // что выведет в консоль и почему

f = function() {
	console.log(2);
}
```
?
``` js
ƒ () {
	console.log(2);
}
1
```


#### Що таке <span style="background:#fdbfff">рекурсія</span>?

#### Поясніть, що означає <span style="background:#fdbfff">currying</span>. Наведіть приклад використання на практиці.

#### Наведіть приклад функції з <span style="background:#fdbfff">мемоізацією</span>. Коли варто застосовувати цю техніку?

#### Що таке <span style="background:#fdbfff">чейнінг</span> функцій? Напишіть приклад з використанням цього підходу.

#### У чому різниця між <span style="background:#fdbfff">function</span> і <span style="background:#fdbfff">arrow function</span>? 

#### Output
``` js
const pluckDeep = key => obj => key.split('.').reduce((accum, key) => accum[key], obj)

const compose = (...fns) => res => fns.reduce((accum, next) => next(accum), res)

const unfold = (f, seed) => {
  const go = (f, seed, acc) => {
    const res = f(seed)
    return res ? go(f, res[1], acc.concat([res[0]])) : acc
  }
  return go(f, seed, [])
}
```