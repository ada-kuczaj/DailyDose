--- 
tags: [[React]]
date: 2024-08-22

---
### <span style="color: #ffc425;">Sposób 1 - dynamicznie w zależności od zmieniającej się długości tablicy w osobnym pliku</span>

W tym podejściu użyto funkcji `map`, aby przeiterować przez całą tablicę `CORE_CONCEPTS` i dla każdego elementu utworzyć komponent `CoreConcept`. Każdy element tablicy jest przekazywany jako `conceptItem`, który następnie jest destrukturyzowany (`...conceptItem`) i przekazywany jako propsy do komponentu `CoreConcept`.

- **Zalety**: To najbardziej dynamiczne podejście. Automatycznie renderuje wszystkie elementy z tablicy `CORE_CONCEPTS`, niezależnie od tego, ile ich jest. Dodanie lub usunięcie elementu z tej tablicy automatycznie spowoduje aktualizację listy renderowanych komponentów.

- **Wady**: Wymaga mapowania tablicy, co może być nieco bardziej skomplikowane w zależności od struktury danych i sposobu ich wykorzystania.


![[Pasted image 20240822203122.png]]


### <span style="color: #f37735">Sposób 2 bezpośrednie odwołanie się do poszczególnych elementów w tablicy (nazwy muszą się zgadzać)</span> 

W tym podejściu komponent `CoreConcept` jest tworzony ręcznie, a dane są przekazywane do niego przez bezpośrednie odwołanie się do poszczególnych elementów w tablicy `CORE_CONCEPTS`.

- **Zalety**: Podejście to jest bardziej przejrzyste, gdy mamy do czynienia z niewielką ilością danych lub gdy chcemy wyświetlić tylko konkretny element z tablicy.
- **Wady**: Jest mniej elastyczne. Jeśli liczba elementów w `CORE_CONCEPTS` zmieni się, będziesz musiał ręcznie dostosować ten kod, aby odzwierciedlał nową strukturę.

![[Pasted image 20240822203231.png]]


### <span style="color: #00aedb;">Sposób 3 - całe obiekty z tablicy danych są przekazywane do komponentów przez destrukturyzację</span>

W tym podejściu komponenty `CoreConcept` są również tworzone ręcznie, ale całe obiekty z tablicy `CORE_CONCEPTS` są przekazywane do komponentów przez destrukturyzację (`...CORE_CONCEPTS[index]`).

- **Zalety**: W porównaniu do drugiego podejścia, jest bardziej zwięzłe i pozwala na przekazanie wszystkich właściwości obiektu bez konieczności ich wyliczania. Jeśli struktura obiektu zmieni się, to podejście nadal będzie działać, pod warunkiem, że komponent `CoreConcept` obsługuje nową strukturę.

- **Wady**: Podobnie jak w drugim podejściu, jest to mniej elastyczne pod względem ilości elementów w tablicy `CORE_CONCEPTS`. Dodatkowo, jeśli obiekt zawiera wiele właściwości, które nie są potrzebne, może być mniej wydajne niż dokładne przekazanie tylko potrzebnych danych.

![[Pasted image 20240822203555.png]]


> [!IMPORTANT]  KEY PROP
> TRZEBA TO DODAĆ! WAŻNE!
> W React, `key` to specjalny prop, który pomaga w efektywnym zarządzaniu i renderowaniu list elementów. Jest on kluczowy dla śledzenia, które elementy zostały dodane, usunięte lub zmodyfikowane w liście elementów. `key` jest używany wewnętrznie przez React do optymalizacji procesu aktualizacji wirtualnego DOM.

Gdy React renderuje listę elementów, musi mieć sposób na odróżnienie poszczególnych elementów w tej liście. Bez unikalnego klucza React miałby trudności z określeniem, które elementy zostały zmienione, co mogłoby prowadzić do niepotrzebnych renderów lub błędów.

![[Pasted image 20240822204605.png]]

- **Unikalność**: `key` musi być unikalny w obrębie rodzeństwa (czyli elementów na tym samym poziomie hierarchii). React używa tego klucza do identyfikacji poszczególnych elementów w liście.

- **Stabilność**: `key` powinien być stabilny, co oznacza, że nie powinien się zmieniać między renderami, jeśli struktura listy pozostaje taka sama.
### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649260#overview

---



