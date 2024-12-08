
Давайте рассмотрим несколько конкретных примеров задач по Angular, которые могут столкнуться разработчики в своей повседневной работе, с подробными решениями.

### Задача 1: Создание кастомной директивы для подсветки текста

#### Write a directive that will take a color and apply that color as the background for the text of the element it is applied to.
``` typescript
import { Directive } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  
}


--------------------
<div [appHighlight]="'yellow'">Текст с желтым фоном</div>
```
**Задача**: Написать директиву, которая будет принимать цвет и применять этот цвет в качестве фона для текста элемента, к которому она применена.

 <span style="background:#ff4d4f">-----------------------------------Решение---------------------------------</span>:

1. Создайте файл директивы:

``` typescript
import { Directive, ElementRef, Input, OnChanges, SimpleChanges } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective implements OnChanges {
  @Input() appHighlight: string;

  constructor(private el: ElementRef) {}

  ngOnChanges(changes: SimpleChanges) {
    this.el.nativeElement.style.backgroundColor = this.appHighlight;
  }
}
```

2. Добавьте директиву в `declarations` массив модуля, где она будет использоваться.
3. Используйте директиву в шаблоне компонента:

``` html
<div [appHighlight]="'yellow'">Текст с желтым фоном</div>
```

**Объяснение**: Директива `HighlightDirective` принимает цвет через свойство `appHighlight` и применяет его как фон элемента. Класс `ElementRef` используется для доступа к DOM элементу.

### Задача 2: Создание сервиса для работы с данными

**Задача**: Реализовать сервис, который будет выполнять HTTP GET запрос для получения данных и предоставлять эти данные компонентам.

 <span style="background:#ff4d4f">-----------------------------------Решение---------------------------------</span>:

1. Создайте сервис:

typescript

```
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor(private http: HttpClient) {}

  fetchData(url: string): Observable<any> {
    return this.http.get(url);
  }
}
```

2. Внедрите сервис в компонент:

typescript

```
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-data-consumer',
  template: `<div *ngFor="let item of data">{{ item.name }}</div>`
})
export class DataConsumerComponent implements OnInit {
  data: any[];

  constructor(private dataService: DataService) {}

  ngOnInit() {
    this.dataService.fetchData('api/data').subscribe(
      data => this.data = data,
      error => console.error('An error occurred', error)
    );
  }
}
```

**Объяснение**: `DataService` использует `HttpClient` для выполнения GET запроса на указанный URL. Внедренный сервис в `DataConsumerComponent` получает данные и сохраняет их для отображения в шаблоне компонента.

### Задача 3: Использование Angular Forms для сбора пользовательских данных

**Задание**: Создать форму с двумя полями ввода для имени и возраста, и отображать данные в представлении после отправки формы.

 <span style="background:#ff4d4f">-----------------------------------Решение---------------------------------</span>:

1. Объявите форму в компоненте:

typescript

```
import { Component } from '@angular/core';
import { FormBuilder, FormGroup } from '@angular/forms';

@Component({
  selector: 'app-user-form',
  template: `
    <form [formGroup]="userForm" (ngSubmit)="onSubmit()">
      <input type="text" formControlName="name" placeholder="Name">
      <input type="number" formControlName="age" placeholder="Age">
      <button type="submit">Submit</button>
    </form>
    <p>Submitted: {{ userData | json }}</p>
  `,
})
export class UserFormComponent {
  userForm: FormGroup;
  userData: any = null;

  constructor(private fb: FormBuilder) {
    this.userForm = this.fb.group({
      name: [''],
      age: [null]
    });
  }

  onSubmit() {
    this.userData = this.userForm.value;
  }
}
```

**Объяснение**: В этом примере используются Reactive Forms. `FormBuilder` используется для создания формы `userForm` с двумя полями. Данные из полей ввода привязаны к свойствам формы, а при отправке формы данные сохраняются в `userData` и отображаются на странице.

Давайте рассмотрим несколько реальных примеров задач для разработки на Angular, оформленные в виде практических заданий с решениями.

### Задача 4: Создание Пользовательского Пайпа для Форматирования Даты

**Задание**: Создать Angular пайп, который преобразует стандартный формат даты в формат `DD-MM-YYYY`.

 <span style="background:#ff4d4f">-----------------------------------Решение---------------------------------</span>:

