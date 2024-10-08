
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-08-06

---

**KLUCZOWE INFORMACJE W ROZDZIALE 8:**
	• Global JavaScript methods 
	• String methods 
	• Math methods 
	• Date methods
	• Array methods 
	• Number methods


Wbudowane metody to funkcjonalność, którą dostajemy od razu w JavaScript. Możemy używać tych metod bez potrzeby ich wcześniejszego kodowania. Wiele wbudowanych metod należy również do wbudowanych klas. Te klasy i ich metody można używać w dowolnym momencie, ponieważ JavaScript już je zdefiniował. Te klasy istnieją dla naszej wygody, ponieważ są bardzo powszechne, takie jak klasy `Date`, `Array` i `Object`. Możliwość wykorzystania możliwości już wbudowanych w JavaScript może poprawić skuteczność kodu, zaoszczędzić czas i zgodnie z różnymi najlepszymi praktykami rozwijania rozwiązań.



### Wprowadzenie do wbudowanych metod JavaScript

Różnica między metodą a funkcją polega na tym, że funkcja jest definiowana w dowolnym miejscu w skrypcie, a metoda jest definiowana wewnątrz klasy. Tak więc metody są praktycznie funkcjami w klasach i instancjach. Metody mogą być również często łańcuchowane; dotyczy to tylko metod zwracających wynik.


### Global methods

Globalne metody JavaScript mogą być używane bez odniesienia do wbudowanego obiektu, do którego należą. Oznacza to, że możemy po prostu użyć nazwy metody, jakby była funkcją zdefiniowaną w zakresie, w którym się znajdujemy, bez "obiektu" przed nią. Na przykład:

```js
let x = 7;
//zamiast pisać:
console.log(Number.isNaN(x));
//można napisać:
console.log(isNaN(x));
```


### Dekodowanie i kodowanie URI

Czasami trzeba zakodować lub zdekodować ciąg znaków. Kodowanie to przekształcanie z jednej formy na inną. W tym przypadku będziemy zajmować się kodowaniem procentowym, zwanym także kodowaniem URL.


**URI (uniform resource identifier)** to identyfikator określonego zasobu. 
**URL (uniform resource locator)** to podkategoria URI, która nie tylko jest identyfikatorem, ale także zawiera informacje o tym, jak uzyskać do niego dostęp (lokalizacja).

Przykład, kiedy będziesz tego potrzebować, to wysyłanie zmiennych przez URL za pomocą metody GET w formularzu. Te zmienne, które wysyłasz przez URL, nazywane są parametrami zapytania.

Jeśli coś zawiera spację, zostanie to zakodowane, ponieważ nie można używać spacji w URL. Zostaną one przekształcone na %20. URL może wyglądać na przykład tak: `www.example.com/submit?name=maaike%20van%20putten&love=coding`

Wszystkie znaki mogą zostać przekształcone na pewien format zaczynający się od %, jednak w większości przypadków nie jest to konieczne. URI mogą zawierać określoną liczbę znaków alfanumerycznych. Specjalne znaki muszą być zakodowane. Przykład przed kodowaniem to: `https://www.example.com/submit?name=maaike van putten`
Ten sam URL po zakodowaniu wygląda następująco: 
`https://www.example.com/submit?name=maaike%20van%20putten`


### <span style="color: #ffc425;">decodeUri(), encodeUri()</span>

Metody `decodeURI()` i `encodeURI()` faktycznie nie kodują i nie dekodują, lecz bardziej naprawiają uszkodzone URI. 

Metoda `encodeURI()` jest używana do kodowania (escapowania) całego Uniform Resource Identifier (URI). Zamienia znaki, które mają specjalne znaczenie w URI, na ich odpowiedniki kodowane w formacie UTF-8. Dzięki temu URI może być bezpiecznie przesyłane w zapytaniach sieciowych. 
Nie koduje znaków takich jak `:`, `/`, `;`, `?`, `&`, `=` itp., które mają specjalne znaczenie w URI. Zastosowanie to: kodowanie całych URI, aby były zgodne ze standardami URL oraz zapobieganie błędom podczas przesyłania URL zawierających spacje lub inne specjalne znaki.

