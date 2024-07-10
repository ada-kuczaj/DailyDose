
--- 
tags: [[5 - Tags/Methods|Methods]] 
date: 2024-07-02

---
Metoda to funkcja będąca właściwością obiektu. Istnieją dwa rodzaje metod: metody instancji, które są wbudowanymi zadaniami wykonywanymi przez instancję obiektu, lub metody statyczne, które są zadaniami wywoływanymi bezpośrednio w konstruktorze obiektu.

# Najważniejsze metody:

Przykładowa tablica ```

```js
const films = [
  { name: "Titanic", year: 1997, rating: 7.5 },
  { name: "Władca pierścieni", year: 1978, rating: 5.4 },
  { name: "Zielona mila", year: 1999, rating: 8.3 },
  { name: "Skazani na Shawshank", year: 1994, rating: 8.4 },
  { name: "Ojciec chrzestny", year: 1972, rating: 9.2 }
];
```

## Map

Metoda `map()` pozwala na iteracyjne przeglądanie treści tablicy i wykonania określonej czynności na danym elemencie tablicy. Poniższy kod utworzy nam nową tablicę, jednak zawierającą jedynie nazwy filmów.

```js
const filmNames = films.map((film) => {
  return film.name;
});
```

## Filter

Jak sama nazwa metody wskazuje, `filter()` przetworzy nam dane z tablicy i wyodrębni tylko te dane, które jej wskażemy. W poniższym przykładzie wybierzmy filmy nowsze niż rok 1990.

```js
const filteredFilms = films.filter(film => {
  return film.year >= 1990;
});
```
## ForEach

Metoda `forEach()` również iteruje po wszystkich elementach tablicy, jednak nie tworzy ona osobnej struktury, tylko wykona prostą czynność jak w poniższym przykładzie, czyli wyświetli określone dane.

```js
films.forEach((film) => {
  console.log(`${film.name} - moja ocena filmu: ${film.rating}`);
});
```
## Find

Metoda `find()` zwraca pierwszy element tablicy, który będzie spełniał warunek funkcji. Natomiast, gdy nie ma elementów spełniających warunek, zwróci „_undefined_”.

```js
const foundFilm = films.find((film) => {
  return film.name === "Ojciec chrzestny";
});
```




### References:

https://developer.mozilla.org/en-US/docs/Glossary/Method
https://www.lukaszbacik.pl/4-najwazniejsze-metody-w-javascript/

---



