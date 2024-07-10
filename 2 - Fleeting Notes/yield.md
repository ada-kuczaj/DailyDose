
--- 
tags: [[JS Functions]]
date: 2024-07-10

---

`yield` to słowo kluczowe w języku JavaScript używane w funkcjach generatorów. Funkcja generatora jest specjalnym typem funkcji, która może wstrzymywać i wznawiać swoje wykonanie. Słowo kluczowe `yield` pozwala funkcji generatora zwrócić wartość w trakcie swojego działania, a następnie wznowić działanie od tego miejsca później.

```js
function* foo(index) {
  while (index < 2) {
    yield index;
    index++;
  }
}

const iterator = foo(0);

console.log(iterator.next().value);
// Expected output: 0

console.log(iterator.next().value);
// Expected output: 1
```
### References:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield
---



