
--- 
tags: [[ASCII, UTF-8, UTF-16 i Unicode]]
date: 2024-07-17

---
Fragment zadania z ==anagramami==. Porównywanie wyrazów za pomocą kodowania ASCII.

Tworzymy tablicę z 128 miejscami i wypełniamy je zerami.

Iterujemy po str1 i porównywanym do niego str2 i jednocześnie:
- zwiększamy licznik danej pozycji w zależności od wystąpienia litery (na pozycji jej kodu) dla str1
- zmniejszamy licznik danej pozycji w zależności od wystąpienia litery (na pozycji kodu) dla str2

Jeśli oba ciągi mają te same znaki w dowolnej kolejności, przyrost i spadek  liczników tych samych znaków ostatecznie zrównoważą się do zera.

Na końcu przechodzimy przez tablicę `charCount`. Jeśli którykolwiek licznik nie jest równy zeru, oznacza to, że jeden z ciągów ma więcej wystąpień pewnego znaku niż drugi, więc zwracamy `false`. Jeśli wszystkie liczniki są zerami, zwracamy `true`, co oznacza, że oba ciągi są anagramami.

```js
    const charCount = new Array(128).fill(0);
    
    for (let i = 0; i < str1.length; i++) {
        charCount[str1.charCodeAt(i)]++;
        charCount[str2.charCodeAt(i)]--;
    }
    
    for (let count of charCount) {
        if (count !== 0) {
            return false;
        }
    }
    return true;
}
```

---
### Inny przykład:

Załóżmy, że chcemy zliczyć wystąpienia poszczególnych znaków w ciągu "Hello":

```js
const charCount = new Array(128).fill(0);
const str1 = "Hello";

for (let i = 0; i < str1.length; i++) {
  charCount[str1.charCodeAt(i)]++;
}

console.log(charCount);
```
### Analiza:

1. Inicjalizujemy tablicę `charCount` o długości 128 z wszystkimi elementami ustawionymi na 0.
2. Przechodzimy przez każdy znak w ciągu `str1`:
    - Dla `i = 0`, `str1.charCodeAt(0)` zwraca 72 (kod ASCII dla 'H'). `charCount[72]` jest zwiększane z 0 na 1.
    - Dla `i = 1`, `str1.charCodeAt(1)` zwraca 101 (kod ASCII dla 'e'). `charCount[101]` jest zwiększane z 0 na 1.
    - Dla `i = 2`, `str1.charCodeAt(2)` zwraca 108 (kod ASCII dla 'l'). `charCount[108]` jest zwiększane z 0 na 1.
    - Dla `i = 3`, `str1.charCodeAt(3)` zwraca 108 (kod ASCII dla 'l'). `charCount[108]` jest zwiększane z 1 na 2.
    - Dla `i = 4`, `str1.charCodeAt(4)` zwraca 111 (kod ASCII dla 'o'). `charCount[111]` jest zwiększane z 0 na 1.

Po zakończeniu pętli, tablica `charCount` będzie zawierała liczniki dla odpowiednich kodów ASCII, które pojawiły się w ciągu `str1`.

Następnie analogicznie odejmujemy te dla str2 i jeżeli tablica będzie zawierała same zera, wyrazy są anagramami.

### References:


---