1. **Создание пайпа:**
    
    typescript
    
    ```
    import { Pipe, PipeTransform } from '@angular/core';
    import { DatePipe } from '@angular/common';
    
    @Pipe({
      name: 'customDate'
    })
    export class CustomDatePipe extends DatePipe implements PipeTransform {
      transform(value: any, args?: any): any {
        return super.transform(value, "dd-MM-yyyy");
      }
    }
    ```
    
2. **Регистрация пайпа в модуле:**
    
    typescript
    
    ```
    @NgModule({
      declarations: [CustomDatePipe],
      exports: [CustomDatePipe]
    })
    export class SharedModule {}
    ```
    
3. **Использование пайпа в компоненте:**
    
    html
    
    ```
    <p>{{ currentDate | customDate }}</p>
    ```
    

**Объяснение**: Создается пользовательский пайп `CustomDatePipe`, наследующийся от `DatePipe`, предоставляемого Angular. Пайп переопределяет метод `transform`, форматируя дату в указанный формат `DD-MM-YYYY`.

### Задача 5: Реализация Аутентификации с Использованием HTTP Interceptors
#### Implement an HTTP interceptor that will add an authentication header with a JWT token to every outgoing request if the user is authenticated.
``` typescript

	
    import { HttpEvent, HttpInterceptor, HttpHandler, HttpRequest } from '@angular/common/http';
    import { Observable } from 'rxjs';
    
    export class AuthInterceptor implements HttpInterceptor {
      intercept() {
        const authToken = localStorage.getItem('authToken');
      }
    }

----------------------------------------
@NgModule({
      
    })
    export class CoreModule {}
    
```
**Задание**: Реализовать HTTP interceptor, который будет добавлять заголовок аутентификации с токеном JWT к каждому исходящему запросу, если пользователь аутентифицирован.

 <span style="background:#ff4d4f">-----------------------------------Решение---------------------------------</span>:

1. **Создание интерцептора:**

    ``` typescript
    import { Injectable } from '@angular/core';
    import { HttpEvent, HttpInterceptor, HttpHandler, HttpRequest } from '@angular/common/http';
    import { Observable } from 'rxjs';
    
    @Injectable()
    export class AuthInterceptor implements HttpInterceptor {
      intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
        const authToken = localStorage.getItem('authToken');
        const authReq = req.clone({
          headers: req.headers.set('Authorization', `Bearer ${authToken}`)
        });
        return next.handle(authReq);
      }
    }
    ```

2. **Регистрация интерцептора в модуле:**

    ``` typescript
    @NgModule({
      providers: [
        { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true }
      ]
    })
    export class CoreModule {}
    ```


**Объяснение**: Интерцептор `AuthInterceptor` добавляет заголовок `Authorization` с токеном JWT к каждому исходящему HTTP запросу. Этот заголовок используется для аутентификации пользователя на сервере.

### Задача 6: Динамическое Создание Компонентов

**Задание**: Разработать сервис для динамического создания компонентов на основе данных, полученных от сервера.

**Решение**:

1. **Сервис для динамического создания компонентов:**
    
    typescript
    
    ```
    import { Injectable, ComponentFactoryResolver, ViewContainerRef } from '@angular/core';
    
    @Injectable({
      providedIn: 'root'
    })
    export class DynamicComponentService {
      constructor(private resolver: ComponentFactoryResolver) {}
    
      loadComponent(viewContainerRef: ViewContainerRef, component: any) {
        const componentFactory = this.resolver.resolveComponentFactory(component);
        viewContainerRef.clear();
        viewContainerRef.createComponent(componentFactory);
      }
    }
    ```
    
2. **Использование сервиса в компоненте:**
    
    typescript
    
    ```
    export class SomeComponent {
      @ViewChild('container', { read: ViewContainerRef }) container: ViewContainerRef;
    
      constructor(private dynamicComponentService: DynamicComponentService) {}
    
      loadDynamicComponent() {
        this.dynamicComponentService.loadComponent(this.container, SomeDynamicComponent);
      }
    }
    ```
    
    html
    
    ```
    <!-- Шаблон компонента -->
    <ng-template #container></ng-template>
    ```
    

**Объяснение**: Сервис `DynamicComponentService` использует `ComponentFactoryResolver` для создания и вставки компонентов в контейнер, указываемый в декораторе `@ViewChild`. Это позволяет динамически загружать различные компоненты на основе данных или событий.

Эти примеры задач показывают различные возможности Angular в практическом применении, охватывая работу с датами, безопасной передачей данных и гибкой загрузкой компонентов.