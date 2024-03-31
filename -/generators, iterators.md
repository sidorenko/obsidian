``` 
38.. Поясніть, що робить наведений код:

function * fn(num) {

for (let i = 0; i < num; i += 1) {

yield console.log(i);

}

}

const loop = fn(5);

loop.next();

loop.next();

```