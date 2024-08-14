
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

Elementy HTML mogą wykonywać określone działania po kliknięciu. Dzieje się tak dlatego, że do elementu HTML można przypisać funkcję JavaScript. Za każdym razem, gdy klikniesz tekst w div, pojawi się wyskakujące okienko z tekstem "Ouch! Stop it!". 

```html
<!DOCTYPE html>
<html>
	<body>
		<script>
			function stop() {
				alert("Ouch! Stop it!");
			}
		</script>
		<div id="one" onclick="stop()">Nie klikaj tutaj!</div>
	</body>
</html>
```

Istnieje również sposób dodania obsługi kliknięcia za pomocą JavaScript. Wybieramy element HTML, do którego chcemy dodać obsługę kliknięcia, i łapiemy go po id. Jeśli chcemy dynamicznie dodać obsługę kliknięcia do elementu div, możemy wybrać go i określić właściwość za pomocą konsoli:

```js
document.getElementById("one").onclick = function () {
    alert("Auch! Stop!");
}
```



### <span style="color: #f37735">This i DOM</span>

Słowo kluczowe `this` zawsze ma względne znaczenie; zależy od dokładnego kontekstu, w którym się znajduje. W DOM specjalne słowo kluczowe `this` odnosi się do elementu DOM, do którego należy. Jeśli określimy `onclick`, aby wysłać `this` jako argument, przekaże ono element, w którym znajduje się `onclick`. Możemy uzyskać dostęp do rodzica this za pomocą funkcji w ten sposób:

```js
function reveal(el) {
    console.log(el.parentElement);
}
```

Możemy w ten sam sposób wyświetlić dowolną inną właściwość elementu; na przykład, `console.log(el.innerText);` Tak więc słowo kluczowe `this` odnosi się do elementu, a z tego elementu możemy przemieszczać się po DOM.



### <span style="color: #ffc425;">Manipulowanie stylem elementu</span>

Po wybraniu odpowiedniego elementu z DOM możemy zmienić przypisany do niego styl CSS. Możemy to zrobić, używając właściwości `style`. Oto, jak to zrobić:

1. Wybierz odpowiedni element z DOM.
2. Zmień odpowiednią właściwość wewnątrz właściwości `style` tego elementu.

```js
<!DOCTYPE html>
<html>
	<body>
		<script>
			function toggleDisplay(){
			    let p = document.getElementById("magic");
			    if(p.style.display === "none") {
			        p.style.display = "block";
			    } else {
			        p.style.display = "none";
			    }
			}
		</script>
		<p id="magic">Mogę zniknąć i pojawić się.</p>
		<button onclick="toggleDisplay()">Magia!</button>
	</body>
</html>
```



### <span style="color: #d11141;">Zmiana klas elementu</span>

Elementy HTML mogą mieć przypisane klasy i możemy wybierać elementy po nazwie klasy. Klasy są często używane do nadawania elementom określonego wyglądu za pomocą CSS. Dzięki JavaScript możemy zmieniać klasy elementów HTML, co może wywołać pewien wygląd związany z daną klasą w CSS. 

#### Dodawanie klas do elementów

```html
<!DOCTYPE html>
<html>
	<body>
		<script>
			function disappear(){
			    document.getElementById("shape").classList.add("hide");
			}
		</script>
		<style>
			.hide {
			    display: none;
			}
			.square {
			    height: 100px;
			    width: 100px;
			    background-color: yellow;
			}
			.square.blue {
			    background-color: blue;
			}
		</style>
		<div id="shape" class="square blue"></div>
		<button onclick="disappear()">Zniknij!</button>
	</body>
</html>
```

#### Usuwanie klas z elementów

```js
function change(){ 
	document.getElementById("shape").classList.remove("blue"); 
}
```
#### Przełączanie klas

```js
function changeVisibility(){ 
	document.getElementById("shape").classList.toggle("hide"); 
}
```


Możesz się zastanawiać, dlaczego kwadrat był niebieski na początku, skoro miał przypisane dwa layouty dla `background-color` w CSS. Dzieje się tak ze względu na system punktów. Kiedy stylizacja jest bardziej specyficzna, otrzymuje więcej punktów. Więc wskazanie dwóch klas bez spacji między nimi oznacza, że odnosi się do elementów z tymi dwoma klasami. Jest to bardziej specyficzne niż wskazanie jednej klasy. Odwoływanie się do identyfikatora (ID) w CSS, `#nameId`, otrzymuje jeszcze więcej punktów i byłoby priorytetowe nad layoutami opartymi na klasach. Ta warstwowa organizacja pozwala na mniej zduplikowanego kodu, ale może się zrobić bałagan, więc zawsze upewnij się, że dobrze łączysz CSS i HTML, aby uzyskać pożądany layout.



### <span style="color: #00b159;">Manipulowanie stylem elementu</span>
### Metoda`setAttribute()`

Istnieje bardziej ogólna metoda, która może być użyta do zmiany dowolnego atrybutu. Atrybutami są `id`, `class` i `href`. Inne powszechne atrybuty to `src` i `style`, ale istnieje wiele innych. Za pomocą metody `setAttribute()` możemy dodawać lub zmieniać atrybuty elementu.

```js
function changeAttr(){ 
	let el = document.getElementById("shape"); 
	el.setAttribute("style", "background-color:red;border:1px solid black"); 
	el.setAttribute("id", "new"); 
	el.setAttribute("class", "circle"); 
}
```



### <span style="color: #00aedb;">Nasłuchiwacze zdarzeń na elementach</span>

Zdarzenia to działania, które mają miejsce na stronie internetowej, takie jak kliknięcie czegoś, przesunięcie myszy nad elementem, zmiana elementu i wiele innych. Widzieliśmy już, jak dodać obsługę zdarzenia `onclick`. W ten sam sposób można dodać obsługę zdarzenia `onchange` lub `onmouseover`. Jest jednak jedno szczególne ograniczenie; jeden element może mieć tylko jeden handler zdarzeń jako atrybut HTML. Jeśli więc ma obsługę zdarzenia onclick, nie może mieć również obsługi zdarzenia onmouseover.


Sposób rejestrowania obsługi zdarzeń za pomocą JavaScript. Nazywamy to słuchaczami zdarzeń -`event listeners`. Korzystając ze słuchaczy zdarzeń, możemy dodać wiele zdarzeń do jednego elementu. W ten sposób JavaScript ciągle sprawdza, czy na stronie nie występują określone zdarzenia.

Dodanie słuchaczy zdarzeń to proces dwuetapowy:

1. Wybierz element, do którego chcesz dodać zdarzenie.
2. Użyj składni `addEventListener("event", function)`, aby dodać zdarzenie.

```js
document.getElementById("square").addEventListener("click", changeColor);
```

`Event listeners` często są dodawani podczas innych zdarzeń!
```js
window.onload = function() {
    // cokolwiek ma się zdarzyć po załadowaniu
    // na przykład dodawanie słuchaczy zdarzeń do elementów
}
```

Możesz dodawać zdarzenia do wszelkiego rodzaju elementów. Dotychczas używaliśmy tylko zdarzenia `click`, ale istnieje wiele innych, na przykład `focus`, `blur`, `focusin`, `focusout`, `mouseout`, `mouseover`, `keydown`, `keypress` i `keyup`.



### <span style="color: #f37735">Tworzenie nowych elementów</span>

Możesz dodać nowe elementy do dowolnego elementu w DOM, po prostu wybierając go i używając `appendChild()`.

```js
let el = document.createElement("p");
el.innerText = Math.floor(Math.random() * 100);
document.body.appendChild(el);
```



### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



