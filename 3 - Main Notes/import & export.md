--- 
tags: [[React]]
date: 2024-08-19

---
### <span style="color: #d11141;">Różnice w składni:</span>

#### I SPOSÓB `let nazwaZmiennej` (więcej wartości)

plik app.js
```js
import {apiKey,abc as content} from './util.js';
```
Można przypisywać aliasy za pomocą `as` keyword.

plik util.js
```js
export let apiKey = "afgadfhahf";
export let abc = "abc";// możesz eksportować dowolną ilość zmiennych tym sposobem
```


#### II SPOSÓB `default` (jedna wartość)

plik app.js
```js
import apiKey from './util.js'; //tu przypisujemy nazwę zmiennej dopiero 
```

plik util.js
```js
export default "afgadfhahf"; //tylko jedna wartość defaultowa na plik
```

Tutaj nie tworzymy zmiennej i nie przypisujemy jej nazwy. Tylko eksportujemy wartość. Wtedy wartość staje się domyślną rzeczą eksportowaną z pliku, dlatego możemy jej użyć tylko raz.


> [!IMPORTANT] UWAGA
>UWAGA! Można też mieszać składnię `default` i `let`, pod warunkiem, że jest tylko jeden `default` w pliku util.js.
Wtedy import:
> 
> ```js
import * as util from './util.js'; //importujemy jako obiekt, zamiast wypisywać całą listę w nawiasach
`


```js
import * as util from './util.js'; //importujemy jako obiekt, zamiast wypisywać całą listę w nawiasach
console.log(util.abc); //odwołujemy się jak do obiektu
```




### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/38345174#overview

---



