#angular 
Angular имеет два типа директив:
```table-of-contents
```
#### Структурные директивы (<font color="#f79646">Structural directives</font>)
Они меняют DOM, добавляя или убирая элементы. Они выглядят как обычные атрибуты, но с * перед именем. Например, `*ngFor`, `*ngIf`, `*ngSwitch`.

Пример:

```html
<div *ngIf="showDiv">Hello Angular</div>

<ul>
    <li *ngFor="let item of itemsList">{{ item }}</li>
</ul>
```
#### Атрибутивные директивы (<font color="#f79646">Attribute directives</font>)
Они меняют внешний вид или поведение элементов, компонентов, или других директив. Они выглядят как обычные атрибуты, не имеют * перед именем. Пример: `ngStyle`, `ngClass`.

Пример:

```html
<button [ngStyle]="{'color': active ? 'red' : 'green'}">My Button</button>
``` 

Ваша собственная директива может выглядеть так:

```typescript
@Directive({
   selector: '[myDirective]'
})
export class MyDirective {
//...
}
```
И тогда она применяется так:
```html
<div myDirective></div>