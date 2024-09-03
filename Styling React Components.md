--- 
tags: [[React]]
date: 2024-08-27

---
### <span style="color: #00b159;">Styling React Apps:</span>

#### **1. Styling with Vanilla CSS**

`index.css` jeden plik w projekcie ze zdefiniowanymi wszystkimi CSS-ami. Za pomocą element selektorów, id lub klas. Import plików CSS do plików JS (zostaje wstrzyknięty dzięki VITE) w `main.jsx`: 

![[Pasted image 20240831225301.png]]

![[Pasted image 20240831223937.png]]

Zamiast tego można dodać dowolną liczbę plików .css i można podzielić ten jeden wyjściowy plik na wiele plików, dołączając poszczególne pliki css do komponentów, do których należą.
`Header.jsx` i `Header.css` w folderze components + import w `main.jsx`.

![[Pasted image 20240831224446.png]]

Jedną z wad korzystania z Vanilla CSS jest to, że reguły CSS i ogólnie kod CSS nie są ograniczone 
do komponentu, do którego chcesz, aby należały, co może powodować konflikty w całej aplikacji.

Dlatego naprawdę ważne jest, aby zrozumieć, że nawet jeśli podzielisz swój kod CSS na wiele plików, a następnie zaimportujesz niektóre z tych plików do określonych plików komponentów, 
reguły CSS w tych plikach nie będą przypisane do komponentów, do których należą, ponieważ tak naprawdę nie należą do tych komponentów.

![[Pasted image 20240831225035.png]]

Zamiast tego, jeśli ponownie otworzysz narzędzia deweloperskie, pamiętaj, że wszystkie te style są ostatecznie wstrzykiwane do sekcji `head` przez Vite, więc style nagłówka i inne style. Dlatego są one oczywiście stosowane globalnie do tej strony.



#### **2. Inline Styles**

 Co możemy z tym zrobić, jeśli chcemy osiągnąć pewien scope? Jednym z rozwiązań byłoby przejście na  Inline Styles. Style inline oznaczają, że zamiast definiować style CSS w pliku CSS, stosujesz je bezpośrednio w kodzie JSX.
 
 Używamy do tego tyle prop i obiektu. Właściwość stylu przyjmuje wartość dynamiczną, dlatego potrzebujemy nawiasów klamrowych otwierających i zamykających, a następnie przekazujemy obiekt jako wartość do właściwości stylu.
 
![[Pasted image 20240831230419.png]]

![[Pasted image 20240831225905.png]]

#### Dynamic & Conditional Inline Styles

![[Pasted image 20240901194108.png]]

![[Pasted image 20240901195028.png]]

#### **3. Scoping Styles with CSS Modules**

CSS Modules to sposób na organizowanie stylów CSS, który pozwala na uniknięcie konfliktów nazw klas i stylów w dużych projektach. Jest to podejście, które izoluje style CSS do konkretnego komponentu, dzięki czemu klasy są lokalne dla danego komponentu, a nie globalne, co zapobiega przypadkowemu nadpisaniu stylów.

### Jak to działa:
1. **Lokalne klasy**: Każda klasa CSS w module CSS jest domyślnie lokalna. Oznacza to, że klasy są unikalne tylko dla danego komponentu i nie będą kolidować z innymi klasami w projekcie.
   
2. **Mapowanie klas**: Klasy są kompilowane do unikalnych nazw w postaci hashy (np. `.button {}` może zostać przekształcone w `.button_hash1234 {}`). Dzięki temu, nawet jeśli w innych komponentach używasz klasy `.button`, te style się nie nadpiszą.
   
3. **Importowanie stylów**: W kodzie JavaScript (np. w React) importujesz moduły CSS jako obiekty. Możesz odwoływać się do klas CSS jako właściwości tego obiektu.

![[Pasted image 20240901200256.png]]

![[Pasted image 20240901200306.png]]
![[Pasted image 20240901200338.png]]

 Ta nowa nazwa klasy została ostatecznie wygenerowana automatycznie przez wbudowane narzędzie kompilacji. I to jest właśnie idea modułów CSS. Ta nazwa klasy jest teraz unikalna dla tego komponentu. CSS modułu jest przekształcany przez ten proces. Zatem ten proces kompilacji ostatecznie zapewnia, że style mojej klasy są przypisane do pliku komponentu, w którym je importuję.

![[Pasted image 20240901201003.png]]


#### **4. CSS-in JS Styling with "Styled Components"**

Jest to pakiet komponentów stylizowanych, który można wykorzystać w projektach React.
Idea tego popularnego pakietu polega na tym, że nie definiujesz reguł i stylów CSS w osobnych plikach CSS, ale także nie jako style wbudowane, ale zamiast tego w specjalnych komponentach, które są budowane za pomocą tego pakietu.

![[Pasted image 20240901201225.png]]
![[Pasted image 20240901201518.png]]

==Tagged template== literals to zaawansowana funkcja w JavaScript, która pozwala na manipulowanie szablonami dosłownymi (template literals) przed ich ostatecznym przetworzeniem. Dzięki temu możesz dynamicznie modyfikować wartości w szablonie, zanim zostaną one połączone w jeden ciąg znaków.

![[Pasted image 20240901203647.png]]


