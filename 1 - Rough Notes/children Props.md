--- 
tags: [[React]] [[Props w Komponentach React]]
date: 2024-08-21

---

W React, `children` to specjalny prop, który pozwala przekazywać elementy potomne do komponentu. Dzięki temu możemy tworzyć elastyczne i wielokrotnego użytku komponenty, które mogą być wypełniane różną zawartością w zależności od kontekstu.

### <span style="color: #00b159;">Jak działa `children`?</span>

Gdy tworzysz komponent w React, możesz go zdefiniować tak, aby akceptował elementy potomne. `children` to niejawny prop, który zawiera wszystkie elementy znajdujące się wewnątrz tagów komponentu, w którym go używasz.

![[Pasted image 20240821210430.png]]

![[Pasted image 20240821210504.png]]


W powyższym kodzie, zawartość pomiędzy tagami `<TabButton>` a `</TabButton>`  jest przekazywana jako `children` do komponentu `TabButton`. W rezultacie, komponent `TabButton` wyświetli te elementy wewnątrz swojego `button`.

![[Pasted image 20240821211345.png]]


### <span style="color: #00aedb;">Component Composition</span>

**Component Composition** to koncepcja w React, która polega na tworzeniu złożonych interfejsów użytkownika poprzez łączenie i osadzanie prostszych, mniejszych komponentów w większe, bardziej złożone struktury. Dzięki tej technice możliwe jest tworzenie aplikacji w sposób modularny, reużywalny i łatwy do zarządzania.

#### Zaawansowane użycie Component Composition

W bardziej złożonych scenariuszach, Component Composition może obejmować takie techniki jak **"container and presentational components"**, **"higher-order components (HOC)"**, **"render props"**, czy **"composition with children"**.

![[Pasted image 20240821211126.png]]


### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649200#overview

---



