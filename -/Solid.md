![[Pasted image 20240129143555.png]]
Это наиболее известный принцип разработки ПО. Solid — это аббревиатура от:  
  
**S) Single-responsibility principle /Принцип единственной ответственности**  
  
Его важность невозможно переоценить. Каждый объект, класс и метод должны отвечать только за что-то одно. Если ваш объект/класс/метод делает слишком много, вы получите спагетти-код. Вот пример:  
  

```
const saveTodo = async () => {
    try {
        response = await saveTodoApi(); 
        showSuccessPop('Success'); 
        window.location.href = '/successPage';
    } catch (error) { 
        showErrorPopup(`Error: ${error} `);
    }
}
```

  
Этот метод кажется безобидным, но на самом деле он делает слишком много:  
  

1. Сохраняет объект
2. Обрабатывает уведомление в UI
3. Выполняет навигацию

  
Еще один побочный эффект такого кода – проблемы с тестированием. Запутанный функционал тестировать сложно.  
  
**O) Open–closed principle / Принцип открытости-закрытости**  
  
Программные объекты должны быть открыты для расширения, но закрыты для модификации. Речь о том, что нельзя переопределять методы или классы, просто добавляя дополнительные функции по мере необходимости.  
  
Хороший способ решения этой проблемы – использование наследования. В JavaScript эта проблема решается с помощью композиции.  
  
Простое правило: если вы изменяете сущность, чтобы сделать ее расширяемой, вы впервые нарушили этот принцип.  
  
**L) Liskov substitution principle / Принцип подстановки Лисков**  
  
Этот принцип гласит, что объекты старших классов должны быть заменимы объектами подклассов, и приложение при такой замене должно работать так, как ожидается.  
  
**I) Interface segregation principle / Принцип разделения интерфейсов**  
  
Этот принцип был сформулирован Робертом Мартином, когда он консультировал Xerox, и он очевиден.  
  

> Объекты не должны зависеть от интерфейсов, которые они не используют

  
  
ПО должно разделяться на независимые части. Побочные эффекты необходимо сводить к минимуму, чтобы обеспечивать независимость.  
  
Убедитесь, что вы не заставляете объекты реализовывать методы, которые им никогда не понадобятся. Вот пример:  
  

```
interface Animal {
  eat: () => void;
  walk: () => void;
  fly: () => void;
  swim: () => void;
}
```

  
Не все животные могут fly, walk или swim, поэтому эти методы не должны быть частью интерфейса или должны быть необязательными.  
  
**D) Dependency inversion principle / Принцип инверсии зависимостей**  
  
Этот принцип невозможно переоценить. Мы должны полагаться на абстракции, а не на конкретные реализации. Компоненты ПО должны иметь низкую связность и высокую согласованность.  
  
Заботиться нужно не о том, как что-то устроено, а о том, как оно работает. Простой пример – использование дат в JavaScript. Вы можете написать для них свой слой абстракции. Тогда если у вас сменится источник получения дат, вам нужно будет внести изменения в одном месте, а не в тысяче.  
  
Иногда добавление этого уровня абстракции требует усилий, но в конечном итоге они окупаются.  
  
В качестве примера взгляните на [date-io](https://github.com/dmtrKovalenko/date-io), в этой библиотеке создан тот уровень абстракции, который позволяет вам использовать её с разными источниками дат.