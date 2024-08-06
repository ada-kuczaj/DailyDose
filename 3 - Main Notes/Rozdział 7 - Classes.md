
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-08-06

---

**KLUCZOWE INFORMACJE W ROZDZIALE 7:**
	• Programowanie zorientowane obiektowo
	• Klasy i obiekty
	• Klasy 
	• Dziedziczenie 
	• Prototypy



### Programowanie zorientowane obiektowo

Object-oriented programming (OOP) - paradygmat programowania, w którym kod jest strukturyzowany w obiekty, co prowadzi do bardziej utrzymywalnego i wielokrotnego użycia kodu. Praca z OOP uczy myślenia o różnych tematach w kategoriach obiektów, grupując właściwości w taki sposób, aby mogły być opakowane w schemat zwany klasą. Ta z kolei może dziedziczyć właściwości od klasy nadrzędnej.

**Zalety OOP:**

- **Modularność:** Programy są podzielone na moduły (klasy), co ułatwia ich zarządzanie i współpracę zespołów programistycznych.

- **Reużywalność kodu:** Dzięki dziedziczeniu i polimorfizmowi możliwe jest wielokrotne użycie istniejących klas.

- **Łatwość w utrzymaniu:** Modyfikacje w kodzie są łatwiejsze do wprowadzenia, ponieważ zmiany w jednej klasie mogą być izolowane i nie wpływają na inne części systemu.

- **Lepsze odwzorowanie rzeczywistości:** Obiekty mogą reprezentować rzeczywiste byty, co ułatwia modelowanie problemów z rzeczywistości.



### Klasy i obiekty

- **Klasa:**
    - Klasa to szablon lub blueprint, z którego tworzone są obiekty. Definiuje ona właściwości i zachowania, które obiekty danej klasy będą miały.

- **Obiekt:**
	- Obiekt to instancja klasy. Jest konkretnym egzemplarzem klasy z własnym stanem. Obiekty zawierają właściwości i metody. Właściwości obiektu powinny mieć sensowne nazwy.

```js
class ClassName {
  constructor(prop1, prop2) {
    this.prop1 = prop1;
    this.prop2 = prop2;
  }
}

let obj = new ClassName("arg1", "arg2"); 
```

Ten kod definiuje klasę o nazwie ClassName, deklaruje zmienną obj i inicjalizuje ją nową instancją obiektu. Podane są dwa argumenty. Te argumenty zostaną użyte przez konstruktor do inicjalizacji właściwości. Jak widać, parametry konstruktora i właściwości klasy (prop1 i prop2) mają tę samą nazwę. Właściwości klasy można rozpoznać po słowie kluczowym `this` przed nimi. Słowo kluczowe `this` odnosi się do obiektu, do którego należy, więc jest to pierwsza właściwość instancji ClassName. 

>[!IMPORTANT] 
UWAGA: w Javascript klasy to po prostu specjalne funkcje pod powierzchnią (inaczej niż w pozostałych językach programowania)


Pierwszy sposób tworzenia obiektu za pomocą funkcji:

```js
function Dog(dogName, weight, color, breed) {
  this.dogName = dogName;
  this.weight = weight;
  this.color = color;
  this.breed = breed;
}

let dog = new Dog("Jacky", 30, "brown", "labrador");
```

Drugi sposób tworzenia obiektu za pomocą składni klasy: 

```js
class Dog {
  constructor(dogName, weight, color, breed) {
    this.dogName = dogName;
    this.weight = weight;
    this.color = color;
    this.breed = breed;
  }
}

let dog = new Dog("JavaScript", 2.4, "brown", "chihuahua");
```

To skutkuje obiektem z tymi samymi właściwościami.


### Klasy

Klasy są schematem lub szablonem do tworzenia obiektów. Zgodnie z konwencją, nazwy klas zaczynamy od wielkiej litery. Jeśli potrzebujemy stworzyć 20 psów, musimy pisać znacznie mniej, gdy mamy klasę psa. Jeśli musimy tworzyć obiekty, musimy każdorazowo określać wszystkie nazwy właściwości. Łatwo byłoby zrobić literówkę i źle napisać nazwę właściwości. Klasy przydają się w takich sytuacjach.

