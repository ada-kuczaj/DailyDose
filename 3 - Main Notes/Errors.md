
--- 
tags: [[JS Object]]
date: 2024-07-26

---

Błędy są przydatne do raportowania, gdy coś jest nie tak lub niespodziewane w programie lub fragmencie kodu.

Errory to obiekty w JavaScript.
Główną właściwością tego obiektu jest `message`:

```js
const error = new Error('Oops, something went wrong');

console.log(error.message);
// => "Oops, something went wrong"
```
Używając składni `throw`, można wyrzucić błąd.

```js
throw new Error('Oops');
```
Gdy `Error` jest wyrzucany, bieżące wykonanie jest zatrzymywane i wznawiane w pierwszym bloku `catch` stosu wywołań.

```js
try {
  throw new Error('Oops');
} catch (error) {
  console.log(error.message);
  // => "Oops"
}
```

Jak w przypadku każdej klasy w JavaScript, klasy podrzędne mogą dziedziczyć z klasy `Error`, aby tworzyć niestandardowe błędy, używając słowa kluczowego `extends`. Składnia `instanceof` sprawdzi, czy złapany błąd jest instancją określonej klasy podrzędnej `Error`.

```js
class CustomError extends Error {}

try {
  // ... Kod, który może wyrzucić błąd
} catch (error) {
  if (error instanceof CustomError) {
    console.log('Wyrzucony błąd jest instancją klasy CustomError');
  }
}
```


### References:
https://exercism.org/tracks/javascript/concepts/errors

---



