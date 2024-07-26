
--- 
tags: [[JS Class]] [[Inheritance]]
date: 2024-07-25

---
JavaScript oferuje możliwości programowania obiektowego (OOP). W OOP tworzymy obiekty (instancje) z "szablonów" (klas), które zawierają pewne dane i funkcjonalności. Dane to pola, a funkcje to metody.

JavaScript przed wprowadzeniem klas w 2015 roku umożliwiał programowanie obiektowe przy użyciu dziedziczenia opartego na ==prototypach==. Nawet teraz, pomimo istnienia słowa kluczowego `class`, JavaScript pozostaje językiem opartym na prototypach.

### Prototypy w JavaScript

##### Funkcja Konstruktor

Szablon (klasa) jest realizowany przez zwykłą funkcję. Jeśli funkcja ma być używana jako szablon, nazywana jest funkcją konstruktorem, a jej nazwa powinna zaczynać się wielką literą. Obiekty (instancje) są tworzone za pomocą słowa kluczowego `new`.

```js
function Car() {
  // ...
}

const myCar = new Car();
const yourCar = new Car();
```

Każdy obiekt ma ukrytą właściwość `[[prototype]]`, która odnosi się do wartości klucza `prototype` funkcji konstruktora.


### Pola Instancji

Pola są dodawane do nowej instancji przez `this` w funkcji konstruktorze.

Często chcesz, aby wszystkie utworzone obiekty (instancje) zawierały pewne pola i miały przekazane pewne początkowe wartości dla tych pól podczas tworzenia obiektu. Można to ułatwić za pomocą słowa kluczowego `this`. Wewnątrz funkcji konstruktora, `this` reprezentuje nowy obiekt, który zostanie utworzony za pomocą `new`. `this` jest automatycznie zwracane z funkcji konstruktora, gdy jest ona wywoływana z `new`.

```js
function Car(color, weight) {
  this.color = color;
  this.weight = weight;
  this.engineRunning = false;
}

const myCar = new Car('red', '2mt');
console.log(myCar.color); // 'red'
console.log(myCar.engineRunning); // false

```


### Metody Instancji

Metody są dodawane za pomocą właściwości `prototype` funkcji konstruktora. Wewnątrz metody można uzyskać dostęp do pól instancji za pomocą `this`. Działa to dzięki następującej ogólnej zasadzie.

Kiedy funkcja jest wywoływana jako metoda obiektu, jej `this` jest ustawiane na obiekt, na którym metoda została wywołana.

```js
function Car() {
  this.engineRunning = false;
}

Car.prototype.startEngine = function() {
  this.engineRunning = true;
};

Car.prototype.addGas = function (litre) { 
// ... 
};

const myCar = new Car();
myCar.startEngine();
console.log(myCar.engineRunning); // true

```


### Łańcuch Prototypów

JavaScript sprawdza właściwości i metody w obiekcie, a jeśli ich nie znajdzie, szuka w prototypie tego obiektu, tworząc tzw. ==łańcuch prototypów==.

Gdy próbujesz uzyskać dostęp do dowolnej właściwości (pola lub metody) obiektu, JavaScript najpierw sprawdza, czy odpowiedni klucz można znaleźć bezpośrednio w samym obiekcie. Jeśli nie, kontynuuje szukanie klucza w obiekcie referencjonowanym przez właściwość \[\[prototype\]\] oryginalnego obiektu.

```js
function Car() {
  // ...
}

Car.prototype.startEngine = function() {
  // ...
};

const myCar = new Car();
myCar.startEngine();

```

I łańcuch się na tym nie kończy. Właściwość \[\[prototype\]\] Car.prototype (myCar.\[\[prototype\]\].\[\[prototype\]\]) odnosi się do Object.prototype (właściwości prototype funkcji konstruktora Object). Zawiera ona ogólne metody dostępne dla wszystkich obiektów JavaScript, np. toString(). W związku z tym możesz wywołać myCar.toString() i ta metoda będzie istnieć, ponieważ JavaScript przeszukuje całą ścieżkę prototypów.