#### Konstruktor
Ważnym elementem klasy jest konstruktor. Metoda konstruktor to specjalna metoda, której używamy do inicjalizacji obiektów z naszym szablonem klasy. W klasie może być tylko jeden konstruktor. Ten konstruktor zawiera właściwości, które zostaną ustawione podczas inicjalizacji klasy.

```js
class Person {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }
}
```

Gdy utworzymy klasę bez wszystkich właściwości, Javascript automatycznie nada im undefined. 

```js
let p = new Person("Maaike");
console.log("Hi", p.firstname, p.lastname);
//Hi Maaike undefined
```

Można określić wartości domyślne w konstruktorze.

```js
constructor(firstname, lastname = "Doe") {
  this.firstname = firstname;
  this.lastname = lastname;
}
```


### Metody

Obiekt może zacząć wykonywać różne czynności, korzystając z własnych właściwości, na przykład drukując imię. Określone w klasie funkcje nazywane są metodami. Podczas definiowania tych metod nie używamy słowa kluczowego `function`. Zaczynamy bezpośrednio od nazwy.

```js
class Person {
  constructor(firstname, lastname) {
    this.firstname = firstname;
    this.lastname = lastname;
  }
  
  greet() {
    console.log("Hi there!");
  }
  
  compliment(name, object) {
    return "That's a wonderful " + object + ", " + name;
  }
}

let compliment = p.compliment("Harry", "hat");
console.log(compliment);

```


### Właściwości (Properties)

Właściwości, czasami nazywane również polami, przechowują dane klasy. Właściwości można dodawać lub usuwać tak samo jak dla obiektów. Można uzyskać do nich dostęp z zewnątrz klasy, wypisując je na konsoli poza klasą poprzez dostęp do nich na instancji:

```js
let p = new Person("Maaike", "van Putten");
console.log("Hi", p.firstname);
```

Często nie jest pożądane, aby zapewnić bezpośredni dostęp do właściwości wewnątrz klasy. Chcemy, aby nasza klasa miała kontrolę nad wartościami. Aby dodać właściwości, które nie są dostępne z zewnątrz prefiksujemy je symbolem `#`

```js
class Person {
  #firstname;
  #lastname;
  
  constructor(firstname, lastname) {
    this.#firstname = firstname;
    this.#lastname = lastname;
  }
}
```


>[!WARNING] 
>W JavaScript istnieją dwie główne konwencje dotyczące definiowania pól prywatnych w klasach: użycie prefiksu `#` oraz użycie prefiksu `_`

>Od wersji ECMAScript 2019 (ES10), JavaScript wprowadził wsparcie dla prywatnych pól klasowych za pomocą prefiksu `#`. Jest to oficjalny sposób na deklarowanie pól prywatnych, które są dostępne tylko wewnątrz klasy.
>
>Użycie prefiksu `_` jest jedynie konwencją, która sugeruje, że pole jest przeznaczone do użytku wewnętrznego i nie powinno być modyfikowane bezpośrednio z zewnątrz klasy. Jednakże, nie zapewnia to rzeczywistej prywatności, a jedynie informuje innych programistów o zamiarze.



### Akcesory (Getters) i Mutatory (Setters)

Akcesory i mutatory to specjalne właściwości, których możemy używać do pobierania danych z klasy oraz do ustawiania pól danych w klasie. Wyglądają trochę jak funkcje, ponieważ mają nawiasy () za sobą, ale nimi nie są. Akcesory zaczynają się od słów kluczowych `get` i `set`.

Uważa się za dobrą praktykę, aby jak najwięcej pól było prywatnych i zapewniało dostęp do nich za pomocą akcesorów i mutatorów. W ten sposób właściwości nie mogą być ustawiane z zewnątrz bez kontroli samego obiektu. Ta zasada nazywana jest ==enkapsulacją==. Klasa kapsułkuje dane, a obiekt kontroluje swoje własne pola.

```js
class Person {
  #firstname;
  #lastname;
  
  constructor(firstname, lastname) {
    this.#firstname = firstname;
    this.#lastname = lastname;
  }
  
  get firstname() {
    return this.#firstname;
  }
  
  set firstname(firstname) {
    this.#firstname = firstname;
  }
  
  get lastname() {
    return this.#lastname;
  }
  
  set lastname(lastname) {
    this.#lastname = lastname;
  }
}
```

