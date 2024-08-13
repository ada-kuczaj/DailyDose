
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-08-13

---

**KLUCZOWE INFORMACJE W ROZDZIALE 10:**
	 • Podstawowe poruszanie się po DOM
	 • Dostęp do elementów w DOM
	 • Obsługa kliknięcia elementu
	 • This i DOM
	 • Manipulowanie stylem elementu
	 • Zmiana klas elementu
	 • Manipulowanie atrybutami
	 • Nasłuchiwacze zdarzeń na elementach
	 • Tworzenie nowych elementów

### <span style="color: #d11141;">Podstawowe poruszanie się po DOM</span>

Możemy poruszać się po DOM, używając obiektu document. Ten obiekt document zawiera cały HTML i jest reprezentacją strony internetowej. Przemierzanie tych elementów może doprowadzić  do elementu, który chcesz manipulować. 

Przykład:
```html
<!DOCTYPE html>
<html>
<body>
    <h1>Znajdźmy skarb</h1>
    <div id="forest">
        <div id="tree1">
            <div id="squirrel"></div>
            <div id="flower"></div>
        </div>
        <div id="tree2">
            <div id="shrubbery">
                <div id="treasure"></div>
            </div>
            <div id="mushroom">
                <div id="bug"></div>
            </div>
        </div>
    </div>
</body>
</html>
```

Chcemy znaleźć skarb.
**==SPOSÓB I (właściwości children):==**
Zaczynamy od użycia właściwości body z obiektu document. Zawiera ona wszystko, co jest wewnątrz elementu body. Aby dotrzeć do skarbu za pomocą children, wpisujemy:
```js
console.dir(document.body);
console.dir(document.body.children.forest.children.tree2.children.shrubbery.children.treasure);
```
Jak widać, na każdym wybranym elemencie musimy ponownie wybrać children.


**==SPOSÓB II (właściwości childNodes):==**
Aby dotrzeć do skarbu za pomocą childNodes, trzeba często korzystać z konsoli, ponieważ znajdują się tam również węzły tekstowe i komentarze. childNodes jest tablicą, więc trzeba wybrać odpowiedni indeks, aby wybrać odpowiednie dziecko. Jest tu jedna zaleta: jest to znacznie krótsze, ponieważ nie trzeba wybierać nazwy osobno.
```js
console.dir(document.body.childNodes[3].childNodes[3].childNodes[1].childNodes[1]);
```
childNodes jest bardziej kompletnym terminem niż children. Children zawiera tylko wszystkie elementy HTML, więc są to w rzeczywistości węzły. childNodes zawiera również węzły tekstowe i komentarze. Za pomocą children możesz jednak używać ID, dlatego są łatwiejsze w użyciu.

**==SPOSÓB III (poruszanie się w górę - parentElement):==**
Możemy również poruszać się po DOM w górę. Każdy element zna swojego rodzica. Możemy użyć właściwości `parentElement`, aby wrócić na górę.
```js
document.body.children.forest.children.tree2.parentElement;
```
Może to okazać się bardzo przydatne, zwłaszcza w połączeniu z funkcjami takimi jak `getElementById()`.

**==SPOSÓB IV (poruszanie się w bok - nextElementSibling):==**
```js
document.body.children.forest.children.tree2;
document.body.children.forest.children.tree2.previousElementSibling; //do tree1
document.body.children.forest.children.tree1.nextElementSibling; //do tree2
```
Alternatywnie do `nextElementSibling`, który zwraca następny węzeł będący elementem, można użyć `nextSibling`, który zwraca następny węzeł dowolnego typu.


#### Wybieranie elementów jako obiektów

Gdy wiadomo, jak poruszać się po DOM, można dokonywać zmian w elementach. Zamiast używać `console.dir()`, trzeba wpisać ścieżkę do elementu, który chcemy zmienić. Teraz mamy element jako obiekt JavaScript, i możemy dokonywać zmian we wszystkich jego właściwościach.


#### Zmiana `innerText`
Właściwość `innerText` skupia się na tekście pomiędzy otwierającym a zamykającym elementem.
```js
document.body.children.greeting.innerText = "Do widzenia!";
```
`innerText` zwraca zawartość elementu jako zwykły tekst, co nie stanowi problemu w tym przypadku, ponieważ jest tam tylko tekst. Jednak, jeśli wewnątrz elementu znajduje się jakikolwiek HTML, którego potrzebujesz, lub jeśli chcesz dodać HTML, nie możesz użyć tej metody. Będzie on interpretował HTML jako tekst i po prostu wyświetli go na ekranie. Więc jeśli wykonamy to:
```js
document.body.children.greeting.innerText = "<p>Do widzenia!</p>";
```
To wyświetli na ekranie `"<p>Do widzenia!</p>"`, z HTML-em wokół niego, tak jakby był to ciąg tekstowy. Aby obejść ten problem, musisz użyć `innerHTML`.


