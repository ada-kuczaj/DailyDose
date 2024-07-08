
--- 
tags: [[JS]]
date: 2024-07-07

---
Tworzenie obiektu:

```js
const emptyObject = {}; 

const obj =  { 
	favoriteNumber: 42,
	greeting: 'Hello World',
	useGreeting: true,
	address: { 
	     street: 'Trincomalee Highway', 
	     city: 'Batticaloa', 
	}, 
	fruits: ['melon', 'papaya'], 
	addNumbers: function (a, b) { 
		 return a + b; 
	}, 
};
```

 short-hand notation:

```js
const obj = { 
'1keyStartsWithNumber': '...', 'key/with/slashes': '...', 
'key-with-dashes': '...', 
'key with spaces': '...', 
'#&()[]{}èä樹keyWithSpecialChars': '...', 
};
```

Pobieranie wartości z obiektu:

```js
const obj = { greeting: 'hello world' };

obj.greeting; 
// => hello world 

obj['greeting']; 
// => hello world 

// Bracket notation also works with variables.
const key = 'greeting'; 
obj[key]; 
// => hello world
```

Dodawanie oraz zmienianie wartości 

```js
const obj = { greeting: 'hello world' };

obj.greeting = 'Hi there!'; 
obj['greeting'] = 'Welcome.'; 

obj.newKey1 = 'new value 1'; 
obj['new key 2'] = 'new value 2'; 

const key = 'new key 3'; 
obj[key] = 'new value 3';
```

Usuwanie atrybutów:

```js
const obj = { 
	key1: 'value1', 
	key2: 'value2', 
};

delete obj.key1; 
delete obj['key2'];
```

Sprawdzanie czy właściwość obiektu istnieje:

```js
const obj = { greeting: 'hello world' }; 

obj.hasOwnProperty('greeting'); 
// => true 

obj.hasOwnProperty('age'); 
// => false
```

### Looping Through an Object

There is a special `for...in` loop to iterate over all keys of an object.

```js
const obj = { 
	name: 'Ali', 
	age: 65, }; 

for (let key in obj) { 
	console.log(key, obj[key]); 
} // name Ali 
// age 65
```

To avoid subtle errors, you should always assume the `for...in` loop visits the keys in an arbitrary order. Also, be aware that `for...in` includes [inherited keys](https://exercism.org/tracks/javascript/concepts/inheritance) in its iteration.


### References:

https://exercism.org/tracks/javascript/exercises/high-score-board/edit 
---



