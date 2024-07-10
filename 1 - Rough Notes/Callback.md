
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

### References:


---



