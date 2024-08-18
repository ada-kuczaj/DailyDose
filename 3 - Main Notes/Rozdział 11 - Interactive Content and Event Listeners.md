--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-08-14

---

**KLUCZOWE INFORMACJE W ROZDZIALE 11:**
	• Interaktywna zawartość 
	• Określanie zdarzeń 
	• Obsługa zdarzenia `onload` 
	• Obsługa zdarzenia myszy 
	• Właściwość event target 
	• Przepływ zdarzeń DOM 
	• `onchange` i `onblur` 
	• Obsługa zdarzeń klawiszy 
	• Przeciąganie i upuszczanie elementów 
	• Wysyłanie formularza 
	• Animacja elementów

### <span style="color: #d11141;">Interaktywna zawartość </span>

Treść interaktywna to treść, która reaguje na działania użytkownika. Te interakcje mogą być różne: wpisywanie tekstu w polu tekstowym, kliknięcie w określone miejsce na stronie, najechanie kursorem na określony element lub wprowadzenie określonego znaku za pomocą klawiatury. Wszystkie te działania nazywamy zdarzeniami (events).


### <span style="color: #00b159;">Określanie zdarzeń</span>

Istnieją trzy sposoby określania zdarzeń:

##### 1. Określanie zdarzeń za pomocą HTML
Zdarzenie kliknięcia (click event). Można w ten sposób określić tylko jedno zdarzenie, a także nie można dynamicznie zmieniać zdarzenia.

```html
<p id="unique" onclick="magic()">Kliknij tutaj, aby zobaczyć magię!</p>
```

##### 2. Określanie zdarzeń za pomocą Javascript
Pobieramy właściwość reprezentującą wybrane zdarzenie i przypisujemy do niej funkcję. W tym przypadku wybieramy paragraf pokazany w poprzedniej sekcji na podstawie wartości atrybutu `id="unique"`, pobieramy właściwość `onclick` i przypisujemy do niej funkcję `magic()`, opakowując ją w funkcję anonimową. Możemy również na miejscu określić dokładną funkcję. Możemy nadpisać to inną funkcją w dowolnym momencie, co sprawia, że zdarzenie, które może być wywołane, jest bardziej dynamiczne. Możemy teraz także określić różne zdarzenia, czego nie możemy zrobić za pomocą HTML. Możemy na przykład dodać zdarzenie `keyup`, `keydown` lub `mouseover`

```js
document.getElementById("unique").onclick = function() { magic(); };
```

##### 3. Określanie zdarzeń za pomocą nasłuchiwaczy zdarzeń
Ostatnią metodą jest użycie metody `addEventListener()`, aby dodać zdarzenie do elementu. Dzięki temu możemy przypisać wiele funkcji do tego samego zdarzenia, na przykład gdy element zostanie kliknięty. Jeśli chcemy określić wywołania zdarzeń dla wszystkich elementów na stronie, możemy to zrobić w pętli, co prowadzi do bardziej przejrzystego stylu kodowania.

Warto zauważyć, że w obu metodach, które omawialiśmy wcześniej – używanie zdarzeń HTML oraz przypisywanie zdarzeń do właściwości – zdarzenie poprzedzone jest prefiksem `on`. Na przykład `onclick`, `onload`, `onfocus`, `onblur`, `onchange` itp. Nie jest to jednak wymagane, gdy używamy metody `addEventListener()`, gdzie określamy typ zdarzenia w nasłuchiwaczu zdarzeń bez prefiksu `on`, jak w poniższym przykładzie, alternatywnie dla `onclick`:

```js
document.getElementById("unique").addEventListener("click", magic);
```

Uwaga: tutaj pomijamy nawiasy za funkcją `magic`. Nie możemy w ten sposób przekazać parametrów. Jeśli trzeba to zrobić, należy opakować funkcję w funkcję anonimową, tak jak poniżej:

```js
document.getElementById("unique").addEventListener("click", function() {
    magic(arg1, arg2);
});
```



### <span style="color: #00aedb;">Obsługa zdarzenia `onload` </span>

Zdarzenie `onload` jest wywoływane po załadowaniu określonego elementu. Może to być przydatne z różnych powodów. Na przykład, jeśli chcesz wybrać element za pomocą `getElementById`, musisz mieć pewność, że ten element został już załadowany do DOM. To zdarzenie jest najczęściej używane na obiekcie `window`, ale można go użyć na dowolnym elemencie. Gdy używasz go na `window`, zdarzenie to jest uruchamiane, gdy obiekt `window` zakończy ładowanie.

