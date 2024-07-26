
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-07-23

---

**KLUCZOWE INFORMACJE W ROZDZIALE 2:**
	• Zmienne (Variables)
	• Prymitywne typy danych
	• Analizowanie i modyfikowanie typów danych
	• Operatory



### Zmienne (Variables)

```js
let firstname = "Maria"; 
firstname = "Jacky";
```

Tworząc zmienną trzeba ją zadeklarować za pomocą `let`, `var` lub `const`. Następnie tylko przypisujemy wartości.


`let` i `var` są używane do zmiennych, którym może zostać przypisana nowa wartość. Różnica między let i var jest złożona. Różnica polega w zakresie (`scope`). `var` ma zasięg globalny, a `let` ma zasięg blokowy.

Globalny zasięg var oznacza, że ​​można używać zmiennych zdefiniowanych za pomocą var w całym skrypcie. Zakres bloków oznacza, że ​​można używać tylko zmiennych zdefiniowanych za pomocą let w konkretnym bloku kodu, w którym zostały zdefiniowane. 

`const` jest używana w przypadku zmiennych, którym wartość jest przypisana tylko raz — na przykład wartość pi, która nie ulegnie zmianie. 

```js
let nr1 = 12; 
var nr2 = 8; 
const PI = 3.14159;
```


### Prymitywne typy danych

JavaScript jest językiem o luźnym typie. Oznacza to, że JavaScript określa typ na podstawie wartości.

JavaScript ma 7  prymitywnych typów danych: 
**String, Number, BigInt, Boolean, Symbol, undefined i null.** 

**Escape characters:**
```js
let str = "Hello, what's your name? Is it \"Mike\"?";
let str2 = 'Hello, what\'s your name? Is it "Mike"?';
let str3 = "New \nline."; 
let str4 = "I'm containing a backslash: \\!";
```


#### **Symbol**

Symbol to zupełnie nowy typ danych wprowadzony w ES6. Symbolu można użyć, gdy ważne jest, aby zmienne nie były równe, mimo że ich wartość i typ są takie same. Każdy symbol jest wyjątkowy, dlatego też, chociaż zawierają ten sam ciąg znaków, nie są takie same i przy porównaniu zwracają wartość `false`. Te typy danych symboli mogą być bardzo przydatne jako właściwości obiektów


```js
let str1 = "JavaScript is fun!"; 
let str2 = "JavaScript is fun!"; 
console.log("These two strings are the same:", str1 === str2); 

let sym1 = Symbol("JavaScript is fun!"); 
let sym2 = Symbol("JavaScript is fun!"); 
console.log("These two Symbols are the same:", sym1 === sym2); 

// Output:
These two strings are the same: true 
These two Symbols are the same: false
```

#### Undefined i null

`undefined` oznacza, że zmienna została zadeklarowana, ale nie została jej przypisana żadna wartość. Jest to również domyślna wartość zwracana przez funkcje, które nie mają zdefiniowanego `return`.

`null` jest explicytną wartością oznaczającą brak jakiejkolwiek wartości. Programiści używają `null`, aby celowo wskazać, że zmienna nie powinna mieć żadnej wartości.

`"Explicytna"` oznacza "wyraźna" lub "jawna". W kontekście programowania, gdy mówimy, że coś jest explicytne, oznacza to, że zostało jasno określone lub zdefiniowane przez programistę, zamiast być domyślnie przyjęte przez system.


### Analizowanie i modyfikowanie typów danych


```js
let str = "Hello";
let nr = 7; 
let bigNr = 12345678901234n; 
let bool = true; 
let sym = Symbol("unique"); 
let undef = undefined; 
let unknown = null;

console.log("str", typeof str); 
console.log("nr", typeof nr); 
console.log("bigNr", typeof bigNr); 
console.log("bool", typeof bool); 
console.log("sym", typeof sym); 
console.log("undef", typeof undef); 
console.log("unknown", typeof unknown);

//Output:
str string 
nr number 
bigNr bigint 
bool boolean
sym symbol 
undef undefined 
unknown object //!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
```

**Ciekawostka:**
Na wyjściu widać, że `typeof null` zwraca `obiekt`, podczas gdy w rzeczywistości null jest pierwotnym typem danych, a nie obiektem. Jest to błąd, który występuje od zawsze i obecnie nie można go usunąć ze względu na problemy z kompatybilnością wsteczną.


### Konwertowanie typów danych

Zmienne w JavaScript mogą zmieniać typy. Czasami JavaScript robi to automatycznie. Ale uwaga! W pierwszym przykładzie zamienił string na liczbę i wykonał mnożenie, ale w drugim zamienił liczbę na string i wykonał konkatenację.

```js
let nr1 = 2; 
let nr2 = "2"; 
console.log(nr1 * nr2);

//Output: 4
```

```js
let nr1 = 2; 
let nr2 = "2"; 
console.log(nr1 + nr2);

//Output: '22'
```

Dlatego korzystamy w metod konwersji:

 String()
 
 **Number()** - wszystko, czego nie można zinterpretować jako liczby poprzez proste usunięcie cudzysłowów, zostanie ocenione jako NaN. Pusty ciąg znaków i wartość null dadzą w wyniku liczbę 0.
 
**Boolean()** - tylko pusty ciąg znaków, null i undefined doprowadzi do wartości logicznej `false`.



### Operatory

1. Add: `+` concatenation
2. Subtract: `-`
3. Multiply: `*`
4. Divide: `/`
5. Modulus: `%`
6. Exponentiation `**`
7. Unary operators: increment `++` and decrement `--`
	- Prefix and postfix operators
8. Assignment operators `+=`, `-=`, `**=`
9. Comparison operators `==`, `===`, `!=`, `!==`
10. Greater than and smaller than `>`, `<`, `<=`
11. Logical operators `&&`, `||`, `!x` 



Operatory te można łączyć i działa to tak samo, jak w matematyce. Wykonywane są w określonej kolejności, niekoniecznie od lewej do prawej.

![[Pasted image 20240723220701.png]]



### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



