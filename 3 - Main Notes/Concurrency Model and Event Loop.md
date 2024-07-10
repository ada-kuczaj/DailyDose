
--- 
tags: [[JS]] 
date: 2024-07-10

---
## Model współbieżności i pętla zdarzeń

Jeśli wiesz o programowaniu asynchronicznym, możesz zastanawiać się, w jaki sposób Twój kod może w rzeczywistości nie blokować się i przejść do innych zadań, czekając na zakończenie operacji asynchronicznych.

JavaScript to `single-threaded language` czyli język jednowątkowy, co oznacza, że ​​dwie instrukcje NIE mogą być wykonane jednocześnie (`simultaneously`).

### Concurrency Model =Model Współbieżności

1. **Single-threaded** (Jednowątkowość):
	- JavaScript jest jednowątkowy, co oznacza, że może wykonywać tylko jeden fragment kodu w danym momencie.
    - Może się to wydawać ograniczające, ale JavaScript został zaprojektowany z myślą o operacjach nieblokujących, co jest szczególnie ważne w programowaniu webowym.
    
1. **Programowanie Asynchroniczne**:
    
    - JavaScript obsługuje wiele zadań równocześnie za pomocą programowania asynchronicznego, bez użycia wielu wątków.
    - Osiąga się to za pomocą `callbacks, promises`, and `async/await`.


Przykład 1:

```js
console.log("I'm learning about");  
  
for (let idx=0; idx < 999999999; idx++) {}  
  
// The second console.log() statement is  
// delayed by the for loop's execution  
console.log("the Event Loop");
```
Kod wypisał 2 linie na konsoli. Wypisano pierwszą linię, następnie wykonano pętlę for i po pewnym czasie ostatnia linia została wypisana na konsoli.


Przykład 2:

```js
console.log("I’m learning about");  
setTimeout(() => { console.log("Event Loop");}, 2000);  
console.log("the");
```
Kod wypisał 3 linie na konsoli. Wypisano pierwszą linię, następnie wykonuje się setTimeout,  ostatnia linia została wypisana na konsoli, końcowo timer kończy działanie i "Event Loop" zostaje wypisane na konsoli.

### Pętla Zdarzeń

Pętla zdarzeń jest fundamentalną częścią modelu współbieżności JavaScript, która pozwala na wykonywanie operacji nieblokujących mimo jednowątkowości.

![[Event Loop.png]] 

#### Komponenty pętli zdarzeń:

- **==Memory Heap==** - Sterta to przestrzeń pamięci, używana do dynamicznej alokacji obiektów w sposób nieustrukturyzowany. przechowuje także wskaźniki do zmiennych.

- **==Call Stack==** - Stos wywołań to miejsce, gdzie JavaScript śledzi wywołania funkcji. Kiedy funkcja jest wywoływana, jest dodawana do stosu. Gdy funkcja zwraca wartość, jest usuwana ze stosu. Jeśli stos jest pusty, pętla zdarzeń może przechwycić nowe zadania. Funkcje wchodzą na stos w kolejności „ostatnie weszło, pierwsze wyszło” (LIFO).

- ==**Event Queue**== - to lista wiadomości odpowiadających funkcjom, które czekają na przetworzenie. Na diagramie te wiadomości wchodzą do kolejki zdarzeń z takich źródeł jak różne API przeglądarki (web APIs) lub asynchroniczne funkcje, które zostały wywołane i zwracają dodatkowe zdarzenia do obsłużenia przez stos wywołań. Wiadomości wchodzą do kolejki w kolejności "first in, first out" (FIFO), czyli pierwsze weszło, pierwsze wyszło. W samej kolejce zdarzeń nie jest wykonywany żaden kod; zamiast tego przechowuje ona funkcje, które czekają na ponowne dodanie do stosu wywołań.

- ==**Event Loop**== - Pętla zdarzeń sprawdza (polling), czy stos wywołań jest pusty. Jeśli stos jest pusty, dodaje pierwszą oczekującą wiadomość (funkcję) z kolejki zdarzeń. Powyższe kroki są powtarzane, aż stos wywołań zostanie opróżniony.

- ==**Node or Web APIs**==

JavaScript jest jednowątkowy, ale możemy emulować współbieżność z pętlą zdarzeń. Kod będzie zawsze wykonywany synchronicznie, ale kod asynchroniczny można wypchnąć do internetowych interfejsów API i skierować z powrotem na stos za pośrednictwem kolejki zdarzeń i pętli zdarzeń.




### References:
https://www.codecademy.com/courses/learn-javascript-best-practices/articles/javascript-concurrency-model-and-event-loop

---