```js
window.onload = function() {
    // cokolwiek musi się wydarzyć po załadowaniu strony, wchodzi tutaj
}
```

Zdarzenie `onload` jest podobne, ale różni się w przypadku obiektów `window` i `document`. Różnica zależy od przeglądarki internetowej, której używasz. Zdarzenie `load` uruchamia się na końcu procesu ładowania dokumentu.

##### Zdarzenie `DOMContentLoaded`

Możesz także użyć metody `addEventListener()` na dowolnym elemencie, aby obsłużyć dowolne zdarzenie. Może być ono również użyte do obsługi zdarzenia, które oznacza, że cała zawartość w DOM została załadowana. Istnieje specjalne wbudowane zdarzenie do tego celu: `DOMContentLoaded()`. To zdarzenie może być używane do obsługi zdarzenia ładowania DOM, które zostanie wywołane natychmiast po skonstruowaniu DOM dla strony, gdy zdarzenie jest ustawione.

```js
document.addEventListener("DOMContentLoaded", (e) => {
    console.log(e);
});
```

Alternatywnie, często zobaczysz to w tagu `body`:

```html
<body onload="unique()"></body>
```

o przypisuje funkcję nazwaną `unique()` do `body`, która zostanie wywołana, gdy ciało zostanie załadowane. Nie można łączyć `addEventListener()` z HTML używając ich jednocześnie. Jedno nadpisze drugie, w zależności od kolejności na stronie internetowej. Jeśli potrzebujesz dwóch zdarzeń, które mają się wydarzyć po załadowaniu DOM, będziesz musiał użyć dwóch wywołań `addEventListener()` w swoim JavaScript.



### <span style="color: #f37735">Obsługa zdarzenia myszy </span>

Istnieje wiele różnych obsługujących zdarzenia myszy. Oto lista dostępnych zdarzeń myszy:

- `**ondblclick`:** kiedy mysz zostanie podwójnie kliknięta
- **`onmousedown`:** kiedy mysz kliknie na element, ale przycisk myszy nie zostanie jeszcze zwolniony
- **`onmouseup`:** kiedy kliknięcie myszy na element zostanie zwolnione
- **`onmouseenter`:** kiedy mysz przesunie się na element
- **`onmouseleave`:** kiedy mysz opuszcza element i wszystkie jego dzieci
- **`onmousemove`:** kiedy mysz przesuwa się po elemencie
- **`onmouseout`:** kiedy mysz opuszcza pojedynczy element
- **`onmouseover`:** kiedy mysz najeżdża na element

```html
<!doctype html>
<html>
<body>
  <div id="divvy" onmouseover="changeColor()" style="width: 100px; height: 100px; background-color: pink;"></div>
  <script>
    function changeColor() {
      document.getElementById("divvy").style.backgroundColor = "blue";
    }
  </script>
</body>
</html>
```



### <span style="color: #ffc425;">Właściwość event target </span>

Za każdym razem, gdy zostanie wywołane zdarzenie, dostępna staje się zmienna zdarzenia (event). Ma ona wiele właściwości, które można sprawdzić za pomocą tego polecenia w funkcji wywoływanej przez zdarzenie:

```js
console.dir(event);
```

To pokaże wiele właściwości. Jedną z najciekawszych jest właściwość `target`. `Target` to element HTML, który wywołał zdarzenie. Dzięki temu możemy uzyskać informacje z strony internetowej.


Przypadek użycia, w którym właściwości rodzica mogą być przydatne, to formularze HTML, gdzie jest wiele pól wejściowych i przycisk. Przycisk w formularzu często ma formularz jako swojego bezpośredniego rodzica. Poprzez tego rodzica można pobrać dane z pól wejściowych. Jest to pokazane w następnym przykładzie:

```html
<!doctype html>
<html>
<body>
  <div id="welcome">Witaj!</div>
  <form>
    <input type="text" name="firstname" placeholder="Imię" />
    <input type="text" name="lastname" placeholder="Nazwisko" />
    <input type="button" onclick="sendInfo()" value="Wyślij" />
  </form>
  <script>
    function sendInfo() {
      let p = event.target.parentElement; 
      message("Witaj " + p.firstname.value + " " + p.lastname.value);
    }

    function message(m) {
      document.getElementById("welcome").innerHTML = m;
    }
  </script>
</body>
</html>
```

![[Pasted image 20240817224535.png]]

