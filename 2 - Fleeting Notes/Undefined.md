
--- 
tags: [[Object]] 
date: 2024-07-09

---

> A variable that has not been assigned a value is of type `undefined`.

That means while `null` represents an empty value (but still a value), `undefined` represents the total absence of a value. 

`undefined` appears in different contexts.

- If a variable is declared without a value (initialization), it is `undefined`.
- If you try to access a value for a non-existing key in an object, you get `undefined`.
- If a function does not return a value, the result is `undefined`.
- If an argument is not passed to a function, it is `undefined`, unless that argument has a default value.

```javascript
let name;
console.log(name);
// => undefined
```

You can check whether a variable is undefined using the strict equality operator `===`.

```javascript
let name;

name === undefined;
// => true
```

### References:

https://exercism.org/tracks/javascript/exercises/amusement-park/edit

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined

---



