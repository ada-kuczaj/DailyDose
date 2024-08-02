
--- 
tags: [[JS Functions]]
date: 2024-07-09

---
Wyrażenie funkcji strzałkowej jest alternatywą dla tradycyjnych funkcji, z pewnymi różnicami semantycznymi i celowymi ograniczeniami w użyciu:

- Funkcje strzałkowe nie mają własnych powiązań z `this`, `arguments` ani `super` i nie powinny być używane jako metody.

- Funkcje strzałkowe NIE mogą być używane jako konstruktory. Wywołanie ich za pomocą `new` powoduje błąd `TypeError`. Nie mają również dostępu do słowa kluczowego `new.target`.

- Funkcje strzałkowe nie mogą wykorzystywać `yield` w swojej treści i nie można ich tworzyć jako funkcji generatora.

Przykład:
```js
const materials = ['Hydrogen', 'Helium', 'Lithium', 'Beryllium'];

console.log(materials.map((material) => material.length));
// Expected output: Array [8, 6, 7, 9]

```

Składnia:
```js
() => expression

param => expression

(param) => expression

(param1, paramN) => expression

() => {
  statements
}

param => {
  statements
}

(param1, paramN) => {
  statements
}

```

--- 

W funkcjach strzałkowych (arrow functions) w JavaScript, istotne jest rozróżnienie między "statement" a "expression". Oto wyjaśnienie różnic między nimi:

### Expression (Wyrażenie)

- **Definicja**: Expression to fragment kodu, który ewaluowany jest do wartości. Może to być np. operacja arytmetyczna, przypisanie wartości, wywołanie funkcji itp.
- **Składnia**: Jeśli ciało funkcji strzałkowej jest pojedynczym wyrażeniem, można pominąć nawiasy klamrowe `{}` i słowo kluczowe `return`.
- **Zastosowanie**: Używane, gdy funkcja ma zwracać wartość bez potrzeby dodatkowej logiki.

```js
const add = (a, b) => a + b;
```
### Statement (Instrukcja)

- **Definicja**: Statement to polecenie, które wykonuje jakąś akcję, ale nie zwraca wartości. Może to być np. instrukcja warunkowa `if`, pętla `for`, przypisanie wartości itp.
- **Składnia**: Jeśli ciało funkcji strzałkowej zawiera więcej niż jedną instrukcję, należy użyć nawiasów klamrowych `{}`. W takim przypadku, aby zwrócić wartość, trzeba użyć słowa kluczowego `return`.
- **Zastosowanie**: Używane, gdy funkcja ma wykonać kilka instrukcji lub zawiera logikę kontrolną.
- 
```js
const addAndLog = (a, b) => {
    const result = a + b;
    console.log(result);
    return result;
};
```
### Podsumowanie

- **Expression**: Proste, jednowierszowe funkcje strzałkowe, które zwracają wartość bez użycia `{}` i `return`.
- **Statement**: Funkcje strzałkowe zawierające wiele instrukcji lub logikę kontrolną, wymagające `{}` i jawnego użycia `return` do zwracania wartości.

---
Funkcje strzałkowe mogą być asynchroniczne, poprzedzając wyrażenie słowem kluczowym `async`.

```js
async param => expression
```

---

```js
// Traditional anonymous function
(function (a) {
  return a + 100;
});

// 1. Remove the word "function" and place arrow between the argument and opening body brace
(a) => {
  return a + 100;
};

// 2. Remove the body braces and word "return" — the return is implied.
(a) => a + 100;

// 3. Remove the parameter parentheses
a => a + 100;
```






```js
function addUpTwoNumbers(num1, num2) { return num1 + num2; } 
// function keyword removed and => added 
const addUpTwoNumbers = (num1, num2) => { return num1 + num2; };
```

Jeśli treść funkcji zawiera tylko instrukcję return, jak w powyższym przykładzie, można pominąć {} i słowo kluczowe return.

```js
const addUpTwoNumbers = (num1, num2) => { return num1 + num2 }; 
// can be shortened to 
const addUpTwoNumbers = (num1, num2) => num1 + num2; 
// braces {} and return removed
```








### References:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions
https://exercism.org/tracks/javascript/concepts/arrow-functions

---



