
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-07-27

---

**KLUCZOWE INFORMACJE W ROZDZIALE 6:**
	• Podstawowe funkcje
	• Argumenty funkcji
	• Return 
	• Zakres zmiennych w funkcjach (scope) 
	• Funkcje rekurencyjne
	• Funkcje zagnieżdżone
	• Funkcje anonimowe
	• Callbacks


### Podstawowe funkcje

Wywoływanie funkcji:

```js
nameOfTheFunction(); 
functionThatTakesInput("the input", 5, true);
```

Składnia funkcji:
```js
function sayHello() { 
	let you = prompt("What's your name? "); 
	console.log("Hello", you + "!"); 
}
```

### Nazywanie funkcji

Dobra praktyki
- używać camelCase 
- nazwa powinna opisywać, co funkcja robi
- używać czasownika, aby opisać, co funkcja robi - ma to być akcja
  Zamiast `hiThere`, lepiej nazwać funkcję `sayHi`


### Parametry i argumenty

Parametr jest definiowany jako zmienna wymieniona wewnątrz nawiasów w definicji funkcji, która określa zakres działania funkcji. Kiedy funkcja zostanie wywołana, wykona dodawanie przekazanych parametrów i wyświetli wynik. Aby to zrobić, należy wywołać funkcję z argumentami:

```js
function addTwoNumbers(x, y) {
    console.log(x + y);
}
myFunc("arg1", "arg2");
```

Wywołując funkcję bez parametrów Javascript przypisze im wartość `undefined`. 


#### Wartość domyślna parametrów:

Jeśli teraz wywoła się funkcję bez argumentów, automatycznie przypisze ona 2 do `x` i 3 do `y`, chyba że nadpiszemy je, wywołując funkcję z argumentami. Wartości używane podczas wywołania funkcji mają priorytet nad zakodowanymi argumentami.

```js
function addTwoNumbers(x = 2, y = 3) {
    console.log(x + y);
}
```



### Funkcje strzałkowe

Funkcje strzałkowe w JavaScript to skrócona notacja do pisania funkcji, która jest bardziej zwięzła i czytelna. Oto kilka powodów, dlaczego funkcje strzałkowe są używane:

- **Krótsza składnia:** Funkcje strzałkowe eliminują potrzebę używania słowa kluczowego `function`, a także słowa `return` w przypadku jednowierszowych funkcji.

- **Automatyczne wiązanie `this`:** Funkcje strzałkowe nie mają własnego `this`, co oznacza, że używają `this` z zewnętrznego zakresu, co jest szczególnie przydatne w przypadku funkcji zagnieżdżonych.

```js
(param1, param2) => body of the function;
() => body of the function; //for no parameters
param => body of the function; //for one parameter

param1, param2) => { 
	// line 1; 
	// any number of lines; 
};
```

Aby zamienić zwykłą funkcję na funkcję strzałkową, jeśli chcemy jej używać, trzeba przechować ją w zmiennej lub przekazać jako argument. Używamy nazwy zmiennej do wywołania funkcji strzałkowej.

```js
let doingArrowStuff = x => console.log(x);
```
`
Warto łączyć funkcje strzałkowe z niektórymi wbudowanymi metodami. Na przykład możemy użyć metody `forEach()` na tablicy. Ta metoda wykonuje określoną funkcję dla każdego elementu w tablicy. 

```js
const arr = ["squirrel", "alpaca", "buddy"];
arr.forEach(e => console.log(e));
```


### Spread operator (operator rozproszenia)

Operator spread (`...`) jest używany do rozwijania elementów tablicy lub obiektu.
Operator rozproszenia to składa się z trzech kropek użytych przed wyrażeniem referencyjnym lub ciągiem znaków i rozprasza argumenty lub elementy tablicy.

```js
const numbers = [1, 2, 3];
const newNumbers = [...numbers];
console.log(newNumbers); // [1, 2, 3]
```

```js
function addFourNumbers(x, y, z, a) {
    console.log(x + y + z + a);
}
let arr = [5, 9];
let arr2 = [6, 7];
addFourNumbers(...arr, ...arr2);
// addFourNumbers(5, 9, 6, 7);
```

```js
const person = { name: 'John', age: 30 };
const newPerson = { ...person, city: 'New York' };
console.log(newPerson); // { name: 'John', age: 30, city: 'New York' }
```



### Rest parameter (operator reszty)

Ma on ten sam symbol co operator spread, ale jest stosowany wewnątrz listy parametrów funkcji. Operator rest (`...`) jest używany do gromadzenia pozostałych argumentów funkcji w tablicę.

```js
const [first, ...rest] = [1, 2, 3, 4];
console.log(first); // 1
console.log(rest); // [2, 3, 4]
```


### Return

Aby funkcja mogła zwracać wynik, używamy słowa kluczowego `return`, po którym następuje wartość, którą chcemy zwrócić. Wynik zwrócony przez funkcję można przechować w zmiennej, aby móc go dalej wykorzystywać. Jeśli funkcja nie zawiera instrukcji `return`, zwróci `undefined` jako wynik. Instrukcja `return` kończy wykonywanie funkcji natychmiast. Kod znajdujący się po `return` w tej samej funkcji nie zostanie wykonany. W funkcjach strzałkowych (jednoliniowych) możemy zwrócić wartość bez słowa kluczowego `return`.
 


### Zakres zmiennych w funkcjach (scope) 

Zakres (scope) definiuje, gdzie można uzyskać dostęp do danej zmiennej. Gdy zmienna jest w zakresie, możesz ją uzyskać. Gdy zmienna jest poza zakresem, nie możesz uzyskać do niej dostępu. 

#### Zmienne lokalne w funkcjach

Zmienne lokalne są w zakresie tylko wewnątrz funkcji, w której są zdefiniowane. Dotyczy to zarówno zmiennych `let`, jak i `var` oraz parametrów funkcji. Zmienne lokalne zadeklarowane wewnątrz funkcji nie są dostępne poza funkcją, ale za pomocą `return` możesz udostępnić ich ==wartości== poza funkcją.

```js
function testAvailability() { 
	let y = "I'll return"; 
	console.log("Available here:", y); 
	return y; 
} 

