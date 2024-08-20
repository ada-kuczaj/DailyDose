--- 
tags: [[React]]
date: 2024-08-19

---
### <span style="color: #f37735">plik.jsx - rozkład na czynniki pierwsze</span>

![[Pasted image 20240819231430.png]]

Plik `index.jsx` w projekcie React pełni rolę głównego ==punktu wejścia (entry point)== aplikacji. Jest to miejsce, w którym aplikacja React jest inicjalizowana i renderowana w przeglądarce (odpowiada za to biblioteka ReactDOM). W tym pliku importowane są główne komponenty aplikacji, najczęściej `App.jsx`, oraz style globalne.

Następnie, w `index.jsx`, odnajdywany jest element HTML, który ma pełnić rolę kontenera dla aplikacji (najczęściej `div` o ID `root`). Używając ReactDOM, aplikacja React jest renderowana w tym kontenerze.

Dzięki temu plikowi `index.jsx`, cała struktura aplikacji jest ładowana i wyświetlana w przeglądarce, co czyni go kluczowym elementem każdego projektu React.


#### Metoda `render()`

Metoda `render()` w React jest kluczowym elementem każdego komponentu klasowego. Jest to jedyna wymagana metoda w komponentach klasowych, a jej głównym zadaniem jest zwracanie opisu tego, co ma być wyświetlone na ekranie.

Wewnątrz metody `render()` tworzymy strukturę UI za pomocą JSX (JavaScript XML), która zostanie przekształcona przez React w odpowiednie elementy DOM. Metoda `render()` jest wywoływana za każdym razem, gdy stan (`state`) lub właściwości (`props`) komponentu zmieniają się, co sprawia, że UI jest automatycznie aktualizowane, odzwierciedlając te zmiany.

Ważne jest, że metoda `render()` powinna być czysta, co oznacza, że nie powinna modyfikować stanu komponentu ani wykonywać żadnych efektów ubocznych (np. zapytań do API). Jej zadaniem jest jedynie zwrócenie JSX, który określa, jak dany komponent powinien wyglądać.


#### Metoda `createRoot()`

Metoda `createRoot` jest nową metodą wprowadzoną w React 18 jako część nowego API do zarządzania renderowaniem aplikacji. Zastępuje ona wcześniejsze `ReactDOM.render()` i jest główną metodą używaną do renderowania aplikacji React do DOM.

- `createRoot` tworzy tzw. "root container" dla aplikacji React. Root container to miejsce w DOM, w którym React będzie renderował swoje komponenty.

- Metoda ta pozwala na użycie nowego trybu renderowania, który obsługuje takie funkcje jak współbieżność (concurrent mode) i strumieniowe renderowanie na serwerze (server-side streaming).



### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649006#content

---



