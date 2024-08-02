
--- 
tags: [[JS Functions]] 
date: 2024-07-10

---
Callback to funkcja przekazywana jako argument do innej funkcji, która jest następnie wywoływana wewnątrz tej funkcji w celu wykonania pewnego zadania. Callbacki są często używane do operacji asynchronicznych, takich jak obsługa zdarzeń, komunikacja sieciowa czy operacje na bazie danych.

Przykład użycia callbacka:

```js
function fetchData(callback) {
  // symulacja pobierania danych
  setTimeout(function () {
    const data = "dane";
    callback(data);
  }, 1000);
}

function processData(data) {
  console.log("Otrzymane dane: " + data);
}

fetchData(processData);
```

W powyższym przykładzie, `fetchData` przyjmuje funkcję `callback` jako argument i wywołuje ją po pobraniu danych, przekazując te dane jako argument do callbacka `processData`.


Funkcje zwrotne (callback functions) są funkcjami przekazywanymi jako argumenty. Ten wzorzec programowania tworzy sekwencję wywołań funkcji zarówno w programowaniu synchronicznym, jak i asynchronicznym. Pisanie funkcji zwrotnej nie różni się od pisania zwykłej funkcji; jednak funkcja zwrotna musi pasować do sygnatury zdefiniowanej przez funkcję wywołującą.

```js
const sideLength = 5;

// Funkcja wywołująca przyjmuje funkcję zwrotną
function applySideLength(callback) {
  return callback(sideLength);
}

// Funkcja zwrotna musi oczekiwać możliwego argumentu od funkcji wywołującej
function areaOfSquare(side) {
  return side * side;
}

applySideLength(areaOfSquare); // => 25
```

Można również napisać funkcje zwrotne jako wyrażenie funkcyjne:

```js
applySideLength(function squarePerimeterLength(side) {
  return side * 4;
});
```

### References:

https://exercism.org/tracks/javascript/concepts/callbacks
---



