#rxjs 
[project](https://stackblitz.com/edit/promise-vs-observable-example-kba756?file=src%2Fapp%2Fapp.component.ts)

#flashcards-rxjs

#### observables vs promises
?
можно разделить на характеристики по 4 критериям:
1. когда начинает работать
2. поддержка нескольких значений
3. операторы (фильтрация)
4. отписка
--------
<!--SR:!2023-11-29,1,230-->

<span style="background:#ff4d4f">промисы отрабатывают только один раз</span>, observable можно перезапускать <span style="background:#d4b106">множество</span> раз. 
То есть вместо того что бы запоминать конфиг, мы буквально создаем объект, описывающий запрос (до вызова subscribe/map запрос реальный не отправляется). Если у вас отвалилась сеть и мы хотим повторить запрос - достаточно еще раз вызвать метод объекта, а не создавать новый запрос. Банально удобнее, особенно в плане реюза кода (можно сделать на уровне сервиса перехватчик запросов, который бы хэндлил за нас такие ситуации).