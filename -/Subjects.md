 
<font color="#00b050">Subject</font> получает с момента подписки и <span style="background:#ff4d4f">каждый</span> некст. 
Для <font color="#00b050">AsyncSubject</font> важно <span style="background:#ff4d4f">complete</span> (только для него), так как каждый такой получает <span style="background:#ff4d4f">последнее</span> некст.
<font color="#00b050">ReplaySubject</font> принимает <span style="background:#ff4d4f">параметр</span> сколько некстов дать перед моментом подписки.
<font color="#00b050">BehaviorSubject</font> тоже имеет параметр <span style="background:#ff4d4f">инита</span>, то есть значения если не было некста, но кто-то подписался, если же был некст, а потом подписка, то <span style="background:#d4b106">прилетает предыдущий некст</span>.


Есть Observable и Subjects
<font color="#f79646">Subject()</font> зритель реагирует на каждое событие
<font color="#f79646">AsyncSubject()</font> уведомляет только о последнем событие
<font color="#f79646">BehaviorSubject(0)</font> уведомляет о последнем событии но имеет значение по умолчанию
<font color="#f79646">ReplaySubject(2)</font> дает знать о всех событиях, но мы можем для производительности брать только последние 2

<span style="background:#9254de">Subjects может быть преобразован в Observable .asObservable()</span>

https://medium.com/@kosmogradsky/subject-%D0%B2-rxjs-%D0%BA%D1%80%D0%B0%D1%82%D0%BA%D0%BE%D0%B5-%D0%B2%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5-c9099231be6d
------------
[Run online in Forefox](https://stackblitz.com/edit/rxjs-asyncsubject-zjng6m?file=index.ts)
login with github

``` js
console.clear();

console.log(`---------------------------------`);
console.log(`---Subject---`);

import { Subject } from 'rxjs';
const subject_test = new Subject();

subject_test.subscribe({next: (v) => console.log(`observer 1: ${v}`),});
subject_test.next('1');
subject_test.next('2');
subject_test.next('3');
subject_test.subscribe({next: (v) => console.warn(`observer 2: ${v}`),});
subject_test.next('Good Morning');
subject_test.next('4');
subject_test.complete();

//-   ---Subject---
//-   observer 1: 1
//-   observer 1: 2
//-   observer 1: 3
//-   observer 1: Good Morning
//-   observer 2: Good Morning
//-   observer 1: 4
//-   observer 2: 4
  

console.log(`---------------------------------`);
console.log(`---AsyncSubject---`);

import { AsyncSubject } from 'rxjs';
const sub = new AsyncSubject();

sub.subscribe({next: (v) => console.log(`observer 1: ${v}`),});
sub.next(1);
sub.next(2);
sub.next(3);
sub.subscribe({next: (v) => console.warn(`observer 2: ${v}`),});
sub.next(4);
sub.next(5);
sub.next(6);
sub.complete();

//-   ---AsyncSubject---
//-   observer 1: 6
//-   observer 2: 6


console.log(`---------------------------------`);
console.log(`---ReplaySubject---`);

import { ReplaySubject } from 'rxjs';
const subject = new ReplaySubject(3); // buffer 3 values for new subscribers

subject.subscribe({next: (v) => console.log(`observer 1: ${v}`),});
subject.next(1);
subject.next(2);
subject.next(3);
subject.next(4);
subject.subscribe({next: (v) => console.warn(`observer 2: ${v}`),});
subject.next(5);

//-   ---ReplaySubject---
//-   observer 1: 1
//-   observer 1: 2
//-   observer 1: 3
//-   observer 1: 4
//-   observer 2: 2
//-   observer 2: 3
//-   observer 2: 4
//-   observer 1: 5
//-   observer 2: 5


console.log(`---------------------------------`);
console.log(`---BehaviorSubject---`);

import { BehaviorSubject } from 'rxjs';
const subj = new BehaviorSubject(0); // 0 is the initial value

subj.subscribe({next: (v) => console.log(`observer 1: ${v}`),});
subj.next(1);
subj.next(2);
subj.subscribe({next: (v) => console.warn(`observer 2: ${v}`),});
subj.next(3);

//-   ---BehaviorSubject---
//-   observer 1: 0
//-   observer 1: 1
//-   observer 1: 2
//-   observer 2: 2
//-   observer 1: 3
//-   observer 2: 3
```
