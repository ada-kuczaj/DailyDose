
--- 
tags: [[JS]] 
date: 2024-07-08

---
Technika programowania polegająca na rozwijaniu funkcji. Używamy jej, aby pisany kod był bardziej modularny, łatwiejszy do testowania i wielokrotnego użytku.

**Programowanie funkcjonalne** to paradygmat deklaratywny, który kładzie nacisk na niezmienność i czyste funkcje — co oznacza, że ​​funkcja jest wolna od skutków ubocznych i dla dowolnych danych wejściowych zawsze zwróci ten sam wynik.

```js
// traditional function
function add(a,b) {  
    return a + b;  
}
```

Przyjrzyjmy się funkcji add(), aby zobaczyć, jak możemy lepiej obsłużyć wywołanie funkcji, jeśli dostępny jest tylko jeden argument (aby zapobiec NaN, undefined itp.) Jedyne, co możemy zrobić, to przekształcić funkcję add(), która zwykle oczekuje wielu argumentów, w serię **==zagnieżdżonych funkcji, z których każda będzie przyjmować pojedynczy argument.==**

Dzięki temu wywołania funkcji są bardziej modułowe. W przypadku funkcji curry wywołanie funkcji zewnętrznej zwraca następną funkcję w łańcuchu i tak dalej, aż zostanie wywołana funkcja najbardziej wewnętrzna, która następnie zwróci wartość.

```js
// curried function  
function curried_add(a) {  
    // The outer function returns a nested single-argument function  
    return function nested_func(b) {  
        return a + b;  
   }  
}
```

W poniższym bloku kodu przypisujemy wynik wywołania curried_add() do zmiennej o nazwie add_one.

```js
let add_one = curried_add(1);  
// returns nested_func()
```

Teraz, gdy wywołamy funkcję add_one(), zwróci ona wartość a + b, ponieważ jest to funkcja zagnieżdżona_func().

```js
add_one(10);  
// returns 11
```

Dzięki  *regułom zakresu leksykalnego* * funkcje zagnieżdżone będą nadal miały dostęp do wszelkich zmiennych zadeklarowanych w zewnętrznym zakresie funkcji nadrzędnych. 
 
```js
function curried_add(a) {  
    // has access to the argument for a  
    return function nested_add(b) {  
        // has access to the arguments for a and b  
        return a + b;  
    }  
}  
  
// creates a local variable a and assigns it the value 1  
let add_one = curried_add(1);  
  
// add_one() still has access to the argument from curried_add()  
add_one(10);
```





### References:


---



