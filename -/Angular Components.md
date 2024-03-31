#angular 
```table-of-contents
```
Properties, Inputs, Outputs, 

#### Examples of binding include
text interpolations
``` html
<h3>Current customer: {{ currentCustomer }}</h3>
```
property binding
``` html
<img alt="item" [src]="itemImageUrl">
```
attributes bindings
``` html
<!--  expression calculates colspan=2 -->
<tr><td [attr.colspan]="1 + 1">One-Two</td></tr>
```
class bindings
``` html
[class.sale]="onSale" // true/false
OR
[class]="classExpression" // "my-class-1 my-class-2 my-class-3"
```
style bindings
``` html
<nav [style.background-color]="expression"></nav>
<nav [style.backgroundColor]="expression"></nav>

[style.width.px]="width" OR [style.width]="width"
```
event binding
``` html
<button (click)="onSave()">Save</button>
<!--  ///// -->
<input (keydown.code.shiftleft.altleft.keyt)="onKeydown($event)" />
```
two-way binding
``` html
<app-sizer [(size)]="fontSizePx"></app-sizer>
```

#### ViewEncapsulation and ng-deep
В Angular стили компонента могут быть инкапсулированы в основной элемент компонента, чтобы они не влияли на остальную часть приложения.

Декоратор `Component` предоставляет опцию [`encapsulation`](https://angular.io/api/core/Component#encapsulation), которую можно использовать для управления тем, как инкапсуляция применяется _для каждого компонента_.
``` typescript
@Component({ 
	selector: 'app-no-encapsulation', 
	template: ` 
		<h2>None</h2> 
		<div class="none-message">No encapsulation</div> `, 
	styles: ['h2, .none-message { color: red; }'], 
	encapsulation: ViewEncapsulation.None, 
}) 
export class NoEncapsulationComponent {}
```

ViewEncapsulation.ShadowDom
ViewEncapsulation.Emulated
##### ViewEncapsulation.None 
любые стили, заданные для компонента, применяются глобально и могут повлиять на любой HTML-элемент, присутствующий в приложении.
##### ng-deep
<font color="#f79646">устаревшее</font>
Применение псевдокласса `::ng-deep` к любому CSS-правилу полностью отключает инкапсуляцию просмотра для этого правила. Любой стиль с примененным `::ng-deep` становится глобальным стилем.

#### Component Nesting (ng-content, ViewChild, ContentChild)
Использование шаблонных переменных открывает нам дополнительный способ взаимодействия между родительским и дочерним компонентом.
##### ViewChild 
Чтобы иметь возможность обращаться к методам и прочей функциональности дочернего компонента, надо использовать декоратор `ViewChild`.
``` typescript
export class AppComponent { 
	@ViewChild(ChildComponent) 
	private counterComponent: ChildComponent;
	 
	increment() { 
		this.counterComponent.increment(); 
	} 
	decrement() { 
		this.counterComponent.decrement(); 
	} 
}
```
##### ng-content and ContentChild
Кроме `ViewChild` для связи с шаблонными переменными мы можем применять другой декоратор — `ContentChild`.

для передачи контента с перента в дочерний компонент и отображения его в дочернем используется <font color="#f79646">ng-content</font>, это тег где будет приниматься шаблон с перента.

вот родительский компонент
``` typescript
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `
        <child-comp>
            <h3 #headerContent>
                Добро пожаловать {{ name }}!
            </h3>
        </child-comp>
    `,
})
export class AppComponent {
    name: string = 'Tom';
}
```
а тут дочерний принимает
``` typescript
import {
    Component,
    ContentChild,
    ElementRef,
} from '@angular/core';

@Component({
    selector: 'child-comp',
    template: `
        <ng-content></ng-content>
        <button (click)="change()">Изменить</button>
    `,
})
export class ChildComponent {
    @ContentChild('headerContent') header: ElementRef;

    change() {
        console.log(this.header);
        this.header.nativeElement.textContent =
            'Hell to world!';
    }
}
```
а для доступа к переменным которые передаются с родительского компонента как раз и нужен декоратор <font color="#f79646">ContentChild</font>

#### ng-template
— это основной элемент шаблонизации Angular, который позволяет вам рендерить HTML на основе условий или переменных.

Он используется в сочетании с структурными директивами Angular (`*ngIf`, `*ngFor`, `*ngSwitch` и прочие), которые реализуют логику внутри `ng-template`.

Пример использования `ng-template` с директивой `*ngIf`:

```html
<div *ngIf="isLoggedIn; else loggedOut">
  Welcome back, user!
</div>

<ng-template #loggedOut>
  <div>Please log in.</div>
</ng-template>
```

В примере выше вложенный шаблон `ng-template` отображается, когда `isLoggedIn` равно `false`.

Элемент `ng-template` является общим элементом каркаса шаблона и ничего не выводит сам по себе. Он рендерится только тогда, когда результат инициализируется директивой.

#check https://angdev.ru/angular/dynamic-component-loader/#_2

 
 [[Dynamic Components]]
