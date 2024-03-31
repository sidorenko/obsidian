#angular 
Для <font color="#9bbb59">манипуляций с DOM-элементами</font> в Angular используются так называемые абстракции, которые представлены классами 
<font color="#f79646">ElementRef,</font>
<font color="#f79646">TemplateRef, </font>
<font color="#f79646">ViewRef,</font>
<font color="#f79646">ComponentRef,</font>
<font color="#f79646">ViewContainerRef</font>

Сами абстракции представляют шаблон компонента или его отдельные части.

Для получения доступа к абстракциям используется механизм DOM-запросов, реализованных декораторами [`@ViewChild()`](https://angular.io/api/core/ViewChild) (возвращает одну ссылку) и [`@ViewChildren()`](https://angular.io/api/core/ViewChildren) (возвращает массив ссылок).