Metoda `decodeURI()` jest używana do dekodowania (deskalowania) zakodowanego Uniform Resource Identifier (URI). Zamienia kodowane sekwencje UTF-8 z powrotem na ich oryginalne znaki.

```js
let uri = "https://www.example.com/submit?name=maaike van putten";
let encoded_uri = encodeURI(uri);
console.log("Encoded:", encoded_uri);
//Encoded: https://www.example.com/submit?name=maaike%20van%20putten

let decoded_uri = decodeURI(encoded_uri);
console.log("Decoded:", decoded_uri);
//Decoded: https://www.example.com/submit?name=maaike van putten
```

Jak widać, w wersji zakodowanej zastąpiło spacje, a w wersji zdekodowanej usunęło je ponownie.

>[!WARNING]
>Metody `decodeURI()` i `encodeURI()` mogą być bardzo przydatne do naprawiania uszkodzonych URI, ale są bezużyteczne, gdy chcesz zakodować lub zdekodować ciąg znaków zawierający znak o specjalnym znaczeniu, taki jak `/ , ? : @ & = + $ #`.

### decodeUriComponent(),  encodeUriComponent()

Metoda `encodeURIComponent()` służy do kodowania (escapowania) poszczególnych składników URI, takich jak parametry zapytania. Zamienia znaki, które mają specjalne znaczenie w URI, oraz wszystkie inne znaki, które nie są alfanumeryczne, na ich odpowiedniki kodowane w formacie UTF-8. Koduje więcej znaków niż `encodeURI()`, w tym znaki takie jak `/`, `?`, `:`, `@`, `=`, `&`, `#`.

Metoda `decodeURIComponent()` jest używana do dekodowania (deskalowania) zakodowanych składników URI. Zamienia kodowane sekwencje UTF-8 z powrotem na ich oryginalne znaki. Dekoduje tylko zakodowane składniki, które były kodowane przez `encodeURIComponent()`.


### escape(), unescape()

Są to nadal dostępne globalne metody do zrobienia czegoś podobnego do kodowania (escape) i dekodowania (unescape). Obie metody są zdecydowanie odradzane do użycia i mogą faktycznie zniknąć z przyszłych wersji JavaScript lub nie być obsługiwane przez przeglądarki z ważnych powodów.



## <span style="color: #00aedb;">Parsing numbers</span>

### parseInt()

Zmienia ciąg znaków na liczbę całkowitą. Ta metoda jest częścią klasy `Number`.

```js
let str_int = "6";
let int_int = parseInt(str_int);
console.log("Type of ", int_int, "is", typeof int_int);
```

Co w przypadku floats lub binary numbers? Metoda `parseInt()`przestaje parsować, gdy napotka nienumeryczny znak. To jest określone zachowanie, o którym należy pamiętać, pracując z `parseInt()`. W pierwszym przypadku przestaje parsować, gdy tylko znajdzie kropkę, więc wynik to 7. A w przypadku liczby binarnej przestaje parsować, gdy napotka `b`, więc wynik to 0.

```js
let str_float = "7.6";
let int_float = parseInt(str_float);
// 7

let str_binary = "0b101";
let int_binary = parseInt(str_binary);
// 0

let str_nan = "hello!"; 
let int_nan = parseInt(str_nan);
//NaN
```

### parseFloat()

Przekształcić ciąg znaków na liczbę zmiennoprzecinkową. Działa dokładnie tak samo jak parseInt(), z tym że potrafi również zrozumieć liczby dziesiętne i nie przestaje parsować, gdy napotka pierwszą kropkę. Należy również zauważyć, że nie doda `.0` do liczb całkowitych, więc 6 nie stanie się 6.0. Ostatnia uwaga, zachowanie dla liczb binarnych i ciągów jest takie samo. Przestanie parsować, gdy tylko napotka znak, którego nie może zinterpretować.

```js
let str_float = "7.6"; 
let float_float = parseFloat(str_float);
//7.6

let str_version_nr = "2.3.4"; 
let float_version_nr = parseFloat(str_version_nr);
//2.3

let str_int = "6"; 
let float_int = parseFloat(str_int);
//6
```


