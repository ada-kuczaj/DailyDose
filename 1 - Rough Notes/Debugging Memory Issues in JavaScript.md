
--- 
tags: [[JS]] [[Debugging JavaScript in VSCode]]
date: 2024-07-14

---
# Use Chrome DevTools to fix performance issues and memory leaks in your code

Przypadkowe wprowadzenie wycieków pamięci do aplikacji może być proste, np.:

- Dodanie nasłuchiwacza zdarzeń bez jego usunięcia
- Dodanie zmiennych do obiektu globalnego

Gdy ustawisz obiekty jako dane na elemencie DOM, może to prowadzić do nadmiernego zużycia pamięci lub wycieku pamięci, jeśli nigdy nie usuniesz obiektu DOM. Na przykład, może to się zdarzyć, gdy renderujesz okno modalne poza ekranem i tam je pozostawiasz.

#### Aby znaleźć źródło problemów z pamięcią, musimy rozważyć pytania takie jak:

- Skąd została przydzielona pamięć?
- Dlaczego niektóre części pamięci nie zostały zebrane przez garbage collector?
- Jak pamięć rośnie w czasie?

Narzędzia deweloperskie przeglądarek pomagają odpowiedzieć na te pytania.

# Developer Tools that can help you debug memory issues

Dostępne narzędzia w Memory Inspector:

- **Heap Snapshot**: Pokazuje, jak pamięć jest rozłożona między obiektami JavaScript i powiązanymi węzłami DOM na stronie.
- **Allocation instrumentation on timeline**: Pokazuje alokacje pamięci JavaScript w czasie, pozwalając na izolowanie wycieków pamięci.
- **Allocation sampling**: Rejestruje alokacje pamięci metodą próbkowania, co jest przydatne przy długotrwałych operacjach.


### Heap Snapshot

Heap snapshots są świetne do debugowania problemów z pamięcią, ponieważ pokazują, co zajmuje pamięć w danym momencie i pozwalają na porównania w czasie. Widok ten pokazuje:

- Jakie obiekty są w pamięci
- Szczegóły dotyczące obiektów w pamięci, takie jak funkcja konstruktorowa użyta do ich tworzenia
- Jak obiekty się odnoszą do siebie
- Rozmiar pamięci używany przez obiekty
- Co zostało dodane lub nie zostało zebrane przez garbage collector między snapshotami

Tab Heap Snapshot ma 4 różne widoki:

- **Summary view**: Grupuje obiekty według konstruktora i może być używany do śledzenia wycieków DOM.
- **Comparison view**: Pokazuje różnice między snapshotami. Jeśli zużywasz więcej pamięci lub masz zebrane śmieci między snapshotami, możesz zidentyfikować wyciek pamięci na podstawie liczby referencji i zmian w wolnej pamięci.
- **Containment view**: Pomaga analizować obiekty odniesione w przestrzeni nazw globalnych (Window), aby dowiedzieć się, dlaczego nie są zbierane przez garbage collector.
- **Statistics view**: Pokazuje podział użycia pamięci na różne kategorie, takie jak Kod, Ciągi znaków i Tablice JS.


### Allocation Instrumentation on Timeline

Możesz użyć osi czasu alokacji, aby zidentyfikować obiekty, które nie są zbierane przez garbage collector, gdy powinny być, i dlatego pozostają w pamięci. Jest to kombinacja szczegółów z heap snapshot, z dodatkowym śledzeniem osi czasu, które robi aktualizowane snapshoty co 50 ms.

Widok ten pokazuje:

- Gdzie obiekty były alokowane podczas wykonywania kodu
- Jak często śmieci są zbierane


### Allocation Sampling

Próbkowanie alokacji jest podobne do osi czasu alokacji, ale ma mniejsze obciążenie wydajnościowe. Snapshoty są pobierane jako próbki stosu zamiast regularnie, jak w przypadku osi czasu alokacji. Możesz użyć próbkowania alokacji, gdy potrzebujesz rejestrować snapshoty dla długotrwałych operacji i używać stosu do identyfikacji, skąd pochodzą alokacje.

Widok ten pokazuje:

- Jakie linie kodu tworzą śmieci dla garbage collectora
- Jakie linie kodu alokują nową pamięć sterty





##### Step 1

To open Chrome’s DevTools, select View > Developer > Developer Tools. You can also use keyboard shortcuts:

- On Mac: `Command` + `Option` + `i`
- On Linux/Windows: `F12` or `Control` + `Shift` + `I`

![[Pasted image 20240714230449.png]]

Jeśli przyjrzysz się bliżej obrazowi, zobaczysz, że utworzono instancje wielu obiektów JavaScript w celu załadowania strony, w tym niektóre elementy wewnętrzne silnika JavaScript, takie jak (kod skompilowany) i (system). Ogólnie rzecz biorąc, możesz zignorować wszystko, co jest w nawiasach i założyć, że wycieki będą pochodzić z uruchomionego kodu, a nie z kodu źródłowego przeglądarki.

![[Pasted image 20240714230751.png]]

![[Pasted image 20240714230959.png]]

### References

https://www.codecademy.com/courses/learn-javascript-best-practices/articles/javascript-debugging-memory-issues
---



