
--- 
tags: [[JS]] [[Array methods]] 
date: 2024-07-08

---
Uwaga na metodę reverse()

**Problem**:

- Metoda `reverse()` działa bezpośrednio na oryginalnej tablicy, co powoduje, że zarówno `number`, jak i `reversedNumber` wskazują na tę samą odwróconą tablicę.
- W wyniku tego porównanie `number === reversedNumber` zawsze zwróci `true`, nawet jeśli liczba nie jest palindromem.

Kod poniżej jest zły:
```js
function luckyNumbers(number) {

    let reversedNumber = number.reverse();
    if (number === reversedNumber) {
        return true;
    } else {
        return false;
    }
}```


Kod poniżej jest dobry:
```js
function luckyNumber(value) {
  const number = String(value);
  let reversedNumber = '';
  for (let i = number.length - 1; i >= 0; i--) {
    reversedNumber += number[i];
  }
  return number === reversedNumber;
}
```


### References:


---



