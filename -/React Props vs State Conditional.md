#reactjs
```table-of-contents
```
Сравнение `props` и `state` в React позволяет понять, в каком контексте и для каких целей следует использовать каждый из этих концептов:
#### Props
- Props (свойства) передаются от родительского компонента к дочернему. Они являются исходными данными, которые компонент получает при создании.
- Props являются неизменяемыми (read-only). Это означает, что компонент не может изменять свои props, он только получает их и может использовать.
- Если данные должны быть доступны в нескольких компонентах или должны быть переданы от родителя к ребенку, используйте props.
#### State 
    State (состояние) - это объект компонента, который отслеживает изменения в течение времени и который может быть обновлен.
    Когда состояние компонента изменяется, компонент перерисовывается, чтобы отразить новые данные.
    Если данные внутри компонента могут изменяться без вмешательства извне, то это состояние.
#### На основе Состояния и Props Контролируемые и Неконтролируемые компоненты
- Когда вы хотите, чтобы форма была управляемой React, и вы хотите использовать событие onChange и методы жизненного цикла или хуки на формах, используйте состояние (state).
- Когда форма работает без необходимости управлять ею через React, то есть только с использованием ссылок и DOM, используйте неконтролируемые компоненты.

В общем, способ выбора между использованием `props` или `state` сильно зависит от того, что вам нужно сделать. Важно понимать, что `props` и `state` не являются взаимоисключающими и могут использоваться вместе в одном и том же компоненте.