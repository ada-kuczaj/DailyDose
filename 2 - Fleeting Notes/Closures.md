
--- 
tags: [[JS]]
date: 2024-07-10

---

`Closures` to wzorzec programistyczny w JavaScript, który umożliwia użycie zmiennych z zewnętrznego zakresu leksykalnego wewnątrz zagnieżdżonego bloku kodu. 

```js
// Top-level declarations are global-scope 
const dozen = 12; 

{ 
// Braces create a new block-scope 
// Referencing the outer variable is a closure. 
const twoDozen = dozen * 2; 
} 

// Functions create a new function-scope and block-scope. 
// Referencing the outer variable here is a closure. 
function nDozen(n) { 
return dozen * n; 
}
```


### References:
https://exercism.org/tracks/javascript/exercises/coordinate-transformation/edit

---



