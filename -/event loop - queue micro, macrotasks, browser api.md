
![[Eventloop.excalidraw]]


- цикл событий <span style="background:#fdbfff">Event Loop</span>
	- стек вызовов ====Call stack====
	- ====web api====
	- очередь задач ====Task queue====


> [!info] 
> Выполняется ввесть стек вызовов и только ПОСЛЕ всего стека микротаски

 > [!info] 
> После выполнения всех <span style="background:#fdbfff">микротасок</span> выполняется ОДНА макротаска


#flashcards-js 

#### Output
``` js
console.log('cl0'); // 1

setTimeout(() => { // mAcrotask
	console.log('mAcrotask1');
}, 0);

setTimeout(() => {
	Promise.resolve()
		.then(() => {
			console.log('mIcrotask1 in mAcrotask2');
		})
		.then(() => {
			console.log('mIcrotask2 in mAcrotask2');
		});
	console.log('mAcrotask2');
}, 0);

setTimeout(() => {
	Promise.resolve()
		.then(() => {
			console.log('mIcrotask1 in mAcrotask3');
		});
	console.log('mAcrotask3');
}, 0);

setTimeout(() => {
	console.log('mAcrotask4');
}, 0);

Promise.resolve()
	.then(() => { // mIcrotask
		console.log('mIcrotask1'); // 3
	});
	
console.log('cl1'); // 2
```
?
``` js
// cl0
// cl1
// mIcrotask1
// mAcrotask1
// mAcrotask2
// mIcrotask1 in mAcrotask2
// mIcrotask2 in mAcrotask2
// mAcrotask3
// mIcrotask1 in mAcrotask3
// mAcrotask4
```

> [!question]- Common Information
>#js 
>
> [Event loop](https://habr.com/ru/articles/762618/)