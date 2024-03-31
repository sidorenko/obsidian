#angular 
При подходе Reactive Forms для формы создается набор объектов `FormGroup` и `FormControl`. Сама форма и ее подсекции представляют класс `FormGroup`, а отдельные элементы ввода — класс `FormControl`.
```typescript
myForm: FormGroup = new FormGroup();
////
myForm: FormGroup = new FormGroup({
    userName: new FormControl(),
    userEmail: new FormControl(),
});
/// or
myForm: FormGroup = new FormGroup({
    userName: new FormControl('Tom', Validators.required),
    userEmail: new FormControl('', [
        Validators.required,
        Validators.pattern(
            '[a-zA-Z_]+@[a-zA-Z_]+?.[a-zA-Z]{2,3}'
        ),
    ]),
});
```