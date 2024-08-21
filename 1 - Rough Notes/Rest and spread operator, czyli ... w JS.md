
--- 
tags: [[JS Operators]] [[Array destructuring]]
date: 2024-07-12

---
JavaScript has a built-in `...` operator that makes it easier to work with indefinite numbers of elements. Depending on the context, it's called either a _rest operator_ or _spread operator_.

### Rest elements

When `...` appears on the left-hand side of an assignment, those three dots are known as the `rest` operator. The three dots together with a variable name is called a rest element. It collects zero or more values, and stores them into a single array.
```js
const [a, b, ...everythingElse] = [0, 1, 1, 2, 3, 5, 8]; 

everythingElse; 
// => [1, 2, 3, 5, 8]
```

Note that in JavaScript, unlike some other languages, a `rest` element cannot have a trailing comma. It _must_ be the last element in a destructuring assignment.

### Spread elements

When `...` appears on the right-hand side of an assignment, it's known as the `spread` operator. It expands an array into a list of elements. Unlike the rest element, it can appear anywhere in an array literal expression, and there can be more than one.

```js
const oneToFive = [1, 2, 3, 4, 5]; 
const oneToTen = [...oneToFive, 6, 7, 8, 9, 10]; 

oneToTen; 
// => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

Spread operator można również używać na obiektach:

![[Pasted image 20240820140125.png]]


### References:

https://exercism.org/tracks/javascript/exercises/elyses-destructured-enchantments/edit
https://blog.alexdevero.com/javascript-spread-operator/
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/38345372#overview

---