Za pomocą tego polecenia `event.target` jest przyciskiem HTML:  `let p = event.target.parentElement;` Rodzic przycisku, którym w tym przypadku jest formularz, zostaje zapisany w zmiennej `p`. `p` to rodzic i reprezentuje element formularza.  Za pomocą właściwości `value` można uzyskać wartości elementów wejściowych. `p.firstname.value;`



### <span style="color: #d11141;">Przepływ zdarzeń w DOM</span>

==**Bąbelkowanie zdarzeń**== (ang. _event bubbling_) to jedna z dwóch strategii propagacji zdarzeń w modelu DOM (Document Object Model) w JavaScript. Kiedy zdarzenie zostaje wywołane na danym elemencie w drzewie DOM, bąbelkowanie powoduje, że zdarzenie to jest najpierw obsługiwane przez ten element, a następnie propaguje się w górę drzewa DOM, do jego elementów nadrzędnych, aż do osiągnięcia elementu `document`.

##### Jak działa bąbelkowanie zdarzeń?

1. **Zdarzenie**: Kiedy użytkownik wykonuje akcję, taką jak kliknięcie na elemencie, zdarzenie zostaje wywołane na najniższym poziomie, czyli na elemencie, który został kliknięty.

2. **Obsługa zdarzenia**: Na początku, zdarzenie jest obsługiwane przez dany element. Jeśli element ma przypisany handler zdarzenia (funkcję obsługującą zdarzenie), zostaje ona wykonana.

3. **Propagacja w górę (bąbelkowanie)**: Po obsłużeniu zdarzenia przez dany element, zdarzenie przemieszcza się do jego elementu nadrzędnego, gdzie proces może się powtórzyć, jeśli również ten element ma przypisany handler zdarzenia. Ta propagacja trwa aż do osiągnięcia elementu `document`.

##### Zatrzymanie bąbelkowania
Czasami nie chcemy, aby zdarzenie propagowało się do elementów nadrzędnych. Możemy zatrzymać proces bąbelkowania, używając metody `stopPropagation()` w handlerze zdarzenia:

```js
document.getElementById('li').addEventListener('click', function(event) {
    event.stopPropagation(); // Zatrzymuje bąbelkowanie
    console.log('Kliknięto li');
});
```

Kiedy dodasz `true` jako trzeci argument do metody `addEventListener`, oznacza to, że nasłuchiwacz zdarzeń powinien być wykonany w ==fazie _przechwytywania==_ (ang. _capturing phase_), a nie w ==fazie _bąbelkowania_== (ang. _bubbling phase_). To zmienia sposób, w jaki zdarzenie jest obsługiwane w drzewie DOM.


### Faza przechwytywania a faza bąbelkowania

W przepływie zdarzeń w DOM istnieją dwie główne fazy:

1. **Faza przechwytywania (trickle-down)**: Zdarzenie rozpoczyna się od elementu `document` i przesuwa się w dół drzewa DOM aż do elementu docelowego. Jeśli nasłuchiwacz zdarzeń jest ustawiony na przechwytywanie, zostanie wywołany podczas tej fazy, gdy zdarzenie przemieszcza się w dół drzewa.

2. **Faza bąbelkowania (bubble-up)**: Po dotarciu zdarzenia do elementu docelowego i jego obsłużeniu, zdarzenie przesuwa się z powrotem w górę drzewa DOM, aż do elementu `document`, potencjalnie wywołując inne nasłuchiwacze zdarzeń ustawione na tę fazę.



### <span style="color: #00b159;">`onchange` i `onblur`</span>
Dwa inne zdarzenia, które często są używane w połączeniu z polami wejściowymi, to `onchange` i `onblur`.

- `onchange` jest wywoływane, gdy zmienia się wartość elementu, na przykład gdy wartość pola wejściowego ulega zmianie.

- `onblur` jest wywoływane, gdy obiekt traci fokus; na przykład, gdy kursor jest w jednym polu wejściowym, a następnie przechodzi do innego pola, zdarzenie `onblur` pierwszego pola wejściowego zostanie wywołane.

```html
<!DOCTYPE html>
<html>
<body>
  <div id="welcome">Witaj!</div>
  <form>
    <input type="text" name="firstname" placeholder="Imię" onchange="logEvent()" />
    <input type="text" name="lastname" placeholder="Nazwisko" onblur="logEvent()" />
    <input type="button" onclick="sendInfo()" value="Wyślij" />
  </form>
  <script>
    function logEvent() {
      let p = event.target;
      if (p.name == "firstname") {
        message("Imię zmienione na " + p.value);
      } else {
        message("Nazwisko zmienione na " + p.value);
      }
    }

    function sendInfo() {
      let p = event.target.parentElement;
      message("Witaj " + p.firstname.value + " " + p.lastname.value);
    }

    function message(m) {
      document.getElementById("welcome").innerHTML = m;
    }
  </script>
</body>
</html>
```

