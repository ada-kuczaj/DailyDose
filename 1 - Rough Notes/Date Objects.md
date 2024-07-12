
--- 
tags: [[JS Date]]
date: 2024-07-11

---

Obiekty JavaScript Date reprezentują pojedynczy moment w czasie w formacie niezależnym od platformy. Obiekty Date zawierają liczbę całkowitą reprezentującą milisekundy od północy na początku 1 stycznia 1970 roku czasu UTC (epoki).
### `epoch`
Pomiar czasu w ECMAScript jest analogiczny do pomiaru czasu w POSIX, w szczególności dzieli definicję w kategoriach proleptycznego kalendarza gregoriańskiego, epoki północy na początku 
`1 stycznia 1970 UTC` 
oraz rozliczania każdego dnia jako zawierającego dokładnie 86 400 sekund (każda z czego ma długość 1000 milisekund).

### `leap years` = lata przestępne

W proleptycznym kalendarzu gregoriańskim lata przestępne to dokładnie te lata, które są podzielne przez 4 i albo podzielne przez 400, albo niepodzielne przez 100.

400-letni cykl proleptycznego kalendarza gregoriańskiego zawiera 97 lat przestępnych.


### `maximum timestamp`
Maksymalny znacznik czasu reprezentowany przez obiekt Date jest nieco mniejszy niż maksymalna bezpieczna liczba całkowita (Number.MAX_SAFE_INTEGER, która wynosi 9 007 199 254 740 991). Obiekt Date może reprezentować maksymalnie ±8 640 000 000 000 000 milisekund lub ±100 000 000 (sto milionów) dni w stosunku do epoki. Jest to zakres od 20 kwietnia 271821 r. p.n.e. do 13 września 275760 r. n.e. Każda próba przedstawienia czasu spoza tego zakresu powoduje, że obiekt Date zawiera wartość znacznika czasu NaN, czyli „Nieprawidłową datę”.

### References:

https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-time-values-and-time-range rozdział 21.4 Date Objects

---