## Wykonywanie JavaScript z eval() !!!

Ta globalna metoda wykonuje argument jako instrukcję JavaScript. Oznacza to, że wykona cokolwiek, co zostanie wstawione do niej jako JavaScript, tak jakby ten kod JavaScript został napisany bezpośrednio w miejscu użycia `eval()`. Pozwala to na dynamiczne uruchamianie kodu w czasie wykonywania programu.

```html
<html>
  <body>
    <input onchange="go(this)"></input>
    <script>
      function go(e) {
        eval(e.value);
      }
    </script>
  </body>
</html>
```

- `eval()` jest potencjalnie niebezpieczne, ponieważ wykonuje dowolny kod, który mu przekażesz. Może to prowadzić do poważnych luk bezpieczeństwa, zwłaszcza jeśli kod pochodzi z niezaufanego źródła!!!
- Oprócz ryzyka bezpieczeństwa, ma też strasznie słabą wydajność. Z tego powodu już teraz możesz unikać jego użycia.
```js
let userInput = 'alert("Złośliwy kod")';
eval(userInput); // Może uruchomić złośliwy kod
```



## Array methods

### forEach()

Wykonuje podaną funkcję raz na każdy element tablicy.

```js
let arr = ["grapefruit", 4, "hello", 5.6, true];

function printStuff(element, index) {
  console.log("Printing stuff:", element, "on array position:", index);
}
arr.forEach(printStuff);

//Printing stuff: grapefruit on array position: 0
//Printing stuff: 4 on array position: 1
//Printing stuff: hello on array position: 2
//Printing stuff: 5.6 on array position: 3
//Printing stuff: true on array position: 4
```

### filter()

Tworzy nową tablicę z wszystkimi elementami, które przejdą test zaimplementowany przez podaną funkcję.

```js
let arr = ["squirrel", 5, "Tjed", new Date(), true];

function checkString(element, index) {
  return typeof element === "string";
}

let filterArr = arr.filter(checkString);
console.log(filterArr);

//[ 'squirrel', 'Tjed' ]
```

### every()

Metoda `every()` testuje, czy wszystkie elementy w tablicy przechodzą test implementowany przez dostarczoną funkcję. Zwraca `true`, jeśli funkcja testująca zwraca `true` dla każdego elementu, w przeciwnym razie zwraca `false`.

```js
console.log(arr.every(checkString));
```

### copyWithin()

Metoda `copyWithin()` służy do kopiowania części tablicy w inne miejsce w tej samej tablicy, bez zmiany jej rozmiaru. Nadpisuje istniejące elementy od docelowej pozycji.

```js
array.copyWithin(target, start, end)
```
- `target`: Indeks, od którego zacznie się wstawianie skopiowanych elementów.
- `start` (opcjonalne): Indeks, od którego zaczyna się kopiowanie elementów (domyślnie 0).
- `end` (opcjonalne): Indeks, na którym kończy się kopiowanie elementów (domyślnie `array.length`). Ten ostatni indeks nie jest wliczony.

```js
let arr = ["grapefruit", 4, "hello", 5.6, true];
arr.copyWithin(0, 3, 4);

//[ 5.6, 4, 'hello', 5.6, true ]

let arr = [1, 2, 3, 4, 5];
arr.copyWithin(0, 3, 5);
console.log(arr); 
// [4, 5, 3, 4, 5]

```

### map()

Ta metoda zwróci nową tablicę ze zmienionymi, nowymi wartościami. Za pomocą funkcji strzałkowej należy określić w jaki sposób wartości mają być zmodyfikowane. Będzie ona wykonywana dla każdego elementu w tablicy.

```js
let arr = [1, 2, 3, 4];
let mapped_arr = arr.map(x => x + 1);
console.log(mapped_arr);

//[ 2, 3, 4, 5 ]
```

### indexOf(), lastIndexOf()

