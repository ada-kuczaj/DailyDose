
--- 
tags: [[JS Date]]
date: 2024-07-11

---
`Date.parse()` to metoda JavaScript, która analizuje reprezentację daty w formie łańcucha znaków i zwraca liczbę milisekund od 1 stycznia 1970 roku 00:00:00 UTC (znaną jako Unix Epoch). Jest to przydatne, gdy chcesz przekształcić datę w formie tekstu na obiekt `Date`.

Oto kilka przykładów użycia `Date.parse()`:

```js
// Przykład z pełnym formatem daty i czasu
let dateString = 'July 11, 2024 12:00:00';
let timestamp = Date.parse(dateString);
console.log(timestamp); // Wyświetla liczbę milisekund od 1 stycznia 1970 roku

// Tworzenie obiektu Date z analizowanego timestampu
let date = new Date(timestamp);
console.log(date.toString()); // Wyświetla "Thu Jul 11 2024 12:00:00 GMT+0000 (Coordinated Universal Time)"

// Przykład z różnymi formatami daty
let date1 = new Date(Date.parse('2024-07-11T12:00:00Z'));
console.log(date1.toString()); // Wyświetla "Thu Jul 11 2024 12:00:00 GMT+0000 (Coordinated Universal Time)"

let date2 = new Date(Date.parse('07/11/2024'));
console.log(date2.toString()); // Wyświetla "Thu Jul 11 2024 00:00:00 GMT+0000 (Coordinated Universal Time)"
```

Warto zauważyć, że `Date.parse()` akceptuje wiele różnych formatów daty. Poniżej przedstawiono kilka typowych formatów:

1. ISO 8601: `'2024-07-11T12:00:00Z'` (najbardziej popularny i uniwersalny)
2. Krótki format daty (miesiąc/dzień/rok): `'07/11/2024'`
3. Długi format daty: `'July 11, 2024 12:00:00'`



### References:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date

---



