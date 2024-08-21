--- 
tags: [[React]]
date: 2024-08-19

---
### <span style="color: #d11141;">Co to są komponenty w React?</span>

**React Components** to podstawowe elementy budowy aplikacji w React. Komponenty pozwalają na tworzenie interaktywnych interfejsów użytkownika poprzez dzielenie UI na mniejsze, niezależne części (bloki), które mogą być łatwo zarządzane i wielokrotnie używane. Komponenty mogą być tworzone jako funkcje lub klasy.

React wykorzystuje komponenty do efektywnego zarządzania stanem i logiką aplikacji, co pozwala na tworzenie dynamicznych i złożonych interfejsów użytkownika.

#### Komponent to najczęściej funkcja JavaScript, która musi spełniać 2 warunki:

![[Pasted image 20240819223129.png]]

Plik z rozszerzeniem `App.jsx` zawiera HTML kod wewnątrz funkcji JavaScript. 

![[Pasted image 20240819224943.png]]
![[Pasted image 20240819223644.png]]
### <span style="color: #00b159;">Rodzaje komponentów</span>

- **Komponenty funkcyjne:** Są to proste funkcje, które przyjmują `props` (właściwości) jako argument i zwracają elementy Reacta (czyli opis tego, co ma zostać wyrenderowane).

- **Komponenty klasowe:** Są bardziej rozbudowane i mogą posiadać swój własny stan (`state`) oraz metody cyklu życia, umożliwiając bardziej zaawansowaną logikę.

### <span style="color: #00aedb;">Zalety komponentów</span>

![[Pasted image 20240819221031.png]]

Różne odpowiedzialności komponentów w React np.:

1.  Wyświetlanie głównego tytułu, podtytułu i obrazu.
2. Wyświetlanie informacji o kluczowych konceptach.
3. Obsługa interakcji użytkownika i przełączanie między zakładkami.

### <span style="color: #f37735">Drzewo komponentów</span>

Hierarchia komponentów w React, często nazywana "drzewem komponentów" (React component tree), jest strukturą, która przedstawia sposób organizacji komponentów w aplikacji. Każdy Reactowy komponent może mieć jeden lub więcej komponentów potomnych, tworząc w ten sposób drzewo zależności.

![[Pasted image 20240819230224.png]]

Ważne, że w docelowym drzewie DOM są pokazywane jedynie główne komponenty (te z małej litery, te stworzone przez nas są z dużej). Te wbudowane a nie zcustomowane przez nas.

![[Pasted image 20240819231334.png]]

![[Pasted image 20240819230341.png]]

### <span style="color: #ffc425;">Dynamiczne komponenty</span>

Wstawiamy je za pomocą nawiasów wąsów `{odwołanieDoKomponentu}`. Co ważne w nawiasach nie można wstawiać pętli for, if itp., jedynie wyrażenia, które bezpośrednio produkują wartość.

![[Pasted image 20240820151832.png]]


### References:
https://codesandbox.io/p/sandbox/react-essentials-start-gsmr8r?file=%2Fsrc%2Fstyles.css
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649010#overview
---



