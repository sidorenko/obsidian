#angular 
Async Pipe в Angular используется для автоматической подписки и отписки от Observable или Promise в вашем шаблоне. Это позволяет управлять асинхронными операциями прямо из шаблона, без необходимости писать дополнительную логику в компоненте.

Вот пример использования async pipe с Observable:

```typescript
import { Component, OnInit } from '@angular/core';
import { Observable, interval } from 'rxjs';

@Component({
  selector: 'my-app',
  template: `<div>{{ counter$ | async }}</div>`
})
export class AppComponent implements OnInit {
  counter$: Observable<number>;

  ngOnInit() {
    this.counter$ = interval(1000); // emits a number every 1 second
  }
}
```

В этом примере async pipe автоматически подписывается на Observable `counter$` и обновляет значение в шаблоне при каждом новом значении. Когда компонент уничтожается, async pipe автоматически отписывается от Observable, предотвращая утечки памяти.

Аналогичным образом, async pipe можно использовать с Promise:

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<div>{{ promiseData | async }}</div>`
})
export class AppComponent {
  promiseData: Promise<string> = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Promise Resolved!"), 2000);
  });
}
```

Здесь async pipe автоматически обновляет шаблон, когда промис разрешается.

https://angular.io/api/common/AsyncPipe
https://blog.angular-university.io/angular-reactive-templates/

async pipe используется в темплейтах
сам отписывается


дуобно добавлять скелетон или статус загрузки данных
https://angular.io/api/common/AsyncPipe
https://medium.com/angular-in-depth/angular-show-loading-indicator-when-obs-async-is-not-yet-resolved-9d8e5497dd8

