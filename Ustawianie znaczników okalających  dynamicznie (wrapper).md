--- 
tags: [[React]]
date: 2024-08-23

---

 W większych aplikacjach, możemy chcieć mieć możliwość użycia różnych /znaczników/elementów/komponentów okalających wokół naszej zawartości w różnych miejscach w aplikacji.
np. 
`<menu> jakaś zawartość, lista, przuyciski itp.</menu>`

W tym celu możemy zaakceptować dodatkową właściwość o nazwie `buttonsContainer` (nazwa dowolna).

![[Pasted image 20240823220852.png]]
### <span style="color: #ffc425;"> Różnica między wbudowanymi i niestandardowymi</span>

Musimy upewnić się, że zamiast szukać wbudowanego komponentu o nazwie `buttonsContainer`, React spojrzy na wartość wewnątrz tej właściwości i potraktuje ją jako niestandardowy komponent, który powinien zostać wyrenderowany.

Musimy dodać tutaj specjalną stałą lub zmienną, która może mieć nazwę np. `ButtonContainer`, ale która zaczyna się ==wielką literą==, co jest ważne. A następnie tutaj, w tym `ButtonsContainer`, możemy przechowywać nasz `buttonsContainer`.

W ten sposób zasadniczo tworzymy stałą , która może być używana jako komponent niestandardowy, ponieważ zaczyna się od dużej litery i dlatego może być używana tutaj w ten sposób.

Teraz React przyjrzy się wartości przechowywanej w `buttonsContainer` i będzie to wartość otrzymana we właściwości `buttonsContainer`. Następnie zobaczy, że jest to ciąg znaków i w takim przypadku spróbuje poszukać wbudowanego komponentu, który można zidentyfikować za pomocą tej wartości ciągu znaków. Lub jeśli przekażemy niestandardowy komponent wyrenderuje go.

<span style="color: #f37735">Dzięki temu jesteśmy teraz w stanie dynamicznie ustawić wrapper, który powinien być używany wokół tych przycisków.</span>

#### Dwie ważne rzeczy, o których należy tutaj pamiętać, to:

- Prop musi być użyteczny jako niestandardowy komponent w komponencie odbierającym. Tak więc props musi zaczynać się od ==wielkiej litery== (najlepszy sposób to ,aby został przekonwertowany na stałą, która zaczyna się od wielkiej litery).

W pliku docelowym przekazywanie wartości różni się:
- Dla elementów, takich jak `menu`, `ul` lub `div`  używasz nawiasów `"  "`.
- Dla niestandardowych komponentów używasz nawiasów wąsów `{ }` i samą nazwę `{Jakośkomponent}`. Komponenty niestandardowe muszą być przekazywane jako wartość dynamiczna.

![[Pasted image 20240823221043.png]]


> [!NOTE]  CIEKAWOSTKA
> Wartość defaultową elementu też da się ustawić:
> 
![[Pasted image 20240823224327.png]]
Teraz w głównej aplikacji nie musimy ustawiać `buttonsContainer` prop. Uwaga, jeżeli chcemy jako wartość domyślną inny komponent niestandardowy, który utworzyliśmy np. `Section`, musimy go powyżej zaimportować w `Tabs.jsx`.



### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659756#content

---



