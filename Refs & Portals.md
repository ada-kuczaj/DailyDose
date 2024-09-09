--- 
tags: [[React]]
date: 2024-09-05

---
### <span style="color: #d11141;">Refs</span>

`Refs` pozwalają na bezpośredni dostęp do elementów DOM lub elementów Reacta. Umożliwiają manipulowanie DOM poza standardowym cyklem renderowania Reacta.

**Kiedy używać:**

- Zarządzanie fokusem (np. pola input).
- Wywoływanie animacji lub zaznaczanie tekstu.
- Integracja z bibliotekami zewnętrznymi, które manipulują DOM bezpośrednio.
- Odczytywanie wartości komponentu podrzędnego bez ponownego renderowania.

```jsx
import { useRef, useEffect } from 'react';

function MyComponent() {
  const inputRef = useRef(null);

  useEffect(() => {
    inputRef.current.focus(); // Automatyczne ustawienie fokusu na polu input po zamontowaniu komponentu
  }, []);

  return <input ref={inputRef} type="text" />;
}
```

### <span style="color: #ffc425;">Portals</span>

Portale umożliwiają renderowanie dzieci do węzła DOM znajdującego się poza hierarchią nadrzędną komponentu. Jest to przydatne do wyświetlania elementów, które muszą znajdować się poza standardowym drzewem DOM, takich jak modale czy tooltipy.

**Kiedy używać:**

- Renderowanie modali, tooltipów lub popoverów, które muszą nakładać się na inne elementy, nie naruszając układu.
- Wyświetlanie elementów w innej części drzewa DOM, zachowując logikę renderowania Reacta.

```jsx
import { createPortal } from 'react-dom';

function Modal({ children }) {
  return createPortal(
    <div className="modal">{children}</div>,
    document.getElementById('modal-root') // Renderowanie modala w innym węźle DOM
  );
}
```


![[Pasted image 20240905222235.png]]
### <span style="color: #00b159;">useImperativeHandle</span>

- Umożliwia dostosowanie wartości instancji, która jest przekazywana do komponentu nadrzędnego poprzez `ref`. Stosuje się go razem z `forwardRef`, aby ograniczyć to, co jest udostępniane przez komponent.

- **Kiedy używać**: Gdy chcesz kontrolować, jakie metody lub właściwości komponentu są dostępne dla rodzica za pomocą `ref`.
### <span style="color: #00aedb;">Closing the Modal via the ESC (Escape) Key</span>

- **Zamykanie modali za pomocą klawisza ESC**: Można to zaimplementować, dodając nasłuchiwacz zdarzeń dla `keydown` i sprawdzając, czy naciśnięto klawisz `Escape`.

- **Kiedy używać**: Aby poprawić doświadczenie użytkownika, pozwalając mu łatwo zamknąć okno modalne za pomocą klawiatury.
#### **Element `<dialog>`**

- **`<dialog>`**: Natywny element HTML5 używany do tworzenia okna dialogowego lub wyskakującego. Obsługuje atrybuty takie jak `open` do wyświetlania okna oraz metodę `showModal()`, aby go otworzyć.

- **Kiedy używać**: Do prostych okien dialogowych, modali lub wyskakujących potwierdzeń. Jest wbudowany w HTML, więc nie wymaga JavaScriptu do podstawowego użycia.
### <span style="color: #f37735">createPortal</span>

- **`createPortal`**: Metoda Reacta, która pozwala na renderowanie dzieci komponentu w innym poddrzewie DOM, poza hierarchią DOM rodzica.

- **Kiedy używać**: Do renderowania elementów takich jak modale, tooltipy czy rozwijane menu, gdzie trzeba upewnić się, że element jest renderowany poza standardową strukturą DOM.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39836296#overview

---