#### Zmiana `innerHTML`
Jeśli nie chcesz pracować tylko ze zwykłym tekstem, lub może chcesz określić jakieś formatowanie HTML dla swojej wartości, możesz użyć właściwości `innerHTML`. Ta właściwość nie przetwarza tylko zwykłego tekstu, ale może także zawierać wewnętrzne elementy HTML:
```js
document.body.children.greeting.innerHTML = "<b>Do widzenia!</b>";
```
To wyświetli `"Do widzenia!"` pogrubione na ekranie, uwzględniając element `b` zamiast po prostu drukować go jako ciąg tekstowy.



### <span style="color: #00b159;">Dostęp do elementów w DOM</span>

Istnieje wiele metod wybierania elementów z DOM. Po uzyskaniu elementów możemy je modyfikować. W kolejnych sekcjach omówimy, jak uzyskać elementy według ich ID, nazwy tagu, nazwy klasy oraz selektora CSS.

Zamiast przechodzić przez DOM krok po kroku, można używać wbudowanych metod, które mogą przeszukiwać DOM i zwracać elementy spełniające określone kryteria.

#### Uzyskiwanie dostępu do elementów po ID - `getElementById()`
Możemy pobrać elementy według ID za pomocą metody `getElementById()`. Ta metoda zwraca jeden element o określonym ID. ID powinny być unikalne, ponieważ z dokumentu HTML zwrócony zostanie tylko jeden wynik. Nie ma wielu reguł dotyczących poprawnych ID; nie mogą one zawierać spacji i muszą mieć co najmniej jeden znak. Podobnie jak w przypadku konwencji nazewnictwa zmiennych, najlepszą praktyką jest uczynienie ich opisowymi i unikanie znaków specjalnych.

```html
<!DOCTYPE html>
<html>
<body>
    <h1 style="color:pink;">Tylko przykład</h1>
    <div id="one" class="example">Cześć!</div>
    <div id="two" class="example">Cześć!</div>
    <div id="three" class="something">Cześć!</div>
</body>
<script>
    console.log(document.getElementById("two"));
</script>
</html>
```

Należy powtórzyć, że jeśli masz więcej niż jeden element z tym samym ID, zostanie zwrócony tylko pierwszy napotkany. Należy unikać tej sytuacji w swoim kodzie.


#### Dostęp do elementów po nazwie tagu -`getElementsByTagName()`

Jeśli poprosimy o elementy według nazwy tagu, otrzymamy wynik w postaci tablicy. Dzieje się tak, ponieważ może być więcej niż jeden element o tej samej nazwie tagu. Będzie to zbiór elementów HTML, czyli `HTMLCollection`, które jest specjalnym obiektem JavaScript. Jest to zasadniczo lista węzłów.
```js
document.getElementsByTagName("div");
```
Otrzymamy:
```js
HTMLCollection(3) [div#one.example, div#two.example, div#three.something, one: div#one.example, two: div#two.example, three: div#three.something]
```

Jak widać, wszystkie elementy w DOM z tagiem `div` są zwrócone. Można odczytać, jakie mają ID i klasy z tej składni. Pierwsze w zbiorze to obiekty: `div` to nazwa, `#` określa ID, a `.` określa klasę. Jeśli jest wiele kropek, oznacza to, że jest wiele klas. Następnie można zobaczyć elementy ponownie (`namedItems`), tym razem jako pary klucz-wartość z ich ID jako kluczem.

Możemy uzyskać do nich dostęp za pomocą metody `item()`, aby uzyskać dostęp do nich według indeksu, jak poniżej:
```js
document.getElementsByTagName("div").item(1);
```
Możemy również uzyskać do nich dostęp według nazwy, używając metody `namedItem()`, jak poniżej:
```js
document.getElementsByTagName("div").namedItem("one");
```



#### Dostęp do elementów po nazwie klasy -`getElementsByClassName()`

Jeśli uzyskamy elementy według nazwy klasy, zwrócony zostanie `HTMLCollection` zawierający wyniki.
```js
document.getElementsByClassName("example");
```
Otrzymamy:
```js
HTMLCollection(2) [div#one.example, div#two.example, one: div#one.example, two: div#two.example]
```


#### Dostęp do elementów za pomocą selektora CSS - `querySelector()`

Możemy także uzyskać dostęp do elementów, używając selektora CSS. Robimy to za pomocą metod `querySelector()` i `querySelectorAll()`. Następnie podajemy selektor CSS jako argument, a to przefiltruje elementy w dokumencie HTML i zwróci tylko te, które spełniają kryteria selektora CSS. Ta pierwsza opcja wybierze pierwszy element, który pasuje do zapytania. Druga opcja zwraca obiekt typu NodeList. Zawiera wszystkie węzły, które pasują do selektora CSS. Za pomocą metody `item()` możemy je pobierać według indeksu, tak jak to robiliśmy dla `HTMLCollection`.
```js
document.querySelector("div");
document.querySelector(".something");

document.querySelectorAll("div");
```
`querySelector()` pozwala na bardziej skomplikowane zapytania, a niektórzy deweloperzy twierdzą, że `getElementById()` jest bardziej czytelny. Inni twierdzą, że możesz używać `querySelector()` wszędzie dla spójności.



### <span style="color: #00aedb;">Obsługa kliknięcia elementu</span>


...





### <span style="color: #f37735">Nagłówek kolorowy test</span>

### <span style="color: #ffc425;">Nagłówek kolorowy test</span>


### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