>[!WARNING]  
>Należy zauważyć, że łańcuch prototypów jest przemierzany tylko podczas pobierania wartości. Ustawianie lub usuwanie właściwości obiektu instancji bezpośrednio dotyczy tylko tej konkretnej instancji. Może to nie być zgodne z oczekiwaniami, jeśli jesteś przyzwyczajony do języka z dziedziczeniem opartym na klasach.

---

### Klasy w JavaScript

Od 2015 roku JavaScript umożliwia definiowanie klas za pomocą słowa kluczowego `class`. Nowa składnia jest bardziej czytelna i przypomina języki takie jak C++ czy Java.


### Deklaracja Klasy

Klasy są definiowane za pomocą słowa kluczowego `class`, a konstruktor jest specjalną metodą o nazwie `constructor`.

```js
class Car {
  constructor(color, weight) {
    this.color = color;
    this.weight = weight;
    this.engineRunning = false;
  }

  startEngine() {
    this.engineRunning = true;
  }

  addGas(litre) {
    // ...
  }
}

const myCar = new Car('red', '2mt');
myCar.startEngine();
console.log(myCar.engineRunning); // true

```


### Metody statyczne

Definiowane za pomocą słowa kluczowego `static`, mogą być wywoływane bez tworzenia instancji klasy.

```js
class Helper {
  static logTwice(message) {
    console.log(message);
    console.log(message);
  }
}

Helper.logTwice('Hello'); // Hello \n Hello

```


### Dziedziczenie

Używając słowa kluczowego `extends`, można tworzyć klasy dziedziczące po innych klasach.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

let animal = new Animal('Dog');
animal.speak(); // Dog makes a noise.



class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

let dog = new Dog('Rex');
dog.speak(); // Rex barks.

```

Słowo kluczowe `super` w konstruktorze jest używane do wywoływania konstruktora klasy rodzica (superklasy). Jest to konieczne, gdy klasa dziecka rozszerza klasę rodzica, aby upewnić się, że właściwości zdefiniowane w konstruktorze klasy rodzica są prawidłowo zainicjowane.

Kiedy klasa dziecka ma swój własny konstruktor, musi wywołać `super` przed użyciem `this`. Poniżej znajduje się przykład, który pokazuje, jak to działa:

```js
class Pet {
  constructor(name) {
    this.name = name;
  }

  introduce() {
    console.log(`This is my pet, ${this.name}.`);
  }
}

class Dog extends Pet {
  constructor(name, breed) {
    super(name); // Wywołuje konstruktor klasy rodzica (Pet)
    this.breed = breed; // Dodaje dodatkową właściwość specyficzną dla klasy dziecka (Dog)
  }

  bark() {
    console.log('Woof!');
  }
}

const dog = new Dog('Otis', 'Labrador');
dog.introduce();
// => This is my pet, Otis.
console.log(`Breed: ${dog.breed}`);
// => Breed: Labrador
dog.bark();
// => Woof!
```


### Pola Prywatne, Gettery i Settery

Pola i metody prywatne powinny zaczynać się od podkreślenia `_`. Gettery i settery pozwalają na kontrolowany dostęp do pól. są Używane do uzyskiwania i ustawiania wartości właściwości.

```js
class Car {
  constructor() {
    this._mileage = 0;
  }

  get mileage() {
    return this._mileage;
  }

  set mileage(value) {
    throw new Error(`Mileage cannot be manipulated, ${value} is ignored.`);
  }
}

const myCar = new Car();
console.log(myCar.mileage); // 0
myCar.mileage = 100; // Error: Mileage cannot be manipulated, 100 is ignored.

```

```js
class Person {
  constructor(name) {
    this._name = name;
  }

  get name() {
    return this._name;
  }

  set name(value) {
    this._name = value;
  }
}

let person = new Person('John');
console.log(person.name); // John
person.name = 'Doe';
console.log(person.name); // Doe

```

### Podsumowanie

JavaScript umożliwia programowanie obiektowe zarówno poprzez dziedziczenie prototypowe, jak i klasy. Prototypy pozwalają na dziedziczenie właściwości i metod, a klasy wprowadzają bardziej zrozumiałą składnię, która jest bliższa tradycyjnym językom OOP.


### References:
https://exercism.org/tracks/javascript/concepts/classes
`this` Examples - As an object method, MDN --> https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this#as_an_object_method

---



