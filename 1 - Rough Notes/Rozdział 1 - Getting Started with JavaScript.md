
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-07-23

---

JavaScript to język programowania, którego można używać zarówno **po stronie serwera, jak i po stronie klienta**. 
- strona serwera aplikacji to logika zaplecza, która zwykle działa na komputerach w centrach danych i wchodzi w interakcję z bazą danych
- strona klienta to ta, która działa na urządzeniu użytkownika, często przeglądarce JavaScript.

**KLUCZOWE INFORMACJE W ROZDZIALE 1:**
	• Dlaczego warto się uczyć Javascript?
	• Przygotowywanie środowiska
	• Jak przeglądarka rozumie JavaScript?
	• Używanie konsoli w przeglądarce
	• Dodawanie JavaScript do przeglądarki
	• Pisanie kodu w JavaScript


### Dlaczego warto się uczyć Javascript?

- najszerzej używany język programowania
- to język obsługiwany i rozumiany przez przeglądarki internetowe
- szybko pozwala na tworzenie dynamicznych stron internetowych, które wchodzą z interakcję z użytkownikiem 
- pozwala na pisanie frontendu jak i backendu
- może być używany do programowania (częściowo) obiektowego, funkcjonalnego i proceduralnego, które są po prostu różnymi paradygmatami programowania
- istnieje mnóstwo bibliotek i frameworków, z których możesz skorzystać
- duża społeczność ludzi piszących w tym języku


### Przygotowywanie środowiska

Integrated Development Environment (IDE) - aplikacja pozwalająca na pisanie, uruchamianie i debugowanie kodu.

Zalety:
- kolorowanie składni
- autouzupełnianie kodu
- debugowanie
- pluginy i wtyczki np. live server


### Jak przeglądarka rozumie JavaScript?

JavaScript jest językiem interpretowanym, co oznacza, że kod jest wykonywany w czasie rzeczywistym przez interpreter, a nie kompilowany przed uruchomieniem, JIT (ang. Just-In-Time Compilation)

HTML definiuje co znajduje się na stronie internetowej, całą zawartość.
CSS szata graficzna strony.
JS określa co strona może robić i jak wchodzić w interakcje z użytkownikiem

ECMAScript - jest to specyfikacja lub standaryzacja języka JavaScript. Obecnym standardem jest ECMAScript 6 (nazywany także ES6). Przeglądarki używają tej specyfikacji do obsługi JavaScript. JavaScript ma wiele implementacji, które mogą się nieznacznie różnić, ale ECMAScript można uznać za podstawową specyfikację, którą na pewno będzie zawierała implementacja JavaScript.

Document Object Model (DOM) to programistyczny interfejs aplikacji, który reprezentuje struktury dokumentów HTML i XML w formie drzewa, umożliwiając programistom modyfikowanie zawartości i struktury dokumentów za pomocą języków programowania


### Używanie konsoli w przeglądarce

Debugowanie polega na znalezieniu problemu, gdy aplikacja nie wykazuje pożądanego zachowania.

Narzędzia dla developerów i "Zbadaj" na stronie internetowej.
console.log()
console.table()
console.error()

### Dodawanie JavaScript do przeglądarki

Istnieją dwa sposoby łączenia JavaScript ze stroną internetową:
Pierwszy sposób polega na wpisaniu kodu JavaScript bezpośrednio w kodzie HTML pomiędzy dwoma znacznikami `<script>`. Można też połączyć plik JavaScript z plikiem HTML, korzystając ze znacznika skryptu znajdującego się w nagłówku strony HTML.

```html
<html> 
  <script type="text/javascript"> 
    alert("Hi there!"); 
  </script> 
</html>
```

To nie jest najlepsza praktyka. Należy utworzyć dwa elementy wewnątrz `<html>`: `<head>` i `<body>`. W elemencie head zapisujemy metadane i tę część wykorzystujemy także później do podłączenia plików zewnętrznych do naszego pliku HTML

```html
<!DOCTYPE html> 
<html> 

<head> 
  <title>This goes in the tab of your browser</title> 
</head> 

<body> 
The content of the webpage 
  <script> console.log("Hi there!"); 
  </script> 
</body> 

</html>
```

#### Podlinkowanie zewnętrznego pliku do naszej strony internetowej

Można połączyć plik zewnętrzny z plikiem HTML. Jest to uważane za lepszą praktykę, ponieważ lepiej organizuje kod i pozwala uniknąć bardzo długich stron HTML ze względu na JavaScript. Oprócz tych korzyści można też ponownie używać kodu JavaScript na innych stronach swojej witryny bez konieczności kopiowania i wklejania. Załóżmy, że mamy ten sam JavaScript na 10 stronach i musimy wprowadzić zmiany w skrypcie. Musimy zmienić tylko jeden plik, jeśli jest to zrobione w sposób pokazany w tym przykładzie.


Ścieżka względna (relative path) odnosi się do lokalizacji pliku lub folderu w stosunku do bieżącego katalogu, podczas gdy ścieżka bezwzględna (absolute path) określa pełną, dokładną lokalizację pliku lub folderu, zaczynając od głównego katalogu systemu plików.


### Pisanie kodu w JavaScript


Podstawowe zasady formatowania kodu:
- wcięcia (indentations)
- średniki (semicolons)
- konwencje nazewnictwa
- komentarze
- wiersz polecenia (command prompt) - działa bardzo podobnie do alertu, ale wymaga danych wejściowych od użytkownika.
- random numbers

### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