W tle ten pakiet styled-components po prostu tworzy unikalne nazwy klas CSS i definiuje reguły dla tych klas w sekcji head, gdzie są one wstrzykiwane.

![[Pasted image 20240901203708.png]]

Style są teraz bliżej kodu JSX, ale nie znajdują się wewnątrz kodu JSX i nie mamy duplikacji w kodzie JSX. Zamiast tego otrzymujemy te małe komponenty opakowujące, które zbudowaliśmy za pomocą komponentów stylizowanych.

#### Dynamic & Conditional Styling with Styled Components

![[Pasted image 20240901205459.png]]![[Pasted image 20240901205518.png]]


Jedną rzeczą, na którą należy zwrócić uwagę przy wstrzykiwaniu props do stylizowanych komponentów, jest to, że oczywiście należy upewnić się, że przypadkowo nie kolidują one z domyślnymi wbudowanymi props, które mogą istnieć w niektórych elementach.

Powszechną konwencją jest poprzedzanie tych propsów, które mają być używane tylko 
w kodzie stylizacji komponentu, znakiem dolara (`$`). Jest to nadal prawidłowa nazwa właściwości, więc jest to dozwolone w JavaScript, ale nie będzie kolidować z wbudowanymi właściwościami.

![[Pasted image 20240901210528.png]]
![[Pasted image 20240901210211.png]]

#### Styled Components: Pseudo Selectors, Nested Rules & Media Queries

- **Media Queries (Zapytania o media)**: Pokazuje, jak używać zapytań o media w komponentach stylizowanych, aby dostosować styl do różnych rozmiarów ekranu, urządzeń lub orientacji.
    
- **Pseudo-selektory**: Przedstawia sposób pracy z pseudo-selektorami, takimi jak `:hover`, `:focus`, czy `:active`, umożliwiając dodawanie efektów interakcji (np. zmiana koloru po najechaniu na przycisk) w komponentach stylizowanych.
    
- **Zagnieżdżone reguły**: Omawia, jak konfigurować zagnieżdżone reguły CSS w komponentach stylizowanych, co pozwala na lepszą organizację kodu i nadawanie stylów elementom potomnym bez potrzeby pisania długich, specyficznych selektorów.

![[Pasted image 20240902224538.png]]

Symbol `&` powie stylizowanym komponentom, że ta reguła powinna wpływać na wszystkie elementy obrazu, które znajdują się wewnątrz tego `header`, a więc są zagnieżdżone wewnątrz tego `header`.

Oto jak łatwo jest skonfigurować stylizowany komponent, który również  stylizuje swoje elementy podrzędne i wykorzystuje funkcje takie jak media Query.

Jak widać, jest to standardowy kod CSS. Nie musieliśmy zmieniać tego kodu i nie trzeba konwertować każdego elementu na komponent stylizowany tylko po to, aby go stylizować. Zamiast tego można po prostu przekonwertować jeden komponent nadrzędny, a następnie dodać do niego style w ten sposób.


#### Creating Reusable Components & Component Combinations

![[Pasted image 20240902230246.png]]
![[Pasted image 20240902230749.png]]
![[Pasted image 20240902230800.png]]
Jako programista Reacta powinieneś zawsze szukać takich możliwości, w których możesz albo uzyskać komponenty wielokrotnego użytku, które mają zastosowany określony styling, którego możesz potrzebować w różnych częściach aplikacji, i/lub komponenty, które mogą mieć określone kombinacje elementów JSX (np. label i input), które możesz  potrzebować do ponownego wykorzystania w innych częściach aplikacji.

![[Pasted image 20240902230209.png]]



#### **5. Styling with Tailwind CSS**

**Tailwind CSS** to kolejne niezwykle popularne rozwiązanie do stylizacji aplikacji  internetowych w ogóle, nie tylko aplikacji React, które jednak okazuje się działać naprawdę dobrze z Reactem. Teraz Tailwind CSS to framework CSS, który może być używany w każdym projekcie internetowym. Jak widać, Tailwind polega na dodawaniu do elementów HTML niewielkich klas CSS, aby stosować style krok po kroku, a tym samym stylizować cały komponent.

![[Pasted image 20240902231712.png]]

![[Pasted image 20240902232100.png]]![[Pasted image 20240902232017.png]]

Integracja Tailwind CSS z komponentami w aplikacji React to popularne podejście, które łączy zalety Tailwind CSS (użycie gotowych klas utility-first) z elastycznością React.

Rozszerzenie/wtyczka:
![[Pasted image 20240902232536.png]]

![[Pasted image 20240902233430.png]]

![[Pasted image 20240902232947.png]]

Podstawową ideą Tailwind CSS jest dodanie tych niewielkich klas CSS do elementów, aby zmienić ich wygląd, zastosować predefiniowane reguł CSS, które zostały zdefiniowane przez zespół Tailwind w dokumentacji i które są dostępne za pośrednictwem tych klas narzędzi. Można customizować elementy np. czcionkę lub tło strony.


![[Pasted image 20240903220337.png]]![[Pasted image 20240903220351.png]]


#### Dynamic & Conditional Styling with Tailwind

![[Pasted image 20240903222311.png]]

![[Pasted image 20240903222937.png]]


### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39835916#overview
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates
https://tailwindcss.com/docs/guides/vite
---



