--- 
tags: [[React]]
date: 2024-08-26

---
**Lifting the State Up** to wzorzec w React, który polega na przeniesieniu stanu (state) do najbliższego wspólnego przodka (rodzica) komponentów, które ten stan potrzebują. Jest to kluczowa koncepcja, która umożliwia efektywne dzielenie się danymi pomiędzy komponentami.

![[Pasted image 20240826193052.png]]
### <span style="color: #d11141;">Kiedy stosować Lifting the State Up?</span>

- **Komunikacja między komponentami**: Gdy dwa lub więcej komponentów muszą współdzielić te same dane, stan należy przenieść do najbliższego wspólnego komponentu nadrzędnego (parent component).

- **Synchronizacja stanu**: Przeniesienie stanu do wspólnego rodzica pozwala na lepszą synchronizację danych między komponentami, które ten stan używają lub zmieniają.
### <span style="color: #00b159;">Jak to działa?</span>

1. **Identyfikacja wspólnego rodzica**: Zaczynamy od znalezienia najbliższego wspólnego przodka komponentów, które muszą korzystać z tego samego stanu.

2. **Przeniesienie stanu**: Przenosimy stan do komponentu nadrzędnego i przekazujemy go do dzieci (komponentów podrzędnych) za pomocą propsów.

3. **Obsługa zmian stanu**: Gdy stan ma się zmieniać w jednym z komponentów podrzędnych, tworzymy funkcję do aktualizacji stanu w komponencie nadrzędnym, którą również przekazujemy jako prop do odpowiedniego komponentu dziecka.


```jsx
function ParentComponent() {
  const [sharedValue, setSharedValue] = useState('');

  return (
    <>
      <InputComponent value={sharedValue} onChange={setSharedValue} />
      <DisplayComponent value={sharedValue} />
    </>
  );
}

function InputComponent({ value, onChange }) {
  return <input value={value} onChange={(e) => onChange(e.target.value)} />;
}

function DisplayComponent({ value }) {
  return <p>{value}</p>;
}
```

W tym przykładzie stan `sharedValue` znajduje się w `ParentComponent`, a `InputComponent` oraz `DisplayComponent` korzystają z tego stanu dzięki przekazywaniu propsów.

### <span style="color: #00aedb;">Zalety</span>

- **Lepsza kontrola nad stanem**: Gdy stan jest zarządzany w jednym miejscu, łatwiej go śledzić i kontrolować.

- **Unikanie duplikacji**: Przenoszenie stanu do wspólnego przodka zapobiega konieczności duplikowania stanu w różnych komponentach.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659800#content

---



