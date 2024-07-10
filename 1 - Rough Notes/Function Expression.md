
--- 
tags: [[JS Functions]]
date: 2024-07-10

---
Function expression to sposób na definiowanie funkcji w JavaScript jako część innego wyrażenia. W przeciwieństwie do deklaracji funkcji, która jest samodzielnym stwierdzeniem, wyrażenie funkcji może być użyte w przypisaniu, jako parametr funkcji (callback) lub jako wartość w obiekcie. Składnia jest taka sama jak w przypadku deklaracji funkcji, ale nazwa funkcji może być pominięta, co tworzy anonimową funkcję.

#### Przypisanie funkcji do zmiennej:
```js
const someFunction = function (param) { 
	// ... 
}; 
```

#### Funkcja jako parametr innej funkcji (callback):
```js
someOtherFunction(function (param) { 
	// ... 
}); 
```

#### Funkcja jako wartość w obiekcie:
```js
const obj = { someFunction: function (param) { 
	// ... 
	}, 
};
```


### References:
https://exercism.org/tracks/javascript/exercises/lasagna-master/edit

---