Możemy znaleźć wystąpienia elementu za pomocą `indexOf()`. Aby znaleźć ostatnie wystąpienie, możemy użyć metody `lastIndexOf()` na tablicy, tak jak robiliśmy to dla ciągów znaków. Gdy zapytamy o ostatni indeks czegoś, czego nie ma w tablicy otrzymamy `-1`.





## String methods

### concat()

Metoda`concat()` łączy ciągi znaków. Nie zmienia ona oryginalnego ciągu (ciągów); zwraca połączony wynik jako ciąg znaków. Trzeba przechwycić wynik w nowej zmiennej, w przeciwnym razie zostanie on utracony.

```js
let s1 = "Hello ";
let s2 = "JavaScript";
let result = s1.concat(s2);
console.log(result);
//Hello JavaScript
```

### split()

Za pomocą metody `split()` możemy przekształcić ciąg znaków na tablicę. Ponownie, musimy przechwycić wynik; nie zmienia ona oryginalnego ciągu. Użyjmy poprzedniego wyniku zawierającego `Hello JavaScript`. Musimy określić, na jakim znaku metoda `split` ma rozdzielić ciąg. Za każdym razem, gdy napotka ten znak, utworzy nowy element tablicy.

```js
let result = "Hello JavaScript";
let arr_result = result.split(" ");
console.log(arr_result);
//[ 'Hello', 'JavaScript' ]
```

### join()

Za pomocą metody `join()` można przekształcić tablicę na ciąg znaków.

```js
let letters = ["a", "b", "c"];
let x = letters.join();
console.log(x);
//a,b,c
```

Typ `x` to `string`. Jeśli chcemy połączyć innym separatorem możemy to określić w ten sposób:

```js
let letters = ["a", "b", "c"];
let x = letters.join('-');
console.log(x);
//a-b-c
```

### indexOf()

Działa tak samo jak w tablicach, możemy znaleźć wystąpienia elementu za pomocą `indexOf()`.  Gdy brak wystąpienia zwraca `-1`.

```js
let poem = "Roses are red, violets are blue, if I can do JS, then you can too!";
let index_re = poem.indexOf("re");
console.log(index_re);
//7
```

### search()
Alternatywnym sposobem wyszukiwania określonego podciągu w ciągu znaków jest użycie metody `search()`. Podobnie jak `indexOf()`, jeśli nie może znaleźć wyniku, zwróci `-1`.

```js
let searchStr = "When I see my fellow, I say hello";
let pos = searchStr.search("lo");
console.log(pos);
//17
```

`search()` przyjmuje format regex jako wejście, podczas gdy `indexOf()` przyjmuje tylko ciąg znaków. `indexOf()` jest szybszy niż metoda `search()`, więc jeśli tylko potrzebujesz wyszukać ciąg znaków, użyj `indexOf()`. Jeśli musisz wyszukać wzorzec ciągu, będziesz musiał użyć metody `search()`.

### charAt(index)

Wskazuje jaki znak znajduje się na określonej pozycji indeksu. Gdzie określona pozycja indeksu jest argumentem. Jeśli zapytamy o pozycję indeksu, która jest poza zakresem ciągu znaków, zwróci pusty ciąg.

```js
let pos1 = poem.charAt(10);
console.log(pos1);
//r
```



## Tworzenie podciągów

### slice(start, end)

Za pomocą metody `slice(start, end)` możemy tworzyć podciągi. Nie zmienia ona oryginalnego ciągu, ale zwraca nowy ciąg z podciągiem. Przyjmuje dwa parametry: pierwszy to indeks, od którego zaczyna, a drugi to indeks końcowy. Jeśli pominiesz drugi indeks, metoda będzie kontynuować do końca ciągu od startu. Indeks końcowy nie jest włączony do podciągu.

```js
let str = "Create a substring";
let substr1 = str.slice(5);
let substr2 = str.slice(0, 3);
console.log("1:", substr1);
console.log("2:", substr2);
//1: e a substring
//2: Cre

```

### replace(old, new)

Metoda przyjmuje dwa argumenty: jeden ciąg do wyszukania w ciągu i nową wartość do zastąpienia starej wartości. Jeśli nie przechwycisz wyniku, zostanie on utracony, ponieważ oryginalny ciąg nie zostanie zmieniony. Uwaga, metoda domyślnie zmienia tylko pierwsze wystąpienie.

