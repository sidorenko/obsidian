#angular 
```table-of-contents
```
Это компоненты Angular, который управляет навигацией.
#### Router Outlets

Router Outlet - это директива, которую Angular предоставляет для создания мест, куда он может "включать" содержимое отдельных Route при смене маршрутов в приложении. Он выступает в роли "контейнера" для отображения содержимого маршрута.

```html
<router-outlet></router-outlet>
```
#### Router Links

Router Link - это директива, которую использует Angular Router для привязки кликабельных элементов к маршрутам, обеспечивая навигацию между различными компонентами приложения без перезагрузки страницы.

```html
<a routerLink="/path">Go to path</a>
```
#### Router Events

Router Events - события, которые Angular Router предоставляет для прослушивания различных этапов навигации. Это позволяет вам, например, показывать индикатор загрузки при переходе между маршрутами, отслеживать действия пользователя и так далее. Эти события включают NavigationStart, NavigationEnd, NavigationCancel и другие. 

Ниже приведен пример прослушивания событий роутера:

```typescript
import { Router, NavigationStart, NavigationEnd } from '@angular/router';

// ...

constructor(private router: Router) {
  router.events.subscribe(event => {
    if (event instanceof NavigationStart) {
      console.log('Navigation started');
      // можно взаимодействовать с изображением загрузки 
    } else if (event instanceof NavigationEnd) {
      console.log('Navigation ended');
      // можно скрыть изображение загрузки 
    }
  });
}
```
Они служат для управления навигацией и улучшения взаимодействия пользователя с вашим приложением.
