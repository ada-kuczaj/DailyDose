
--- 
tags: [[JS]]
date: 2024-07-24

---
**Casting in JavaScript** (często nazywane "konwersją typów") to proces przekształcania jednej wartości z jednego typu danych na inny. W przeciwieństwie do języków takich jak Java czy C++, JavaScript nie wymaga jawnego deklarowania typów danych. Zamiast tego, typy danych są dynamicznie przypisywane i mogą się zmieniać w czasie działania programu.

W JavaScript konwersje typów mogą zachodzić w sposób **jawny** (explicit) lub **niejawny** (implicit).

### **1. Niejawne rzutowanie (Implicit Type Casting)**

JavaScript automatycznie przekształca wartości do odpowiedniego typu w pewnych kontekstach, np. w wyrażeniach arytmetycznych lub porównaniach.

#### Przykłady:

- **Rzutowanie na ciąg znaków (string)**: Kiedy próbujesz łączyć stringi z innymi typami, JavaScript automatycznie konwertuje te inne typy na stringi.

```js
console.log('Hello ' + 123);  // Output: "Hello 123"
```

- **Rzutowanie na liczbę (number)**: Podczas operacji arytmetycznych, JavaScript spróbuje przekonwertować ciągi znaków na liczby.

```js
console.log('5' - 2);  // Output: 3 (ciąg "5" zostaje przekonwertowany na liczbę 5)
console.log('5' * 2);  // Output: 10
```

- **Porównania z rzutowaniem**: W porównaniach za pomocą `==`, JavaScript próbuje konwertować typy na odpowiedni format, aby porównać wartości. Nazywa się to "porównaniem równości bez ścisłego sprawdzenia typu".

```js
console.log(5 == '5');  // Output: true (wartości są porównywane po konwersji typu)
console.log(5 === '5'); // Output: false (sprawdzenie ścisłej równości, różne typy)
```



### 2. **Jawne rzutowanie (Explicit Type Casting)**


JavaScript umożliwia również ręczne przekształcanie typów danych. Najczęściej konwersje są przeprowadzane za pomocą wbudowanych funkcji.

#### Przykłady:

- **Na liczbę (Number)**: Do konwersji wartości na liczbę możemy użyć funkcji `Number()`, operatora `+`, lub parsowania ciągów znaków za pomocą `parseInt()` lub `parseFloat()`.

```js
let str = '123';
let num = Number(str);      // Output: 123
let num2 = +str;            // Output: 123
let parsed = parseInt(str); // Output: 123
let floatParsed = parseFloat('123.45'); // Output: 123.45
```

- **Na ciąg znaków (String)**: Możemy konwertować wartości na ciągi znaków za pomocą `String()` lub konkatenacji.

```js
let num = 123;
let str = String(num);       // Output: "123"
let str2 = num.toString();   // Output: "123"
```

- **Na typ logiczny (Boolean)**: Konwersja do wartości logicznych następuje za pomocą `Boolean()`. Wartości takie jak `0`, `null`, `undefined`, `NaN`, oraz pusty ciąg `""` są rzutowane na `false`, a wszystkie inne wartości są rzutowane na `true`.

```js
let truthy = Boolean(123);   // Output: true
let falsy = Boolean(0);      // Output: false
```


### **Ważne kwestie:**

**Falsy** i **truthy**: JavaScript uznaje niektóre wartości za "falsy" (fałszywe) w kontekście logicznym, czyli podczas rzutowania na `Boolean`, dają one wartość `false`. Są to:

- `false`
- `0`
- `""` (pusty string)
- `null`
- `undefined`
- `NaN`

Wszystkie inne wartości są uznawane za "truthy", czyli konwertują się na `true`.

#### **Konwersja liczb i ciągów znaków**: 
Operacje matematyczne, takie jak dodawanie (`+`), odejmowanie (`-`), mnożenie (`*`) i dzielenie (`/`), mogą prowadzić do nieoczekiwanych konwersji typów, szczególnie przy pracy z liczbami i stringami. Trzeba zachować ostrożność, szczególnie przy operatorze `+`, ponieważ jest on zarówno operatorem dodawania, jak i konkatenacji stringów.


#### **`parseInt()` i `parseFloat()`**

Funkcje `parseInt()` i `parseFloat()` są przydatne do konwertowania ciągów znaków na liczby, ale trzeba uważać na to, jak obsługują niepoprawne dane:

- `parseInt('123abc')` zwróci `123`, ponieważ ignoruje dalsze znaki po napotkaniu niecyfrowego znaku.
- `parseFloat('123.45abc')` zwróci `123.45`.

Natomiast `Number('123abc')` zwróci `NaN`, ponieważ oczekuje prawidłowej liczby w całości.



### References:

https://flaviocopes.com/javascript-casting/
---