let z = testAvailability(); 
	console.log("Outside the function:", z); 
	console.log("Not available here:", y);
	
//Available here: I'll return 
//Outside the function: I'll return 
//ReferenceError: y is not defined
```

#### zmienne let, var, const a zasięg 

Różnica między `let` a `var` polega na tym, że `var` jest zmienną zasięgu funkcji (function-scoped). `let` nie jest zmienną zasięgu funkcji, ale zasięgu bloku (block-scoped). Blok jest zdefiniowany przez dwie klamry `{ }`. 

```js
function doingStuff() {
    if (true) {
        var x = "local";
    }
    console.log(x);
}
doingStuff();

//local
```

W przypadku odwoływania się do zmiennej, która nie została jeszcze zadeklarowana:
`let` zwróci `ReferenceError` a `var` zwróci `undefined`

```js
function doingStuff() {
    if (true) {
        console.log(x);
        var x = "local";
    }
}
doingStuff();
```

Dzieje się tak z powodu zjawiska zwanego "hoisting" (podnoszenie), co oznacza, że używanie zmiennej `var` przed jej zadeklarowaniem skutkuje zmienną o wartości `undefined`, zamiast błędu `ReferenceError`.

`const` też jest zmienną zasięgu bloku (block-scoped). Używanie zmiennej `const` przed jej zadeklarowaniem skutkuje  błędem `ReferenceError`.




#### Zmienne globalne w funkcjach

Zmienne globalne to zmienne zadeklarowane poza funkcją i nie w jakimś innym bloku kodu. Zmienne są dostępne w zakresie (funkcji lub bloku), w którym są zdefiniowane, oraz w każdym „niższym” zakresie. Tak więc zmienna zdefiniowana poza funkcją jest dostępna zarówno w funkcji, jak i wewnątrz każdej funkcji lub innych bloków kodu w tej funkcji. Zmienna zdefiniowana na najwyższym poziomie twojego programu jest dostępna wszędzie w twoim programie. Ta koncepcja nazywa się zmienną globalną.


Można ukryć ich dostępność wewnątrz funkcji, definiując nową zmienną o tej samej nazwie w tym zakresie (można to zrobić dla `let`, `var` i `const`). To nie zmienia wartości zmiennej `const`, bo tworzymy nową zmienną `const`, która nadpisuje pierwszą w wewnętrznym zakresie. To samo dotyczy nazw parametrów.

```js
let x = "global";

function doingStuff() {
    let x = "local";
    console.log(x);
}
doingStuff();
console.log(x);

//local 
//global
```

Należy na to uważać i raczej unikać stosowania, ponieważ zmienne lokalne nadpisują wartość zmiennych globalnych i podczas tworzenia dużych aplikacji może to być problematyczne.


Uwaga: co jeżeli nie użyjemy słowa `let` lub `var`?

```js
function confuseReader() {
    x = "Guess my scope...";
    console.log("Inside the function:", x);
}
confuseReader();
console.log("Outside of function:", x);

///Inside the function: Guess my scope...
//Outside of function: Guess my scope...

