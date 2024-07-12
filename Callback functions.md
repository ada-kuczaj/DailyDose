
--- 
tags: [[JS Functions]] [[Callback]]
date: 2024-07-12

---
Callback functions are functions passed as arguments. This programming pattern creates a sequence of function calls in both synchronous and asynchronous programming. Writing a callback function is no different from writing a function; however, the callback function must match the signature defined by the calling function.

```js
const squareLength = 5; 

// Caller function takes a callback function
function applyToSquare(callback) { 
	return callback(squareLength); 
} 

// Callback must expect the possible argument from the calling function 
function areaOfSquare(number) { 
	return number * number; 
} 

applyToSquare(areaOfSquare); // => 25
```

You may also write callbacks as a function expression:

```js
applyToSquare(function squarePerimeter(side) { 
	return side * 4; 
});
```


![[Pasted image 20240712140244.png]]
![[Pasted image 20240712140402.png]]
### References:
https://exercism.org/tracks/javascript/exercises/fruit-picker/edit
https://www.youtube.com/watch?v=nlKJmAvZoxo

---