Pole wejściowe `firstname` ma przypisane zdarzenie `onchange`. Jeśli wartość danych w polu wejściowym zostanie zmieniona, to zdarzenie zostanie wywołane, gdy tylko pole wejściowe straci fokus. Jeśli pole wejściowe straci fokus, a wartość nie uległa zmianie, nic się nie stanie dla zdarzenia `onchange`. Inaczej jest w przypadku `onblur`, które jest przypisane do pola `lastname`. Nawet jeśli wartość się nie zmieniła, zdarzenie zostanie wywołane.

Innym zdarzeniem, które często jest używane z polami wejściowymi, jest `onfocus`, lub po prostu `focus`, gdy jest używane w połączeniu z nasłuchiwaczem zdarzeń. To zdarzenie jest związane z wejściem kursora do pola wejściowego i jest wywoływane, gdy pole wejściowe zostaje objęte fokusem przez kursor i możliwe jest wprowadzenie danych.



### <span style="color: #00aedb;">Obsługa zdarzeń klawiszy</span>

**Najważniejsze Zdarzenia Klawiszy:**
- `onkeypress`: Wywoływane, gdy klawisz jest naciśnięty i zwolniony.
- `onkeydown`: Wywoływane w momencie naciśnięcia klawisza (przed jego zwolnieniem).
- `onkeyup`: Wywoływane w momencie zwolnienia klawisza.

**Przykład:** Poniższy kod umożliwia wpisywanie tylko liczb do pola wejściowego, blokując inne znaki.
```html
<!doctype html>
<html>
<body>
  <div id="wrapper">JavaScript jest fajny!</div>
  <input type="text" onkeypress="return numCheck()" onpaste="return false">
  <script>
    function numCheck() {
      return !isNaN(event.key);  // Zwraca true tylko dla liczb
    }
  </script>
</body>
</html>
```

**Kluczowe Informacje:**
- `event.key` pozwala na pobranie znaku wywołującego zdarzenie.
- Wartość `true` w `return` dodaje znak do pola, `false` blokuje jego wpisanie.
- `onpaste="return false"` blokuje wklejanie niedozwolonych znaków do pola.


Zwróć uwagę na jeszcze jedną rzecz: `onpaste="return false"`. Służy to do radzenia sobie z osobami, które mogą próbować skopiować i wkleić liczby do pola nienumerycznego lub inne znaki do pola numerycznego, co mogłoby umożliwić wprowadzenie niedozwolonych znaków.



### <span style="color: #f37735"> Przeciąganie i upuszczanie elementów </span>

Aby oznaczyć element jako coś, co można przeciągać, musimy dodać atrybut `draggable`. Następnie musimy zdecydować, co zrobimy, gdy upuścimy przeciągany element. Musimy to określić w obszarze, do którego można przeciągać element. Dodamy tę funkcjonalność do obu pól (`div`), aby można było przeciągać element z jednego pola do drugiego i z powrotem.

```html
<div class="box" ondrop="dDrop()" ondragover="nDrop()">
  1
  <div id="dragme" ondragstart="dStart()" draggable="true">
    Przeciągnij mnie!
  </div>
</div>
<div class="box" ondrop="dDrop()" ondragover="nDrop()">2</div>
```

```js
  let holderItem;

  function dStart() {
    holderItem = event.target;
  }

  function nDrop() {
    event.preventDefault();
  }

  function dDrop() {
    event.preventDefault();
    if (event.target.className == "box") {
      event.target.appendChild(holderItem);
    }
  }
```

Zaczynamy od określenia zmiennej w skrypcie dla elementu, który chcemy przytrzymać podczas przeciągania. Gdy zdarzenie `ondragstart` zostanie wywołane, zapisujemy element, który jest przeciągany, w zmiennej `holderItem`.

Normalnie, gdy przeciągasz element, upuszczanie nie jest dozwolone według domyślnych ustawień HTML. Aby umożliwić upuszczenie, musisz zapobiec domyślnemu zdarzeniu, które oznacza, że element, który chcesz upuścić, nie może być upuszczony.

