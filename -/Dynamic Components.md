#angular 
Динамические компоненты создаются уже в скомпилированном приложении в момент его работы.

В Angular динамическая компиляция компонентов реализована через сервис [`ComponentFactoryResolver`](https://angular.io/api/core/ComponentFactoryResolver).

Вызов метода `clear()` у [`viewContainerRef`](https://angular.io/api/core/ViewContainerRef) очищает содержимое блока представления.

Метод `resolveComponentFactory()` сервиса [`ComponentFactoryResolver`](https://angular.io/api/core/ComponentFactoryResolver) принимает определение класса нужного динамического компонента и возвращает его экземпляр в виде ссылки типа [`ComponentRef`](https://angular.io/api/core/ComponentRef). Для добавления созданного экземпляра в шаблон необходимо передать его в качестве параметра методу `createComponent()` экземпляра класса [`ViewContainerRef`](https://angular.io/api/core/ViewContainerRef).

Метод `createComponent()` возвращает ссылку на созданный компонент, с помощью которой можно манипулировать значениями свойств компонента и вызывать его методы.

``` typescript
@Component({
    selector: 'books-list',
    templateUrl: './books-list.component.html',
})
export class AppComponent {
    @ViewChild('book') book;

    constructor(
        private componentFactoryResolver: ComponentFactoryResolver
    ) {}

    addBook() {
        this.book.viewContainerRef.clear();

        let bookItemComponent = this.componentFactoryResolver.resolveComponentFactory(
            BookItemComponent
        );
        let bookItemComponentRef = this.book.viewContainerRef.createComponent(
            bookItemComponent
        );
        (<BookItemComponent>(
            bookItemComponentRef.instance
        )).value = {
            title: 'Great Expectations',
            author: 'Charles Dickens',
        };
    }
}
```