```js
let hi = "Hi buddy buddy";
let new_hi = hi.replace("buddy", "Pascal");
console.log(new_hi);
//`Hi Pascal buddy`
```


### replaceAll()

Zastąpi to wszystkie wystąpienia określonym nowym ciągiem.

```js
let s3 = "hello hello";
let new_s3 = s3.replaceAll("hello", "oh");
console.log(new_s3);
//`oh oh`
```



## Uppercase and lowercase

### toUpperCase(), toLowerCase()


```js
let caps = "HI HOW ARE YOU?";
let fixed_caps = caps.toLowerCase();
let first_capital = fixed_caps.charAt(0).toUpperCase().concat(fixed_caps.slice(1));
console.log(first_capital);
//// Hi how are you?
```



## Początek i koniec ciągu

### startsWith(), endsWith()

Wypisuje `true` lub `false` w zależności od tego czym zaczyna się lub kończy ciąg znaków. Uwaga, metoda jest wrażliwa na wielkości liter.
```js
let encouragement = "You are doing great, keep up the good work!";
let bool_start = encouragement.startsWith("You");
console.log(bool_start);
//true
```



## Number methods
### isNaN()

Ta funkcja sprawdza, czy wartość nie jest liczbą i zwraca `true`, jeśli wartość to NaN, a `false` w przeciwnym razie.

```js
let x = 34;
console.log(isNaN(x));     // false, ponieważ 34 jest liczbą
console.log(!isNaN(x));    // true, ponieważ 34 jest liczbą i negowanie false daje true

let str = "hi";
console.log(isNaN(str));   // true, ponieważ "hi" nie jest liczbą
let str1 = "5";
console.log(isNaN(str1));  // false, ponieważ "5" może być konwertowane na liczbę 5

```

### isFinite()

Metoda, która sprawdza, czy coś jest skończone. Zwraca ona `false` dla `NaN`, `Infinity` i `undefined`, a `true` dla wszystkich innych wartości.

```js
let x = 3;
let str = "finite";
console.log(isFinite(x));   //true
console.log(isFinite(str));   //false
console.log(isFinite(Infinity));   //false
console.log(isFinite(10 / 0));   //false
```

Ciąg znaków nie jest liczbą, a zatem nie jest skończony.

### isInteger()

W przeciwieństwie do `isNaN()` i `isFinite()`, `isInteger()` nie została przekształcona w metodę globalną i musimy odwołać się do obiektu Number, aby jej użyć. Robi dokładnie to, czego można by się spodziewać: zwraca `true`, jeśli wartość jest liczbą całkowitą, i `false`, gdy nie jest.

```js
let x = 3;
let str = "integer";
console.log(Number.isInteger(x));   //true
console.log(Number.isInteger(str));   //false
console.log(Number.isInteger(Infinity));   //false
console.log(Number.isInteger(2.4));   //false
```

### toFixed()

Określanie liczby miejsc po przecinku. Różni się ona od metod zaokrąglania w klasie `Math`, ponieważ tutaj możemy określić liczbę miejsc po przecinku. Nie zmienia to oryginalnej wartości, więc musimy przechować wynik w innej zmiennej.

```js
let x = 1.23456;
let newX = x.toFixed(3);   //1.235
```

### toPrecision()

Pozwala określić całkowitą liczbę cyfr do rozważenia. Oznacza to, że JavaScript bierze pod uwagę całkowitą liczbę cyfr, wliczając w to te przed kropką.

```js
let x = 1.23456;
let newX = x.toPrecision(4);
console.log(newX);   //1.235
```




## Math methods

### max(), min()

Znajdowanie najwyższej lub najniższej liczby wśród argumentów.

```js
let highest = Math.max(2, 56, 12, 1, 233, 4);
console.log(highest);   //233
console.log(lowest);   //1

let highestOfWords = Math.max("hi", 3, "bye");
console.log(highestOfWords);   //NaN

```

### sqrt()

