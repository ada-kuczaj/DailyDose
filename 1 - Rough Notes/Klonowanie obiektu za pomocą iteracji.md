
--- 
tags: [[Object]] [[JS Object]]
date: 2024-07-10

---
Aby dodać elementy do nowego obiektu, gdzie klucze mają takie same nazwy jak w oryginalnym obiekcie, ale wartości są zwiększone, możesz skorzystać z pętli `for...in` lub metody `Object.keys()`.

#### Użycie pętli `for...in`:
```js
let originalObj = {
  a: 1,
  b: 2,
  c: 3
};

let newObj = {};

for (let key in originalObj) {
  if (originalObj.hasOwnProperty(key)) {
    newObj[key] = originalObj[key] + 1; // Zwiększamy wartość o 1
  }
}

console.log(newObj); // Wyświetli: { a: 2, b: 3, c: 4 }
```

#### Użycie `Object.keys()`:
```js
let originalObj = {
  a: 1,
  b: 2,
  c: 3
};

let newObj = {};

Object.keys(originalObj).forEach(key => {
  newObj[key] = originalObj[key] + 1; // Zwiększamy wartość o 1
});

console.log(newObj); // Wyświetli: { a: 2, b: 3, c: 4 }

```
### Wyjaśnienie:

1. **Pętla `for...in`**:    
    - `for (let key in originalObj) { ... }` przechodzi przez wszystkie enumerowalne właściwości obiektu `originalObj`.
    - `if (originalObj.hasOwnProperty(key)) { ... }` sprawdza, czy właściwość należy bezpośrednio do obiektu `originalObj`.

2. **Metoda `Object.keys()`**:    
    - `Object.keys(originalObj)` zwraca tablicę z kluczami obiektu `originalObj`.
    - `forEach` przechodzi przez każdy klucz w tej tablicy.

3. **Dodawanie do nowego obiektu**:    
    - `newObj[key] = originalObj[key] + 1` przypisuje do nowego obiektu `newObj` wartość zwiększoną o 1 dla każdego klucza z obiektu `originalObj`.

Te metody pozwalają na skopiowanie kluczy z oryginalnego obiektu do nowego obiektu z modyfikowanymi wartościami. Możesz dostosować operację zwiększania wartości do swoich potrzeb (np. zwiększanie o inną wartość, wykonywanie innych operacji na wartościach itp.).

### References:


---



