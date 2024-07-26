
--- 
tags: [[JS Object]] [[JS Class]] [[Prototypy i Klasy (Class)]]
date: 2024-07-26

---
Dziedziczenie jest sposobem tworzenia relacji rodzic-dziecko między klasami. Klasa dziecka (czasami nazywana podklasą) ma dostęp do zachowań i danych zdefiniowanych przez klasę rodzica (czasami nazywaną superklasą).

```js
class Pet {
  constructor(name) {
    this.name = name;
  }

  introduce() {
    console.log(`This is my pet, ${this.name}.`);
  }
}

class Dog extends Pet {}

const dog = new Dog('Otis');
dog.introduce();
// => This is my pet, Otis.
```

Słowo kluczowe `extends` w deklaracji klasy dziecka ustanawia relację z klasą rodzica poprzez łańcuch prototypów.

Obiekty utworzone przez konstruktor klasy dziecka będą miały prototyp klasy rodzica w swoim łańcuchu prototypów, co zapewnia dostęp do wszelkich metod lub danych zdefiniowanych przez rodzica.

```js
const dog = new Dog('Otis');

Dog.prototype.isPrototypeOf(dog); // => true
Pet.prototype.isPrototypeOf(dog); // => true
Pet.prototype.isPrototypeOf(Dog.prototype); // => true

Pet.prototype.hasOwnProperty('introduce'); // => true
Dog.prototype.hasOwnProperty('introduce'); // => false
dog.hasOwnProperty('introduce'); // => false
```

Jak w przypadku każdej klasy w JavaScript, klasy podrzędne mogą dziedziczyć z klasy `Error`, aby tworzyć niestandardowe błędy, używając słowa kluczowego `extends`. Składnia `instanceof` sprawdzi, czy złapany błąd jest instancją określonej podklasy `Error`.

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
https://exercism.org/tracks/javascript/concepts/inheritance
---



