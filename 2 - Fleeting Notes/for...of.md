
--- 
tags: [[JS]]
date: 2024-07-16

---
W JavaScript, pętla `for...of` jest używana do iterowania po iterowalnych obiektach, takich jak tablice, ciągi znaków, mapy, zbiory i inne struktury danych, które implementują protokół iterowalności. Jest szczególnie użyteczna, gdy chcemy iterować po elementach tych struktur danych bez potrzeby korzystania z indeksów, co czyni ją bardziej czytelną i wygodną w użyciu.

### Jak działa `for...of`?

Pętla `for...of` iteruje po wartościach iterowalnego obiektu. W przypadku ciągów znaków, iteruje po kodach punktów Unicode (co jest szczególnie przydatne w przypadku obsługi znaków wielobajtowych, takich jak emoji).

```js
for (const element of iterable) {
  // instrukcje do wykonania dla każdego elementu
}
```

- `const element`: zmienna, która przyjmuje wartość każdego kolejnego elementu iterowalnego obiektu podczas każdej iteracji.
- `iterable`: obiekt, który jest iterowalny, np. tablica, ciąg znaków, mapa, zbiór, itd.

```js
const string = "Hello";

for (const char of string) {
  console.log(char);
}
// Output:
// H
// e
// l
// l
// o
```
### Kluczowe zalety `for...of`:

- **Obsługa znaków Unicode**: Pętla `for...of` poprawnie iteruje po kodach punktów Unicode, co jest przydatne przy obsłudze wielobajtowych znaków takich jak emoji.
- **Łatwość użycia**: Pętla jest prostsza i bardziej czytelna w porównaniu do klasycznych pętli `for` lub `for...in`, zwłaszcza przy iteracji po wartościach.
- **Uniwersalność**: Działa z różnymi typami iterowalnych obiektów, nie tylko tablicami i ciągami znaków.


### References:

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_characters_unicode_code_points_and_grapheme_clusters
---



