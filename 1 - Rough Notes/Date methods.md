
--- 
tags: [[JS Date]]
date: 2024-07-11

---
### getTime()

The **`getTime()`** method of [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) instances returns the number of milliseconds for this date since the [epoch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date), which is defined as the midnight at the beginning of January 1, 1970, UTC.

```js
const moonLanding = new Date('July 20, 69 20:17:40 GMT+00:00');

// Milliseconds since Jan 1, 1970, 00:00:00.000 GMT
console.log(moonLanding.getTime());
// Expected output: -14182940000
```

#### Using getTime() for copying dates

Constructing a date object with the identical time value.

```js
// Since month is zero based, birthday will be January 10, 1995
const birthday = new Date(1994, 12, 10);
const copy = new Date();
copy.setTime(birthday.getTime());
```
### setTime()

```js
const theBigDay = new Date("1999-07-01");
const sameAsBigDay = new Date();
sameAsBigDay.setTime(theBigDay.getTime());
```

### valueOf()

The **`valueOf()`** method of [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) instances returns the number of milliseconds for this date since the [epoch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#the_epoch_timestamps_and_invalid_date), which is defined as the midnight at the beginning of January 1, 1970, UTC.

```js
const date1 = new Date(Date.UTC(96, 1, 2, 3, 4, 5));

console.log(date1.valueOf());
// Expected output: 823230245000

const date2 = new Date('02 Feb 1996 03:04:05 GMT');

console.log(date2.valueOf());
// Expected output: 823230245000
```

### Date.prototype\[@@toPrimitive]()

The **`[@@toPrimitive]()`** method of [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) instances returns a primitive value representing this date. It may either be a string or a number, depending on the hint given.

```js
date[Symbol.toPrimitive](hint)
//hint: string(default) or number

// Depending on timezone, your results will vary
const date = new Date('20 December 2019 14:48');

console.log(date[Symbol.toPrimitive]('string'));
// Expected output: "Fri Dec 20 2019 14:48:00 GMT+0530 (India Standard Time)"

console.log(date[Symbol.toPrimitive]('number'));
// Expected output: 1576833480000
```

### Date.now()

Static method returns the number of milliseconds elapsed since the epoch

```js
const start = Date.now();
doSomeLongRunningProcess();
console.log(`Time elapsed: ${Date.now() - start} ms`);
```

### Date.UTC()

Metoda statyczna Date.UTC() akceptuje parametry reprezentujące składniki daty i godziny podobnie jak konstruktor Date, ale traktuje je jako UTC. Zwraca liczbę milisekund od 1 stycznia 1970 r. o godzinie 00:00:00 UTC.

1. `Date.UTC()` uses universal time instead of the local time.
2. `Date.UTC()` returns a time value as a number instead of creating a [`Date`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) object.

```js
Date.UTC(year, monthIndex, day, hour, minute, second, millisecond)
```


```js
const utcDate1 = new Date(Date.UTC(96, 1, 2, 3, 4, 5));
const utcDate2 = new Date(Date.UTC(0, 0, 0, 0, 0, 0));

console.log(utcDate1.toUTCString());
// Expected output: "Fri, 02 Feb 1996 03:04:05 GMT"

console.log(utcDate2.toUTCString());
// Expected output: "Sun, 31 Dec 1899 00:00:00 GMT"
```
### Date.parse()

`Date.parse()` jest metodą statyczną, która analizuje łańcuch znaków reprezentujący datę i zwraca liczbę milisekund od epoki Unix (1 stycznia 1970, 00:00:00 UTC).

```js
const unixTimeZero = Date.parse('01 Jan 1970 00:00:00 GMT');
const javaScriptRelease = Date.parse('04 Dec 1995 00:12:00 GMT');

console.log(unixTimeZero);
// Expected output: 0

console.log(javaScriptRelease);
// Expected output: 818035920000
```

### Date.prototype.getTime()

 `getTime()` jest metodą instancji obiektu `Date`, która zwraca liczbę milisekund od epoki Unix do daty reprezentowanej przez obiekt `Date`.

```js
const moonLanding = new Date('July 20, 69 20:17:40 GMT+00:00');

// Milliseconds since Jan 1, 1970, 00:00:00.000 GMT
console.log(moonLanding.getTime());
// Expected output: -14182940000
```
### Podsumowanie różnic

1. **`Date.parse()`**:
    
    - **Typ metody:** Statyczna (wywoływana na `Date` jako klasie).
    - **Wejście:** Łańcuch znaków reprezentujący datę.
    - **Wyjście:** Liczba milisekund od epoki Unix.
    - **Przykład:** `Date.parse('2024-07-11T10:00:00Z')`
    - **Użycie Date.parse()**: Jeżeli masz datę w formie łańcucha znaków i chcesz ją przekonwertować na liczbę milisekund od epoki Unix
    
2. **`getTime()`**:
    
    - **Typ metody:** Instancji (wywoływana na obiekcie `Date`).
    - **Wejście:** Brak (wywoływana na instancji `Date`).
    - **Wyjście:** Liczba milisekund od epoki Unix do daty reprezentowanej przez obiekt `Date`.
    - **Przykład:** `new Date('2024-07-11T10:00:00Z').getTime()`
    - **Użycie getTime()**: Jeżeli masz obiekt Date i chcesz uzyskać liczbę milisekund od epoki Unix do tej daty

### Inne
```js
const date = new Date(Date.UTC(2015, 0, 24, 22, 0, 0)); // 24 stycznia 2015 roku, 22:00:00 UTC
const gs = gigasecond(date);

console.log(gs); // Wyświetli obiekt Date: 2046-10-02T23:46:40.000Z (w twojej lokalnej strefie czasowej)

console.log(gs.toISOString()); // Wyświetli: 2046-10-02T23:46:40.000Z (w formacie ISO 8601)

console.log(gs.getTime()); // Wyświetli liczbę milisekund od epoki Unix: 2461441600000

```




### References:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getTime
---



