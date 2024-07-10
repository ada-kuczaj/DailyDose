--- 
tags:  [[Arithmetic Operators]] 
date: 2024-07-04

---

```js
let username = '';  
let defaultName;  
  
if (username) {  
  defaultName = username;  
} else {  
  defaultName = 'Stranger';  
}  
  
console.log(defaultName); // Prints: Stranger
```

=

```js
let username = '';  
let defaultName = username || 'Stranger';  
  
console.log(defaultName); // Prints: Stranger
```




### References:
https://www.codecademy.com/courses/learn-javascript-fundamentals/lessons/control-flow/exercises/truthy-falsy-operators

---