Zazwyczaj, zanim zapobiegniesz domyślnemu zachowaniu, przeprowadzasz pewne sprawdzenia, aby upewnić się, że element, który jest upuszczany, może być zaakceptowany w danym miejscu. W powyższym przykładzie sprawdzamy, czy nazwa klasy elementu, na który jest upuszczany, to `box`. Jeśli tak, dodajemy `holderItem` jako element podrzędny do `box`.

Stworzyliśmy stronę, która umożliwia przenoszenie elementu HTML z jednego pola do drugiego. Jeśli spróbujesz upuścić go gdziekolwiek indziej, element wróci na swoje poprzednie miejsce.



### <span style="color: #ffc425;">Wysyłanie formularzy</span>

Gdy formularz zostaje wysłany, może zostać wywołane zdarzenie. Można to osiągnąć na różne sposoby, a jednym z nich jest dodanie atrybutu `onsubmit` do elementu formularza.

```html
<form onsubmit="doSomething()">
```

Funkcja, która jest tam wymieniona, zostanie wywołana za każdym razem, gdy dane wejściowe typu `submit` zostaną wysłane.

```html
<input type="submit" value="send">
```

Możemy zrobić więcej z HTML-em elementu formularza; na przykład możemy przekierować na inną stronę. Musimy określić sposób, w jaki chcemy wysłać wartości formularza, używając atrybutu `method`, oraz stronę docelową, używając atrybutu `action`.

```html
<form action="anotherpage.html" method="get" onsubmit="doStuff()">
```

Istnieją inne interesujące rzeczy, które możemy zrobić z `onsubmit` w formularzach. Pamiętasz użycie `return` dla `onkeypress`? Możemy zrobić coś podobnego tutaj! Jeśli wywoływana funkcja zwróci wartość logiczną (Boolean), formularz zostanie wysłany tylko wtedy, gdy wartość ta będzie `true`. Jest to bardzo przydatne, jeśli chcemy przeprowadzić walidację formularza przed jego wysłaniem.

```html
<!doctype html>
<html>
<body>
  <div id="wrapper"></div>
  <form action="anotherpage.html" method="get" onsubmit="return valForm()">
    <input type="text" id="firstName" name="firstName" placeholder="First name" />
    <input type="text" id="lastName" name="lastName" placeholder="Last name" />
    <input type="text" id="age" name="age" placeholder="Age" />
    <input type="submit" value="submit" />
  </form>
  <script>
    function valForm() {
      var p = event.target.children;
      if (p.firstName.value == "") {
        message("Potrzebne jest imię!!");
        return false;
      }
      if (p.lastName.value == "") {
        message("Potrzebne jest nazwisko!!");
        return false;
      }
      if (p.age.value == "") {
        message("Potrzebny jest wiek!!");
        return false;
      }
      return true;
    }

    function message(m) {
      document.getElementById("wrapper").innerHTML = m;
    }
  </script>
</body>
</html>
```



### <span style="color: #d11141;">Animowanie elementów</span>

Możesz animować elementy, używając HTML, CSS i JavaScript. Pozwala to na tworzenie jeszcze ciekawszych efektów na naszej stronie internetowej. Na przykład możemy wywołać animację jako zdarzenie. Może to być użyte do różnych celów, takich jak zilustrowanie jakiegoś wyjaśnienia, przyciągnięcie uwagi użytkownika do określonego miejsca, czy nawet do stworzenia gry.

Oto bardzo podstawowy przykład. Możemy użyć właściwości `position` i ustawić ją na `absolute` w CSS. To sprawia, że pozycja elementu jest relatywna w stosunku do jego najbliższego pozycjonowanego rodzica, którym w tym przypadku będzie `body`. Poniżej znajduje się kod dla fioletowego kwadratu, który przesuwa się z lewej na prawą stronę, gdy przycisk zostanie kliknięty.

```html
<!doctype html>
<html>
  <style>
    div {
      background-color: purple;
      width: 100px;
      height: 100px;
      position: absolute;
    }
  </style>
  <body>
    <button onclick="toTheRight()">Przesuń w prawo</button>
    <div id="block"></div>
    <script>
      function toTheRight() {
        let b = document.getElementById("block");
        let x = 0;
        setInterval(function () {
          if (x === 600) {
            clearInterval();
          } else {
            x++;
            b.style.left = x + "px";
          }
        }, 2);
      }
    </script>
  </body>
</html>
```

Jednocześnie możesz także ustawić inne pozycje, takie jak `style.top`, `style.bottom` i `style.right`, lub dodawać nowe elementy, aby stworzyć efekt padającego śniegu lub pokazać ciągle poruszające się samochody.



### References:

Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