**Akcesor (getter)** jest używany do pobierania właściwości. Dlatego nie przyjmuje żadnych parametrów, a po prostu zwraca właściwość. 

**Mutator (setter)** działa odwrotnie: przyjmuje parametr, przypisuje tę nową wartość do właściwości i nic nie zwraca. Mutator może zawierać więcej logiki, na przykład walidację.

Akcesor może być używany na zewnątrz obiektu, jakby był właściwością. Właściwości nie są już bezpośrednio dostępne z zewnątrz klasy, ale można uzyskać do nich dostęp za pomocą akcesora, aby pobrać wartość, oraz za pomocą mutatora, aby zaktualizować wartość.



### Dziedziczenie (Inheritance)

Jest to koncepcja, że klasy mogą mieć klasy potomne, które dziedziczą właściwości i metody z klasy rodzica.

```js
class Vehicle {
  constructor(color, currentSpeed, maxSpeed) {
    this.color = color;
    this.currentSpeed = currentSpeed;
    this.maxSpeed = maxSpeed;
  }
  
  move() {
    console.log("moving at", this.currentSpeed);
  }
  
  accelerate(amount) {
    this.currentSpeed += amount;
  }
}
```

To klasa `Motorcycle`, która dziedziczy z tej klasy przy użyciu słowa kluczowego `extends`:

```js
class Motorcycle extends Vehicle {
  constructor(color, currentSpeed, maxSpeed, fuel) {
    super(color, currentSpeed, maxSpeed);
    this.fuel = fuel;
  }
  
  doWheelie() {
    console.log("Driving on one wheel!");
  }
}
```

Słowo `super` w konstruktorze wywołuje konstruktor z klasy rodzica. Wywołanie `super()` nie jest opcjonalne, trzeba to zrobić, gdy jest się w klasie, która dziedziczy z innej klasy, w przeciwnym razie otrzymamy `ReferenceError`.

Aktualnie nie używamy tutaj żadnych getterów ani setterów, ale moglibyśmy to zrobić. Jeśli akcesory i mutatory są w klasie rodzica, są one również dziedziczone przez klasę potomną. W ten sposób moglibyśmy kontrolować, które właściwości mogą być pobierane i zmieniane (i jak) z zewnątrz naszej klasy. Jest to ogólnie dobra praktyka.


### Prototypy

Prototyp to mechanizm w JavaScript, który umożliwia istnienie obiektów. Gdy nic nie jest określone podczas tworzenia klasy, obiekty dziedziczą z prototypu `Object.prototype`. Jest to dość złożona wbudowana klasa JavaScript, której możemy używać. Nie musimy zagłębiać się w to, jak jest zaimplementowana w JavaScript, ponieważ możemy traktować ją jako bazowy obiekt, który jest zawsze na szczycie drzewa dziedziczenia i dlatego zawsze obecny w naszych obiektach.

Każda klasa ma dostęp do właściwości prototypu, która zawsze nazywa się "prototype".

```js
ClassName.prototype

//Przykład dodawania funkcji do klasy za pomocą właściwości prototypu.
Person.prototype.introduce = function () {
  console.log("Hi, I'm", this.firstname);
};

Person.prototype.favoriteColor = "green";

```

`prototype` to właściwość przechowująca wszystkie właściwości i metody obiektu. Więc dodanie funkcji do prototypu to dodanie funkcji do klasy. Można użyć prototypu, aby dodać właściwości lub metody do obiektu.

To tak, jakbyś zdefiniował klasę z właściwością `favoriteColor` przechowującą domyślną wartość oraz z funkcją `introduce`. Zostały one dodane do klasy i są dostępne dla wszystkich instancji oraz przyszłych instancji. Tak więc metody i właściwości zdefiniowane za pomocą prototypu są naprawdę tak, jakby były zdefiniowane w klasie. Oznacza to, że nadpisanie ich dla pewnej instancji nie nadpisuje ich dla wszystkich instancji.




### References:
Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



