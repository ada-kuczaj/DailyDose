--- 
tags: [[React]]
date: 2024-08-23

---

**Forwarding Props** (przekazywanie propsów) to technika w React, która pozwala na przekazanie właściwości (props) z jednego komponentu do innego, często przez pośredni komponent. Jest to przydatne, gdy chcesz, aby komponenty, które nie bezpośrednio używają pewnych propsów, mogły je przekazać dalej do swoich dzieci.
### <span style="color: #d11141;">W czym problem?</span>

W przypadku gdy zaczynami posługiwać się komponentami w innych komponentach, możemy napotkać problem z importem css-ów i stylowaniem elementów i im potomnych elementów.

Chociaż ustawiamy ID w niestandardowym komponencie sekcji, nie używamy tego identyfikatora wewnątrz tego komponentu sekcji.

> [!IMPORTANT]  WAŻNE
>Kiedy ustawiasz props, czyli atrybuty, na niestandardowym komponencie, te atrybuty nie są automatycznie przekazywane do kodu JSX używanego wewnątrz tego komponentu.

![[Pasted image 20240823212013.png]]
![[Pasted image 20240823212626.png]]
![[Pasted image 20240823212248.png]]

### <span style="color: #f37735">Jak to rozwiązać?</span>

Używamy spread operator w dwóch różnych miejscach. Najpierw, aby pogrupować niektóre dane w obiekt i przy `<section>`, aby wydzielić niektóre potrzebne dane do innego elementu.

Użycie składni `...props` zapewni, że wszystkie dodatkowe props, które mogą być ustawione na naszym niestandardowym komponencie Section, zostaną przekazane do tego wbudowanego elementu Section.

Jest to bardzo użyteczny wzór przy tworzeniu wrapper components.

![[Pasted image 20240823213108.png]]
![[Pasted image 20240823213227.png]]


### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659752#content

---



