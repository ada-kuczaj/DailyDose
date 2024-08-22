--- 
tags: [[State i Hooks]] 
date: 2024-08-22

---
![[Pasted image 20240822191708.png]]
Ten komponent React demonstruje, jak zarządzać stanem aplikacji za pomocą hooka `useState` i dynamicznie aktualizować interfejs użytkownika w odpowiedzi na akcje użytkownika.

W komponentcie zarządzany jest jeden stan (`isDeleting`), który kontroluje, czy tryb usuwania jest aktywny. Stan jest początkowo ustawiony na `false`, co oznacza, że domyślnie komunikat ostrzegawczy dotyczący usunięcia nie jest wyświetlany.

Kiedy użytkownik kliknie przycisk "Delete", wywoływana jest funkcja `deleteHandler`, która aktualizuje stan, ustawiając `isDeleting` na `true`. W wyniku tej zmiany stanowej, komponent ponownie renderuje się, tym razem wyświetlając komunikat potwierdzający wraz z pytaniem "Are you sure?" oraz przyciskiem "Proceed".

Przycisk "Proceed" jest powiązany z funkcją `proceedHandler`, która resetuje stan `isDeleting` do `false`, co powoduje ponowne ukrycie komunikatu ostrzegawczego i powrót do początkowego widoku komponentu, gdzie tylko przycisk "Delete" jest widoczny.

Cały ten mechanizm umożliwia tworzenie prostych interaktywnych elementów interfejsu użytkownika, które reagują na działania użytkownika poprzez zmianę stanu komponentu, co w React skutkuje dynamiczną aktualizacją widoku. Dzięki temu komponenty są bardziej elastyczne i dostosowują się do bieżącego kontekstu użytkowania.



> [!IMPORTANT]  
W React, kiedy przekazujesz funkcję jako `onClick` (lub dowolny inny event handler), istnieją dwa główne sposoby, w jaki możesz to zrobić:
### 1. **Bez nawiasów**:
```js
<button onClick={proceedHandler}>Proceed</button>

```
Gdy przekazujesz referencję do funkcji bez nawiasów, oznacza to, że przekazujesz samą funkcję jako taką. React nie wywołuje tej funkcji natychmiast; zamiast tego, funkcja zostanie wywołana dopiero w momencie, gdy użytkownik kliknie przycisk. Jest to typowy sposób przypisywania event handlerów, ponieważ pozwala na kontrolowanie, kiedy funkcja zostanie uruchomiona.
### 2. **Z nawiasami**:
```js
<button onClick={proceedHandler()}>Proceed</button>
```
  Gdybyś dodał nawiasy do `proceedHandler`, funkcja zostałaby wywołana natychmiast w momencie renderowania tego komponentu, a wynik tej funkcji zostałby przypisany do `onClick`. W większości przypadków nie jest to pożądane zachowanie, ponieważ chcesz, aby funkcja została wywołana tylko wtedy, gdy użytkownik kliknie przycisk, a nie podczas renderowania komponentu.


Dlatego w typowych przypadkach przekazujesz funkcję bez nawiasów, co daje Reactowi referencję do funkcji, którą może wywołać później, gdy zajdzie zdarzenie, takie jak kliknięcie przycisku.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/quiz/6038728#overview

---



