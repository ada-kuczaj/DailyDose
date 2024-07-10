
--- 
tags: [[JS]]
date: 2024-07-10

---
**Hoisting** (podnoszenie) to mechanizm w JavaScript, w którym deklaracje zmiennych i funkcji są przenoszone na początek ich zakresu (scope) podczas fazy kompilacji. Oznacza to, że zmienne i funkcje mogą być używane przed ich faktyczną deklaracją w kodzie źródłowym. Istnieją jednak różnice w hoistingu między deklaracjami zmiennych za pomocą `var`, `let`, `const` oraz funkcji zadeklarowanych przy użyciu funkcji zwykłych i funkcji wyrażeniowych.


Hoisting w rzeczywistości nie powoduje przenoszenia kodu; zamiast tego:

- Znajduje wszystkie deklaracje zmiennych i funkcji w kodzie
- „Podnosi” nazwy zmiennych i deklaracje funkcji na górę zakresu `scope` przed wykonaniem kodu
- Natychmiast inicjuje deklaracje funkcji
- Odracza obsługę inicjalizacji lub przypisania wartości do czasu wykonania kodu


JavaScript podnosi deklaracje funkcji, łącznie z treścią funkcji, na szczyt swojego zakresu. Jeśli funkcja jest zadeklarowana na poziomie globalnym, wówczas zostaje podniesiona na górę zasięgu globalnego. Podnoszenie odbywa się również w obrębie funkcji zagnieżdżonych, więc funkcje zagnieżdżone są podnoszone na górę otaczającego zakresu funkcji.

Deklarację funkcji można wywołać z dowolnego miejsca w zakresie `scope`, o ile faktycznie jest ona zadeklarowana w kodzie. 
W poniższym kodzie funkcja add() jest wywoływana przed jej zadeklarowaniem i działa zgodnie z oczekiwaniami, ponieważ deklaracja add() jest wywoływana w fazie kompilacji.

```js
console.log(add(1,2));  
// prints 3  
  
function add(a,b) {  
    return a + b  
}
```

### `var` hoisting

Zmienne var są przenoszone na górę bloków funkcji, ale nie bloków innych typów, dlatego należy zachować ostrożność podczas używania var do deklarowania zmiennych, aby mieć pewność, że podczas używania zmiennej uzyskana zostanie zamierzona wartość. Zmienne var są inicjowane jako `undefined` podczas ich podnoszenia.

Zmienna zadeklarowana za pomocą `var` jest hoistowana na początek swojego zakresu, ale inicjalizacja pozostaje na swoim miejscu. Oznacza to, że zmienna jest dostępna przed jej deklaracją, ale jej wartość będzie `undefined` do momentu jej inicjalizacji.

```js
console.log(x); // undefined
var x = 5;
console.log(x); // 5
```


### `let` and `const` hoisting

Zmienne `let` i `const` są przenoszone na górę bloku nadrzędnego w celu zapewnienia zasięgu, więc dowolny typ bloku lub funkcji może być nadrzędnym zakresem dla tych zmiennych.

`let` i `const` różnią się od `var` także sposobem inicjacji; podczas gdy nazwy są podnoszone, nie są inicjowane. Zatem wywołanie zmiennej w kodzie przed jej inicjalizacją powoduje wystąpienie błędu `ReferenceError`. Jest to jeden z powodów, dla których preferowane są `let` i `const`, ponieważ błąd `ReferenceError` natychmiast powiadomi Cię o problemie w kodzie. 

Zmiennie zadeklarowane za pomocą `let` i `const` są również hoistowane, ale różnica polega na tym, że nie są inicjalizowane. Są one umieszczone w tzw. "temporal dead zone" (TDZ), czyli strefie czasowej, w której dostęp do nich jest niemożliwy aż do momentu ich deklaracji w kodzie.

```js
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;

console.log(z); // ReferenceError: Cannot access 'z' before initialization
const z = 20;
```

### Hoisting funkcji

#### Deklaracje funkcji

Deklaracje funkcji są całkowicie hoistowane, co oznacza, że zarówno nazwa funkcji, jak i jej ciało są przenoszone na początek zakresu. Funkcje zadeklarowane w ten sposób mogą być wywoływane przed ich deklaracją w kodzie źródłowym.

```js
greet();

function greet() {
    console.log("Hello, world!");
}
```

Powyższy kod działa poprawnie i wyświetla "Hello, world!" w konsoli, ponieważ deklaracja funkcji `greet` jest hoistowana na początek.

#### Funkcje wyrażeniowe

Funkcje zadeklarowane jako wyrażenia (function expressions) NIE są hoistowane w ten sam sposób. Zmienna, do której przypisana jest funkcja, jest hoistowana, ale sama funkcja już nie. Oznacza to, że próba wywołania takiej funkcji przed jej deklaracją skutkuje błędem.

```js
sayHello(); // TypeError: sayHello is not a function

var sayHello = function() {
    console.log("Hello!");
};
```

#### Funkcje strzałkowe

Jeśli używasz składni funkcji strzałkowych ES6, ważne jest, aby pamiętać o przypisaniu funkcji do zmiennej przed jej wywołaniem.

```js
// thisWontRun() is hoisted at the function call but not yet initialized  
thisWontRun();  
let thisWontRun = a => console.log(a);  
  
// thisWillRun() gets initialized after function call below  
let thisWillRun = b => console.log(b);  
// thisWillRun() gets hoisted at the function call  
thisWillRun();
```

### Podsumowanie

Hoisting w JavaScript:

- **`var`**: Deklaracje są hoistowane, inicjalizacje nie.
- **`let` i `const`**: Deklaracje są hoistowane, ale dostępne tylko po inicjalizacji (TDZ).
- **Deklaracje funkcji**: Całe deklaracje (nazwa i ciało) są hoistowane.
- **Funkcje wyrażeniowe**: Zmienna jest hoistowana, ale przypisanie funkcji nie.
### References:

https://www.codecademy.com/courses/learn-javascript-best-practices/articles/javascript-hoisting
---



