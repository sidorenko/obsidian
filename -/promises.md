#js

#### Розкажіть про послідовне і паралельне виконання асинхронних функцій. У чому різниця між Promise.all () і Promise.allSettled ()?

#### Що таке Promise? Назвіть порядок виконання then і catch у ланцюжку

``` js

Promise.resolve(10)

	.then(e => console.log(e)) // ??

		.then(e => Promise.resolve(e))

			.then(console.log) // ??

				.then(e => {

					if (!e) {
					
						throw 'Error caught';
					
					}
					
				})

				.catch(e => {

					console.log(e); // ??
					
					return new Error('New error');
				
				})

				.then(e => {
				
					console.log(e.message); // ??
				
				})

				.catch(e => {
				
					console.log(e.message); // ??
				
				});
```


30.Розкажіть про послідовне і паралельне виконання асинхронних функцій. У чому різниця між Promise.all () і Promise.allSettled ()?