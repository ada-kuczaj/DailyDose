
--- 
tags: [[Methods]]
date: 2024-07-05

---
Tablice JavaScript mają szeroką gamę wbudowanych metod, które ułatwiają manipulowanie danymi i pracę z nimi. Oto niektóre z najpopularniejszych i często używanych metod tablicowych w JavaScript:

# push()

Dodaje jeden lub więcej elementów na końcu tablicy i zwraca nową długość tablicy.
```js
et arr = [1, 2, 3];
arr.push(4); // arr teraz to [1, 2, 3, 4]
```

# pop()

Usuwa ostatni element z tablicy i zwraca ten element.
```js
let arr = [1, 2, 3];
let lastElement = arr.pop(); // arr teraz to [1, 2], lastElement to 3
```

# shift()

Usuwa pierwszy element z tablicy i zwraca ten element. Ta metoda zmienia długość tablicy.
```js
let arr = [1, 2, 3];
let firstElement = arr.shift(); // arr teraz to [2, 3], firstElement to 1
```

# unshift()

Dodaje jeden lub więcej elementów na początku tablicy i zwraca nową długość tablicy.
```js
let arr = [1, 2, 3];
arr.unshift(0); // arr teraz to [0, 1, 2, 3]
```

# map()

Tworzy nową tablicę wypełnioną wynikami wywołania podanej funkcji na każdym elemencie tablicy.
```js
let arr = [1, 2, 3];
let doubled = arr.map(num => num * 2); // doubled to [2, 4, 6]
```
# filter()

Tworzy nową tablicę z wszystkimi elementami, które przejdą test zaimplementowany przez podaną funkcję.
```js
let arr = [1, 2, 3, 4];
let even = arr.filter(num => num % 2 === 0); // even to [2, 4]
```

# reduce()

Wykonuje funkcję redukującą (którą podasz) na każdym elemencie tablicy, skutkując pojedynczą wartością wyjściową.
```js
let arr = [1, 2, 3, 4];
let sum = arr.reduce((accumulator, currentValue) => accumulator + currentValue, 0); // sum to 10
```

# forEach()

Wykonuje podaną funkcję raz na każdy element tablicy.
```js
let arr = [1, 2, 3];
arr.forEach(num => console.log(num)); // wypisuje 1, 2, 3
```

# find()

Zwraca wartość pierwszego elementu w tablicy, który spełnia podaną funkcję testującą. W przeciwnym razie zwraca undefined.
```js
let arr = [1, 2, 3, 4];
let found = arr.find(num => num > 2); // found to 3
```

# findIndex()

Zwraca indeks pierwszego elementu w tablicy, który spełnia podaną funkcję testującą. W przeciwnym razie zwraca -1.
```js
let arr = [1, 2, 3, 4];
let index = arr.findIndex(num => num > 2); // index to 2
```

# includes()

Określa, czy tablica zawiera określoną wartość wśród swoich wpisów, zwracając true lub false.
```js
let arr = [1, 2, 3];
let hasTwo = arr.includes(2); // hasTwo to true
```

# some()

Sprawdza, czy przynajmniej jeden element w tablicy przechodzi test zaimplementowany przez podaną funkcję. Zwraca wartość logiczną.
```js
let arr = [1, 2, 3];
let hasEven = arr.some(num => num % 2 === 0); // hasEven to true
```
j
# every()

Sprawdza, czy wszystkie elementy w tablicy przechodzą test zaimplementowany przez podaną funkcję. Zwraca wartość logiczną.
```js
let arr = [1, 2, 3];
let allEven = arr.every(num => num % 2 === 0); // allEven to false
```

# concat()

Łączy dwie lub więcej tablic. Ta metoda nie zmienia istniejących tablic, ale zamiast tego zwraca nową tablicę.
```js
let arr1 = [1, 2];
let arr2 = [3, 4];
let merged = arr1.concat(arr2); // merged to [1, 2, 3, 4]
```

# slice()

Zwraca płytką kopię części tablicy do nowego obiektu tablicy wybranego od początku do końca (koniec nie jest wliczony), gdzie początek i koniec reprezentują indeksy elementów w tej tablicy. Oryginalna tablica nie zostanie zmieniona.
```js
let arr = [1, 2, 3, 4];
let part = arr.slice(1, 3); // part to [2, 3]
```

# splice()

Zmienia zawartość tablicy poprzez usunięcie lub zastąpienie istniejących elementów i/lub dodanie nowych elementów w miejscu. Zwraca tablicę zawierającą usunięte elementy.
```js
let arr = [1, 2, 3, 4];
let removed = arr.splice(1, 2); // arr teraz to [1, 4], removed to [2, 3]
```

`array.splice(start, deleteCount, item1, item2, ..., itemN)`

Gdzie:

- `start` (obowiązkowy) - Indeks, od którego rozpoczyna się zmiana w tablicy. Jeśli jest ujemny, zaczyna liczyć od końca tablicy.
- `deleteCount` (opcjonalny) - Liczba elementów do usunięcia, zaczynając od indeksu `start`. Jeśli nie jest podana, wszystkie elementy od `start` do końca tablicy zostaną usunięte. Jeśli `deleteCount` jest 0, żadne elementy nie zostaną usunięte.
- `item1, item2, ..., itemN` (opcjonalne) - Elementy, które zostaną dodane do tablicy, zaczynając od indeksu `start`. Jeśli nie zostaną podane, metoda `splice()` usunie elementy bez dodawania nowych.
# join()

Łączy wszystkie elementy tablicy do stringa i zwraca ten string.
```js
let arr = [1, 2, 3];
let str = arr.join('-'); // str to '1-2-3'
```

# sort()

Sortuje elementy tablicy w miejscu i zwraca posortowaną tablicę.
```js
let arr = [3, 1, 4, 2];
arr.sort(); // arr teraz to [1, 2, 3, 4]
```

# reverse()

Odwraca tablicę w miejscu. Pierwszy element tablicy staje się ostatnim, a ostatni staje się pierwszym.
```js
let arr = [1, 2, 3];
arr.reverse(); // arr teraz to [3, 2, 1]

```

### References:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
---



