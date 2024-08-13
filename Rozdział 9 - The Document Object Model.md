
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-08-13

---

**KLUCZOWE INFORMACJE W ROZDZIALE 8:**
	 • Podstawowy kurs HTML
	 • Wprowadzenie do BOM (Browser Object Model)
	 • Wprowadzenie do DOM (Document Object Model)
	 • Rodzaje elementów DOM
	 • Wybieranie elementów strony


## <span style="color: #d11141;">Podstawowy kurs HTML</span>

Hyper-Text Markup Language (HTML) jest językiem, który kształtuje zawartość stron internetowych. Przeglądarki internetowe rozumieją kod HTML i przedstawiają go w formacie, do którego jesteśmy przyzwyczajeni: strony internetowe.

```html
<!DOCTYPE html>
<html>
	<head>
	    <title>Karta w przeglądarce</title>
	</head>
	<body>
	    <p>Cześć, internecie!</p>
	</body>
</html>
```
### Elementy HTML

![[Pasted image 20240813203407.png]]
### Atrybuty HTML

Atrybuty wpływają na element, na którym są określone. Znajdują się one wewnątrz elementu, na którym są określone, i są przypisane wartości za pomocą znaku równości.

![[Pasted image 20240813203658.png]]


## <span style="color: #00b159;">Wprowadzenie do BOM (Browser Object Model)</span>

BOM, czasami nazywany także obiektem okna przeglądarki, zawiera wszystkie metody i właściwości, które pozwalają JavaScriptowi na interakcję z przeglądarką. To informacje związane z wcześniej odwiedzanymi stronami, rozmiarem okna przeglądarki, a także z DOM. Obiekt window ma globalne zmienne i funkcje, a wszystkie te elementy można zobaczyć, gdy zbadamy obiekt window.

F12 lub Zbadaj przenosi nas do DevTools narzędzia dla developerów. Aby uzyskać informacje o obiekcie window, należy wpisać następujące polecenie i nacisnąć Enter: `console.dir(window);` Metoda `console.dir()` pokazuje listę wszystkich właściwości określonego obiektu.

Niektóre z najważniejszych obiektów BOM, to:
- History
- Navigator
- Location

#### Obiekt historii okna

Ten obiekt można faktycznie pisać bez przedrostka window, ponieważ jest dostępny globalnie, więc możemy uzyskać dokładnie ten sam obiekt, używając polecenia `console.dir(window.history)` lub po prostu `console.dir(history)` Ten obiekt można faktycznie użyć do powrotu do poprzedniej strony. Ma wbudowaną funkcję do tego celu, która nazywa się `go`.
```js
window.history.go(-1);
```

#### Navigator

Właściwość navigator jest szczególnie interesująca, ponieważ zawiera informacje o przeglądarce, której używamy, takie jak jej rodzaj i wersja, oraz jaki system operacyjny przeglądarka obsługuje. Może to być przydatne do dostosowywania strony internetowej dla określonych systemów operacyjnych. Wyobraź sobie przycisk pobierania, który będzie inny dla Windows, Linux i macOS.
```js
console.dir(window.navigator);
```

#### Location

Obiekt location zawiera adres URL bieżącej strony internetowej. Jeśli nadpiszesz (części) tej właściwości, zmusisz przeglądarkę do przejścia na nową stronę! Jak dokładnie to zrobić, różni się w zależności od przeglądarki. Obiekt location składa się z kilku właściwości.
```js
console.dir(window.location)
location.ancestorOrigins.length;
```

Drugie polecenie zwróci długość obiektu `ancestorOrigins`, który reprezentuje liczbę kontekstów przeglądania związanych z naszą stroną. Może to być przydatne do określenia, czy strona internetowa jest osadzona w nieoczekiwanym kontekście. Nie wszystkie przeglądarki mają ten obiekt; ponownie, BOM i wszystkie jego elementy różnią się w zależności od przeglądarki.


## <span style="color: #00aedb;">Wprowadzenie do DOM (Document Object Model)</span>

DOM zawiera elementy HTML na stronie internetowej. Za pomocą JavaScriptu możemy wybierać i manipulować częściami DOM. To prowadzi do interaktywnych stron internetowych zamiast statycznych. Krótko mówiąc, umiejętność pracy z DOM oznacza, że możesz tworzyć interaktywne strony internetowe!

DOM jest to sposób przedstawienia struktury dokumentu HTML jako logicznego drzewa. Jest to możliwe dzięki bardzo ważnej zasadzie, że wewnętrzne elementy muszą być zamknięte, zanim zostaną zamknięte elementy zewnętrzne.

![[Pasted image 20240813205351.png]]

Jak widać, najbardziej zewnętrzny element, `html`, znajduje się na szczycie drzewa. Następne poziomy, `head` i `body`, są jego dziećmi. `head` ma tylko jedno dziecko: `title`. `body` ma dwoje dzieci: `h1` i `div`. A `div` ma dwoje dzieci: `p` i `a`. Te elementy są zazwyczaj używane do paragrafów i linków (lub przycisków). Oczywiście skomplikowane strony internetowe mają złożone drzewa. To logiczne drzewo i wiele dodatkowych właściwości tworzą DOM strony internetowej.

## <span style="color: #ffc425;">Wybieranie elementów strony</span>

Obiekt document zawiera wiele właściwości i metod. Aby pracować z elementami na stronie, zmieniać ich wartości itp., najpierw trzeba je znaleźć i wybrać. 

#### `querySelector()`, `querySelectorAll()`

Do wyselekcjonowania elementów strony do użycia w kodzie JavaScript i manipulacji nimi, służą metody `querySelector()` lub `querySelectorAll()`. Obie te metody mogą być używane do wybierania elementów strony za pomocą *nazwy tagu, ID lub klasy*. 

- Metoda `document.querySelector()` zwróci pierwszy element w dokumencie, który pasuje do określonych selektorów. Jeśli nie zostaną znalezione żadne pasujące elementy strony, zwrócony zostanie wynik null. 
- Metoda `querySelectorAll()` zwróci wiele pasujących elementów, w postaci statycznej listy węzłów, która reprezentuje listę elementów dokumentu pasujących do określonej grupy selektorów.

```js
const ele1 = document.querySelector("h1"); //zostanie wybrany tylko pierwszy nagłówek
console.dir(ele1);

const eles = document.querySelectorAll(".output"); //Ta metoda zwróci wszystkie elementy, które pasują do selektora w formie tablicy. W tym przykładzie będziemy szukać instancji klasy `output`, co można zrobić, dodając przed nazwą klasy kropkę
console.log(eles);
```

### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



