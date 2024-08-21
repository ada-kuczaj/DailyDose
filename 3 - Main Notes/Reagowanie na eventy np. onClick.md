--- 
tags: [[React]]
date: 2024-08-21

---
### <span style="color: #d11141;">Jak działa obsługa eventów w React?</span>

React obsługuje eventy poprzez przypisanie ==funkcji== do atrybutów JSX, takich jak `onClick`, `onChange`, `onSubmit` i wiele innych. Ponieważ chcemy wskazać na funkcję, która powinna zostać wyegzekwować gdy ten event się wydarzy. Te atrybuty są napisane w camelCase (np. `onClick` zamiast `onclick`), co odróżnia je od tradycyjnych eventów w HTML. Są wbudowane w React.

Aby zdefiniować funkcję, która ma obsłużyć zdarzenie możemy skorzystać z możliwości zdefiniowania funkcji wewnątrz innych funkcji na co pozwala nam JS i stworzyć takową w komponencie (który też jest funkcją).

> [!WARNING]  UWAGA
> Wewnątrz nawiasów wąsów nie przypisujemy funkcji z nawiasami, tylko samą jej nazwę tak, aby została wywołana przez React faktycznie po kliknięciu w guzik. Chcemy użyć funkcji jako wartości, która została przekazana do onClick prop.

W tradycyjnym Javascripcie obsługa eventów odbywała by się za pomocą poniższego kodu:
![[Pasted image 20240821215400.png]]
Jednak używając Reacta bardzo nie chcemy wchodzić w interakcje z DOM i ze stroną w ten sposób.

![[Pasted image 20240821220450.png]]


## Co dalej? Jak to działa?

Mamy tutaj niestandardowe komponenty, nie mamy tutaj wbudowanego komponentu przycisku. Dlatego, oczywiście, aby ustawić i zaktualizować tę dynamiczną zawartość, musimy przede wszystkim nasłuchiwać kliknięć naszego niestandardowego przycisku. W tym celu ważne jest, aby pamiętać, że nasze niestandardowe przyciski, podobnie jak wszystkie niestandardowe komponenty, po prostu owijają natywne elementy HTML, a dokładniej natywne elementy JSX. Tak więc wbudowane komponenty dostarczane przez React. Te wbudowane przyciski mają na przykład wbudowaną właściwość onClick. Dlatego, aby nasze własne przyciski `TabButton` były klikalne, ostatecznie chcemy ustawić wartość dla tej właściwości onClick na tym wbudowanym przycisku spoza naszego niestandardowego komponentu, z wnętrza komponentu aplikacji w tym przypadku (App.jsx), aby być precyzyjnym.

![[Pasted image 20240821230434.png]]
#### Kroki do Ustawiania Dynamicznych Właściwości:

1. **Tworzenie niestandardowego komponentu**:
    - Zdefiniuj niestandardowy komponent (np. `TapButton`), który przyjmuje propsy. Nazwa propsa może być dowolna, ale często stosuje się konwencję nazewnictwa od "on" (np. `onSelect`).
    
2. **Przekazanie funkcji jako props**:
    - W komponencie nadrzędnym (np. `App`), zdefiniuj funkcję (np. `handleSelect`), która zostanie wywołana, gdy wystąpi zdarzenie (np. kliknięcie przycisku).
    - Przekaż tę funkcję jako wartość do propsa `onSelect` w komponencie `TapButton`.
    
3. **Przypisanie propsa do natywnego elementu**:
    - Wewnątrz komponentu `TapButton`, przekaż otrzymany props (np. `onSelect`) do odpowiedniego natywnego elementu JSX (np. `button`), używając wbudowanej właściwości (np. `onClick`).

4. **Reakcja na zdarzenie**:
    - Kiedy użytkownik kliknie przycisk, React uruchomi przekazaną funkcję (`handleSelect`), co umożliwi zaktualizowanie stanu lub wykonanie innych akcji w komponencie nadrzędnym.



### **Wzorzec przekazywania funkcji jako właściwości w komponentach React**

#### Dynamiczna Zawartość na Podstawie Zdarzeń

Reagowanie na kliknięcie przycisku umożliwia nam aktualizację dynamicznej zawartości w komponencie nadrzędnym. Zamiast jedynie wywoływać funkcję, możemy również zaktualizować stan komponentu nadrzędnego, co bezpośrednio wpłynie na renderowaną zawartość.
#### Dlaczego to Jest Ważne?

Reagowanie na zdarzenia bezpośrednio w komponentach podrzędnych, takich jak `TabButton`, nie byłoby wystarczające, ponieważ komponenty te nie mają dostępu do całego kontekstu aplikacji. Dlatego przekazanie funkcji jako wartości do właściwości, a następnie wywołanie jej w odpowiednim momencie (np. po kliknięciu przycisku), jest kluczowe dla zarządzania dynamiczną zawartością w aplikacji React.

Dzięki temu wzorcowi możemy teraz w prosty sposób ustawić funkcję obsługującą zdarzenie dla wszystkich przycisków `TabButton`. To pozwala na bardziej zorganizowane i modularne zarządzanie logiką zdarzeń w aplikacji.



### **Różnica między kodem przed refaktoryzacją a po refaktoryzacji**

#### 1. Pierwotny kod w `TabButton.jsx`:

- Funkcja `handleClick` była zdefiniowana bezpośrednio w komponencie `TabButton`.
- Kiedy użytkownik klikał przycisk, wywoływana była funkcja `handleClick`, która logowała tekst "Hello World!".
- Problem: Funkcja `handleClick` była statyczna i niezależna od komponentu nadrzędnego (`App`). Nie można było dynamicznie zmieniać zachowania w zależności od kontekstu aplikacji.

#### 2. Zrefaktoryzowany kod z `handleSelect` w `App.jsx`:

- Funkcja `handleSelect` została przeniesiona do komponentu `App`, gdzie jest przekazywana jako props (`onSelect`) do komponentu `TabButton`.
- Dzięki temu `TabButton` może wywołać `handleSelect`, która znajduje się w komponencie nadrzędnym. Pozwala to na dynamiczną reakcję na kliknięcie przycisku w kontekście całej aplikacji.
- **Zaleta**: Teraz `TabButton` jest bardziej uniwersalny i może być używany w różnych kontekstach z różnymi funkcjami. To zwiększa elastyczność i reużywalność komponentów, ponieważ logika dotycząca obsługi zdarzeń jest centralizowana w komponencie nadrzędnym (`App`).



### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649204#overview - Sekcja 3: lekcja 51.

---



