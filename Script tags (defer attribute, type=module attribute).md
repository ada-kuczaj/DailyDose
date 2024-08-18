--- 
tags: [[JS]]
date: 2024-08-18

---
### <span style="color: #ffc425;">defer attribute</span>

Tag `<script defer>` w HTML służy do ładowania skryptu JavaScript w sposób asynchroniczny, ale z pewnym opóźnieniem w jego wykonaniu. Oznacza to, że skrypt zostanie pobrany w tle podczas ładowania strony, ale zostanie wykonany dopiero po zakończeniu ładowania całego dokumentu HTML.

Użycie `defer` jest szczególnie przydatne w przypadku skryptów, które modyfikują DOM, ponieważ gwarantuje, że cała struktura dokumentu HTML będzie już w pełni załadowana, zanim skrypt zacznie działać.

```html
<script src="assets/scripts/app.js" defer></script>
```


### <span style="color: #00aedb;">type="module" attribute</span>

Atrybut `type="module"` w tagu `<script>` wprowadza wsparcie dla modułów JavaScript. Moduły pozwalają na podział kodu na mniejsze, bardziej zorganizowane i wielokrotnego użytku części, które mogą być importowane do innych plików.

```html
<script src="assets/scripts/app.js" type="module"></script>

//lub

<script type="module">
  import { myFunction } from './myModule.js';
  myFunction();
</script>
```

- **Import i eksport:** Moduły mogą importować i eksportować zmienne, funkcje, klasy itp. z innych modułów. Dzięki temu można dzielić kod na mniejsze fragmenty i organizować go w logiczny sposób.

- **Domyślna izolacja zakresu (scope):** Kod w module jest domyślnie izolowany (ma własny scope). Zmienne i funkcje zadeklarowane w module nie będą dostępne globalnie, chyba że zostaną wyraźnie eksportowane.

- **Asynchroniczne ładowanie:** Podobnie jak z atrybutem `defer`, moduły są ładowane asynchronicznie. Oznacza to, że nie blokują renderowania strony, ale są wykonywane po załadowaniu całego HTML-a.

- **Ściślejsze zasady (strict mode):** Moduły działają w trybie "use strict" domyślnie, co oznacza, że JavaScript będzie sprawdzany bardziej rygorystycznie (np. nie można używać niezadeklarowanych zmiennych).


> [!IMPORTANT] UWAGA
> W przypadku aplikacji napisanych w React, zarządzanie skryptami i modułami jest nieco inne, ponieważ React jest zwykle budowany przy użyciu narzędzi do bundlowania i transpilacji, takich jak Webpack, Vite czy Parcel. Te narzędzia automatycznie zajmują się wieloma aspektami ładowania i zarządzania modułami, więc atrybuty takie jak `type="module"` i `defer` nie są bezpośrednio używane w plikach HTML generowanych przez React.
> 
> Biblioteka `react-scripts` automatyzuje proces budowania aplikacji React, zarządzając całą konfiguracją narzędzi i transformacją kodu "za kulisami".

![[Pasted image 20240818204314.png]]



### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/38345170#content

---



