--- 
tags: [[React]]
date: 2024-08-21

---
### <span style="color: #d11141;">Budowanie reużywalnych komponentów za pomocą Props</span>

**Props** (skrót od _properties_) są jednym z podstawowych mechanizmów w React, używanym do przekazywania danych pomiędzy komponentami. W React, komponenty są jak funkcje JavaScript, które przyjmują argumenty i zwracają elementy React. Te argumenty nazywane są właśnie "props".

#### Główne zastosowanie props:
Props są kluczowym elementem w React, ponieważ umożliwiają tworzenie komponentów wielokrotnego użytku. Możesz tworzyć komponenty, które przyjmują różne dane przez props i renderują różne wyniki na ich podstawie, bez potrzeby modyfikowania samego komponentu.


![[Pasted image 20240821175133.png]]

![[Pasted image 20240821180518.png]]
### <span style="color: #00b159;">Jak działają props?</span>

Props są przekazywane do komponentów podobnie jak argumenty do funkcji. Gdy tworzysz komponent i chcesz przekazać do niego dane, robisz to za pomocą atrybutów JSX, które stają się właściwościami w obiekcie `props`.

![[Pasted image 20240821181540.png]]

![[Pasted image 20240821180804.png]]

Można ułatwić i skrócić sobie pracę tworząc w osobnym pliku tablicę obiektów z treścią strony internetowej, która ma się znaleźć w poszczególnych komponentach i odwoływać się do niej jedynie zmieniając indeksy: 

![[Pasted image 20240821182208.png]]

![[Pasted image 20240821182222.png]]

Aby nie powielać tylu podobnych linii kodu, jeżeli nazwy naszych odwołań/atrybutów w props zgadzają się z nazwami atrybutów obiektów  w pliku zawierającym tablicę z obiektami, możemy odwołać się bezpośrednio do niej za pomocą właściwości `...` (_spread operator_), która wyciągnie wszystkie potrzebne nam wartości:

![[Pasted image 20240821183320.png]]
![[Pasted image 20240821182455.png]]

### <span style="color: #00aedb;">Ważne cechy props</span>

1. **Nie mutowalne:** Props są "read-only" (tylko do odczytu). To oznacza, że komponenty nie mogą modyfikować własnych props. Są one stałe w obrębie komponentu.

2. **Przekazywanie danych**: Props pozwalają na przekazywanie danych z komponentu nadrzędnego do komponentu podrzędnego. To jest sposób, w jaki dane przepływają przez aplikację React od rodzica do dziecka.

3. **Dynamika**: Props mogą być dynamiczne. Oznacza to, że możemy przekazywać zmienne, wyrażenia, funkcje i inne komponenty jako props, co pozwala na tworzenie bardziej elastycznych i dynamicznych komponentów.


### <span style="color: #f37735">Przykład dynamicznych props</span>

```js
function App() {
  const user = {
    firstName: "Jane",
    lastName: "Doe"
  };

  return <Welcome name={`${user.firstName} ${user.lastName}`} />;
}
```


### <span style="color: #ffc425;">Props vs State</span>

- Props są przekazywane do komponentu i są przez niego wykorzystywane, ale komponent nie ma nad nimi kontroli (nie może ich zmieniać).
- State jest zarządzany wewnątrz komponentu i może być zmieniany przez komponent (np. w odpowiedzi na akcje użytkownika).


### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649022#overview

---