Jest używana do obliczania pierwiastka kwadratowego z danej liczby

```js
let result = Math.sqrt(64);
console.log(result);   //8
```

### pow(base, exponent)

Pozwala podnieść liczbę do określonej potęgi (podstawapotęga, na przykład 2^3).

```js
let result2 = Math.pow(5, 3);
console.log(result2);   //5^3, czyli 5*5*5, czyli 125
```

### round()

Zaokrągla liczbę.

```js
let x = 6.78;
let y = 5.34;
console.log(Math.round(x));   //7
console.log(Math.round(y));   //5
```

### ceil(), floor()

Metoda `ceil()` zawsze zaokrągla w górę do pierwszej napotkanej liczby całkowitej. Uwaga na liczby ujemne, ponieważ -5 jest większe niż -6.
Metoda `floor()` zaokrągla w dół.

```js
let negativeX = -x;
let negativeY = -y;
console.log(Math.ceil(negativeX));   //-6
console.log(Math.ceil(negativeY));   //-5
```

### trunc()

Daje ten sam wynik co `floor()` dla liczb dodatnich, ale dochodzi do tych wyników inaczej. Nie zaokrągla w dół, po prostu zwraca tylko część całkowitą. Kiedy używamy liczb ujemnych dla `trunc()`, widzimy różnicę.





## Date methods
### now()

Wbudowana metoda, która zwraca bieżącą datę i czas.

```js
let now2 = Date.now();
console.log(now2);   //1622902938507
```

To wypisze bieżący czas, reprezentowany w milisekundach od 1 stycznia 1970 roku. Jest to arbitralna data reprezentująca epokę Uniksa.

Można także określić konkretną datę za pomocą konstruktora:

```js
let specificDate = new Date(2022, 1, 10, 12, 10, 15, 100);
console.log(specificDate);   /2022-02-10T12:10:15.100Z
```

Uwaga na bardzo ważny szczegół: drugi parametr to miesiąc. `0` oznacza styczeń, a `11` oznacza grudzień.

Za pomocą `get` i `set` możemy pobierać i ustawiać określone części dat.

```js
let d = new Date();
console.log("Dzień tygodnia:", d.getDay());
console.log("Dzień miesiąca:", d.getDate());
console.log("Miesiąc:", d.getMonth());
console.log("Rok:", d.getFullYear());
console.log("Sekundy:", d.getSeconds());
console.log("Milisekundy:", d.getMilliseconds());
console.log("Czas:", d.getTime());

let d = new Date();
d.setFullYear(2010);
d.setMonth(0); // styczeń
d.setDate(15);
d.setHours(10);
d.setMinutes(30);
d.setSeconds(45);
d.setTime(1622889770682);
```

Jeżeli chodzi o obsługę wartości poza zakresem, to wywołując `setHours()` z liczbą większą niż 24, godziny zostaną przewinięte do następnej daty (1 na każde 24 godziny) i po użyciu operatora modulo, reszta z `hours % 24` będzie nową wartością godzin. Ten sam proces dotyczy minut, sekund i milisekund.

### parse()

Pozwala parsować daty epoki (epoch dates) z ciągów znaków. Dane wejściowe dla `parse` to formaty ISO dat. Wiele formatów może być sparsowanych na ciąg znaków.

```js
let d1 = Date.parse("June 5, 2021");
console.log(d1);   //1622851200000
```

### Konwertowanie daty na ciąg znaków

Możemy również konwertować daty z powrotem na ciągi znaków. Na przykład za pomocą tych metod:

`console.log(d.toDateString());`

Oto kilka innych metod do konwersji daty na ciąg znaków:

- `toDateString()`: Zwraca część daty w czytelnym formacie (bez godziny).
- `toTimeString()`: Zwraca część czasu w czytelnym formacie.
- `toISOString()`: Zwraca datę w formacie ISO.
- `toUTCString()`: Zwraca datę w formacie UTC.
- `toLocaleDateString()`: Zwraca część daty zgodnie z ustawieniami lokalnymi.
- `toLocaleTimeString()`: Zwraca część czasu zgodnie z ustawieniami lokalnymi.


### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