```

`x` w funkcji zostaje zdefiniowana bez użycia słowa kluczowego `let` lub `var`. Załóżmy, że nie ma deklaracji `x` powyżej. JavaScript nie widzi `let` ani `var` i wtedy decyduje: „to musi być zmienna globalna”. Nawet jeśli zostanie zdefiniowana wewnątrz funkcji, deklaracja `x` w funkcji uzyskuje zakres globalny i nadal może być dostępna poza funkcją. Należy podkreślić, że jest to zła praktyka. Jeśli potrzebujemy zmiennej globalnej, deklarujemy ją na początku pliku.



### Natychmiastowe wywoływanie funkcji

Immediately Invoked Function Expression (IIFE) - to sposób wyrażania funkcji tak, aby została natychmiast wywołana. Jest anonimowa, nie ma nazwy i wykonuje się sama. Może to być przydatne, gdy do zainicjowania czegoś za pomocą tej funkcji. Jest również używana w wielu wzorcach projektowych, na przykład do tworzenia zmiennych i funkcji prywatnych i publicznych.

```js
(function () {
    console.log("IIFE!");
})();
```

IIFE ma wpływ na dostępność funkcji i zmiennych. Jeśli IIFE jest w najwyższym zakresie (top-level scope), cokolwiek jest w niej zawarte, nie jest dostępne z zewnątrz, mimo że jest na najwyższym poziomie. Jeśli funkcja wymagałaby parametru, należy wpisac go wewnątrz tych końcowych nawiasów.

```js
(() => {
    console.log("run right away");
})();
```




### Funkcje rekurencyjne

W niektórych przypadkach chcemy wywołać tę samą funkcję wewnątrz funkcji. Funkcje rekurencyjne mogą być świetne w pewnych kontekstach. Kiedy czujesz potrzebę wywoływania tej samej funkcji wielokrotnie w pętli, powinieneś rozważyć rekurencję. Przykładem może być również wyszukiwanie czegoś. Zamiast przeglądać wszystko w tej samej funkcji, możesz podzielić to wewnątrz funkcji i wielokrotnie wywoływać funkcję z wnętrza. Należy jednak pamiętać, że ogólnie wydajność rekurencji jest nieco gorsza niż wydajność regularnej iteracji przy użyciu pętli.

```js
function logRecursive(nr) {
    console.log("Started function:", nr);
    if (nr > 0) {
        logRecursive(nr - 1);
    } else {
        console.log("done with recursion");
    }
    console.log("Ended function:", nr);
}
logRecursive(3);

//Started function: 3
//Started function: 2
//Started function: 1
//Started function: 0
//done with recursion
//Ended function: 0
//Ended function: 1
//Ended function: 2
//Ended function: 3
```



### Funkcje zagnieżdżone

Podobnie jak w przypadku pętli, instrukcji if i wszystkich innych bloków konstrukcyjnych, możemy mieć funkcje wewnątrz funkcji. Jak widać, funkcja zewnętrzna wywołuje swoją zagnieżdżoną funkcję. Ta zagnieżdżona funkcja ma dostęp do zmiennych funkcji nadrzędnej. W odwrotną stronę to nie działa. Zmienne zdefiniowane wewnątrz funkcji wewnętrznej mają zasięg funkcji.



### Funkcje anonimowe

Możemy tworzyć funkcje bez nazw, jeśli przechowujemy je w zmiennych. Nazywamy te funkcje anonimowymi.

```js
function () {
    console.log("Not so secret though.");
};
```

Jak wywołać taką funkcję? Właściwie, nie można jej wywołać bez przechowywania w zmiennej. Anonimową funkcję można wywołać używając nazwy zmiennej, w ten sposób:

```js
let functionVariable = function () {
    console.log("Not so secret though.");
};
functionVariable();
//Not so secret though.
```

Przechowywanie funkcji w zmiennych umożliwia nam robienie bardzo ciekawych rzeczy, takich jak przekazywanie funkcji jako parametrów. Ta koncepcja dodaje kolejną warstwę abstrakcji do kodowania.



### Callbacks

Callback to funkcja, która jest przekazywana jako argument do innej funkcji i jest wywoływana (lub "zwracana") w późniejszym czasie, aby wykonać pewne działanie. Callbacki są często używane do obsługi asynchronicznych operacji, takich jak wczytywanie danych, oczekiwanie na zdarzenia lub inne operacje, które wymagają czasu.

```js
function greet(name, callback) {
    console.log("Hello, " + name + "!");
    callback();
}

function sayGoodbye() {
    console.log("Goodbye!");
}

// Wywołanie funkcji greet z callbackiem
greet("Alice", sayGoodbye);

//Hello, Alice! 
//Goodbye!
```



### References:
Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



