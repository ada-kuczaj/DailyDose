
--- 
tags: [[Currying]] 
date: 2024-07-09

---
Pipelining to technika programistyczna, w której funkcje są łączone w ciąg operacji, gdzie wyjście jednej funkcji staje się wejściem kolejnej. W kontekście programowania funkcjonalnego, curryng i pipelining są często używane razem, aby stworzyć czytelny i modularny kod.

```js
// Funkcje curried
const add = (x) => (y) => x + y;
const multiply = (x) => (y) => x * y;

// Pipeline
const pipeline = (value) => multiply(2)(add(3)(value));

// Użycie pipeline
const result = pipeline(5); // (5 + 3) * 2 = 16
console.log(result); // 16
```


### References:


---



