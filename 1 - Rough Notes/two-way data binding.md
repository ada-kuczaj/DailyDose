--- 
tags: [[React]]
date: 2024-08-25

---
Dwukierunkowe wiązanie danych (ang. **two-way data binding**) to technika, w której dane w aplikacji są zsynchronizowane w obu kierunkach pomiędzy widokiem (np. interfejsem użytkownika) a modelem danych. Oznacza to, że gdy dane w modelu zmieniają się, aktualizuje się widok, a gdy użytkownik zmienia dane w widoku (np. wprowadza tekst w polu tekstowym), automatycznie aktualizuje się model danych.
### <span style="color: #d11141;">Dlaczego dwukierunkowe wiązanie jest istotne?</span>

- **Ułatwia synchronizację danych**: Dzięki niemu nie musisz ręcznie synchronizować wartości pomiędzy modelem a widokiem. To zmniejsza ilość kodu i ryzyko błędów

- **Zwiększa interaktywność aplikacji**: Gdy użytkownik wprowadza dane, natychmiast widzi ich wpływ na inne elementy interfejsu.


![[Pasted image 20240825230720.png]]

### Jak działa dwukierunkowe wiązanie danych:

- **Zmiana w widoku powoduje aktualizację stanu:** Kiedy użytkownik zmienia wartość w polu tekstowym (edytuje nazwę), `handleChange` zostaje wywołana. Funkcja ta pobiera nową wartość z pola tekstowego (`event.target.value`) i aktualizuje stan `playerName` za pomocą `setPlayerName`.

- **Zmiana stanu powoduje aktualizację widoku:** Zmieniona wartość `playerName` automatycznie aktualizuje wartość w polu tekstowym (`value={playerName}`) oraz w elemencie `<span>`, kiedy tryb edycji jest wyłączony.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659790#overview

---



