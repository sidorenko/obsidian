#rxjs 
[project](https://stackblitz.com/edit/promise-vs-observable-example-kba756?file=src%2Fapp%2Fapp.component.ts)

#flashcards-rxjs

#### Subjects vs observables
?
dddd
<!--SR:!2023-11-29,1,230-->




вы передаете объект с помощью метода next и complete. Вы вызываете next и complete в теле функции. В обоих случаях тело функции не выполняется до тех пор, пока вы не вызовете source.subscribe() или просто вызовете функцию напрямую как source() в другом примере. Это потому, что observables — это просто специализированные функции. 

------------------

[habr](https://habr.com/ru/post/568064/)

``` js
const observable = Rx.Observable.create((observer) => {
  let r = Math.random();
  console.log(r);
    observer.next(1);  
    observer.next(2);  
});  
// subscription 1  
observable.subscribe((data) => {  
  console.log(data);   
});  
// subscription 2  
observable.subscribe((data) => {  
   console.log(data);   
});  
```

``` js

/**
 * A simple object with a `next` and `complete` callback on it.
 */
interface Observer<T> {
  next: (value: T) => void;
  complete: () => void;
}
 
/**
 * A function that takes a simple object with callbacks
 * and does something them.
 */
const source = (subscriber: Observer<number>) => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  subscriber.complete();
};
 
// Usage
console.log('start');
source({
  next: console.log,
  complete: () => console.log('done'),
});
console.log('stop');

```

