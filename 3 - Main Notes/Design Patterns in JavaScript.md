
--- 
tags: [[JS]]
date: 2024-07-14

---
W miarę rozwoju aplikacji, przemyślana kompozycja kodu nabiera znaczenia. W miarę dodawania elementów, trudno jest utrzymać, czytać lub ponownie używać kodu, jeśli relacje między tymi elementami nie są zaprojektowane z zamysłem. Bez przemyślanego projektowania bazy kodu, możesz spędzać więcej czasu na naprawianiu błędów i aktualizowaniu zduplikowanego kodu, zamiast pisać nowe funkcje.

Wzorce projektowe to systemy rozwiązań, a nie kod, który można bezpośrednio użyć. Wzorce dają nazwy i zasady rozwiązywania typów problemów, a rozwiązaniem jest implementacja obiektów i klas w celu rozwiązania problemu. W JavaScript są nawet wbudowane obiekty, które pomagają w implementacji niektórych typowych wzorców projektowych.

Rozwiązania wdrażające wzorce projektowe zazwyczaj są:

- DRY (Don’t repeat yourself)
- Modular
- Reusable
- Easier to maintain
- Easier to discuss with peers at a high level (vs diving into implementation details)

### Uwaga na antywzorce

Antywzorce opisują nieskuteczne rozwiązania problemów, które prowadzą do negatywnych skutków, takich jak:

- Zanieczyszczenie przestrzeni nazw (Namespace pollution) — nieoczekiwane zachowanie wynikające z interakcji różnych klientów
- Zwiększona złożoność kodu (Increased code complexity)
- Trudności w zrozumieniu i aktualizacji kodu
- Trudności z testowaniem i debugowaniem kodu

Zauważysz, że niektóre „zatwierdzone” wzorce projektowe również pojawiają się na liście antywzorców. W takich przypadkach, czy końcowy rezultat okaże się dobrym, czy złym wyborem, zależy od kontekstu implementacji. Dlatego ważne jest ocenienie rozwiązania i jego wpływu na bazę kodu podczas podejmowania decyzji projektowych.

### Niektóre typowe antywzorce to:

- **God Object**: Obiekt, który robi lub wie za dużo. Może początkowo wydawać się łatwiejsze mieć wszystkie właściwości i metody w jednym miejscu, ale może to powodować problemy podczas aktualizacji i utrzymania kodu.
- **Big Ball of Mud / Spaghetti Code**: Kod bez widocznej architektury. Trudno zlokalizować kod dla konkretnej funkcji i zrozumieć, od czego zależy.
- **Yo-Yo Problem**: Problem polegający na konieczności przemieszczania się między definicjami klas, aby zrozumieć dziedziczenie i działania klas.
- **Singleton**: Klasyczny wzorzec projektowy, ale jeśli jest używany niewłaściwie, może prowadzić do problemów ze względu na narzucane ograniczenia.
- **Zanieczyszczenie globalnej przestrzeni nazw**: Definiowanie zbyt wielu zmiennych na poziomie globalnym.
- **Modyfikowanie lub rozszerzanie prototypu klasy Object**: Wszystkie obiekty w JavaScript mają właściwość Prototype, która może być zmieniana metodami i właściwościami, a wszystkie nowe obiekty dziedziczą z tego podstawowego obiektu. Jednak zmiana prototypu jest bardzo niezalecana.


---

# Wzorce projektowe

Wzorce projektowe są zwykle grupowane w schemat klasyfikacji, który składa się z trzech kategorii opartych na celu:

- Creational (Kreacyjny/twórczy)
- Structural (Strukturalny)
- Behavioral (Behawioralny)

## Kategoria Kreacyjna

Wzorce kreacyjne są odpowiednie, gdy musisz kontrolować sposób tworzenia lub instancjonowania swoich obiektów. Obejmują one:

- Factory
- Singleton
- Abstract Factory
- Constructor
- Prototype

### Wzorzec Factory

Wyobraź sobie, że chcesz śledzić swoją listę książek — każda książka miałaby tytuł, autora, liczbę stron, rok wydania, status czytania i więcej. Aby przyspieszyć proces tworzenia obiektów książek, możesz użyć wzorca Factory. Funkcje wykorzystujące wzorzec Factory używają zdefiniowanego szablonu do zwracania obiektu z właściwościami i metodami.

### Wzorzec Singleton

Jak sama nazwa wskazuje, wzorzec projektowy Singleton jest używany, gdy potrzebujemy dokładnie jednej instancji klasy. Często jest stosowany w celu zarządzania globalnym stanem aplikacji, ale bez używania faktycznego zakresu globalnego. Singletons działają jako współdzielone zasoby z pojedynczym punktem dostępu do funkcji. Możesz się zastanawiać, kiedy potrzebna jest tylko jedna instancja obiektu. Oto kilka rzeczywistych zastosowań:

- Pule wątków (Thread pools)
- Bufory (Caches)
- Opcje logowania
- Ustawienia konfiguracyjne
- Wpływ czasu ładowania przeglądarki na zmienne globalnie dostępne Singleton vs. prawdziwe zmienne globalne
- Połączenia z bazą danych: ponowne użycie istniejących połączeń zamiast tworzenia nowych, co zwiększyłoby obciążenie aplikacji i bazy danych

Ograniczenie do jednej instancji jest ustanawiane poprzez sposób, w jaki klasa jest zaimplementowana. Można napisać metodę, która sprawdza, czy instancja już istnieje, i zwraca nowy obiekt tylko wtedy, gdy jeszcze nie istnieje.


## Kategoria Strukturalna

Wzorce projektowe strukturalne zajmują się relacjami między obiektami. Definiują, jak obiekty i klasy mogą być komponowane, aby dostarczać nowe funkcjonalności lub tworzyć większe struktury. Na przykład obiekt może być używany w definicji innego obiektu, aby udostępniać nowe funkcje, lub klasy mogą dziedziczyć z superklas.

Do wzorców strukturalnych należą:

- **Facade**
- **Proxy**
- **Flyweight**
- **Adapter**
- **Decorator**
- **Composite**
- **Bridge**

### Wzorzec Proxy

Wzorzec Proxy chroni dostęp do obiektu, działając jako zastępca, który przechwytuje i redefiniuje operacje docelowego obiektu. Jest szczególnie przydatny do rzeczy takich jak żądania sieciowe, ponieważ może pomóc w unikaniu zbędnych żądań.

W ES6 wbudowany jest obiekt `Proxy`, który można wykorzystać do implementacji wzorca Proxy. Obiekt ten ma dwa parametry:

- **target**: obiekt, który jest proxowany
- **handler**: definicja dowolnego niestandardowego zachowania obsługiwanego przez obiekt proxy

Jeśli użyjesz konstruktora `Proxy()` z pustym handlerem, będzie on zachowywał się jak obiekt docelowy. Obiekty Proxy mają wbudowane funkcje handlera, które są nazywane pułapkami. Pułapki są używane do wywoływania obiektu docelowego.

Obiekty Proxy są używane razem z obiektem `Reflect`, który ma metody o tych samych nazwach co pułapki obiektów Proxy. Różnica polega na tym, że metody `Reflect` przekazują domyślne operacje do obiektu docelowego.

### Wzorzec Facade

Wzorzec Facade to pojedyncza klasa, która bierze na siebie całą złożoność podsystemu i ukrywa ją. Jest często używany w bibliotekach JavaScript i do upraszczania interakcji z API. Użyj tego wzorca, aby stworzyć łatwiejszy interfejs dla użytkowników końcowych.



## Kategoria Behawioralna

Wzorce projektowe behawioralne upraszczają komunikację między niezwiązanymi obiektami w kodzie, delegując sposób, w jaki obiekty mogą się komunikować. Enkapsulują zachowanie komunikacyjne, aby rozdzielić wiadomości między nadawcami a odbiorcami.

Do wzorców behawioralnych należą:

- **Iterator**
- **Mediator**
- **Observer**
- **Visitor**

### Wzorzec Observer

Na ulubionych platformach społecznościowych inni użytkownicy mogą śledzić Twoją aktywność i być powiadamiani, gdy publikujesz nową treść. W ten sam sposób, dzięki wzorcowi Observer, obiekty mogą mieć zależności, które „subskrybują” zmiany innego obiektu. Powiadomienia mogą płynąć w relacji jeden-do-wielu, czyli jeden zmieniający się obiekt może powiadomić wiele innych obiektów.

### Wzorzec Mediator

Jeśli kiedykolwiek korzystałeś z aplikacji do współdzielenia przejazdów, aby wrócić do domu, możesz pamiętać, że wysyłasz żądanie przez aplikację, a następnie aplikacja „mediatoruje” i przypisuje kierowcę, który Cię odbierze. Nie kontaktujesz się bezpośrednio z kierowcą. W ten sam sposób wzorzec Mediator w kodzie działa jako centralny interfejs, aby enkapsulować, jak różne części kodu mogą się ze sobą komunikować.

Wzorzec ten pomaga zapobiegać zbyt wielu bezpośrednim relacjom między różnymi klasami lub komponentami i pomaga różnym komponentom wiedzieć o zmianach w stanie aplikacji. Dzięki temu kod staje się bardziej ponownie używalny i łatwiejszy do modyfikacji, ponieważ klasy nie są ściśle powiązane.


### Wybór odpowiedniego wzorca projektowego

Wybór odpowiedniego wzorca projektowego może być trudny, biorąc pod uwagę liczne wzorce i antywzorce. Oto kilka kroków, które możesz podjąć, aby wybrać odpowiedni wzorzec:

1. **Interfejsy i interakcje obiektów**:
    
    - Zastanów się nad interfejsem każdego obiektu i jego interakcjami z innymi obiektami. Czy enkapsulujesz odpowiednie informacje w każdym obiekcie, czy powinieneś stworzyć nowy typ obiektu?
    
1. **Specyfikacje obiektów**:
    
    - Rozważ specyfikacje każdego obiektu i sposób obsługi każdej właściwości. Jakie inne obiekty muszą być świadome właściwości tego obiektu? Jak będziesz obsługiwać aktualizacje?
    
1. **Cel wzorców projektowych**:
    
    - Pamiętaj o głównym celu każdej grupy wzorców projektowych. Jeśli projektujesz zachowanie obiektu w przeciwieństwie do sposobu jego tworzenia, przejrzyj opcje wzorców w kategorii Behawioralnej.
    
1. **Przegląd i refaktoryzacja**:
    
    - Po wybraniu projektu, przejrzyj go, aby sprawdzić, czy istnieje powód do wyboru innego wzorca. Czy istnieje coś, co należy zrefaktoryzować lub problem, który wydaje się trudny do rozwiązania?
    
1. **Elastyczność wzorca**:
    
    - Czy możesz wprowadzić zmiany bez przeprojektowywania kodu? Czy możesz to zrobić z obecnym wyborem wzorca projektowego? Czy musisz wprowadzić inny wzorzec? Pamiętaj, że możesz używać wielu różnych wzorców w tej samej bazie kodu.


### Wzorce projektowe w architekturze

Wzorce projektowe mogą być również stosowane do architektury systemowej, przenosząc się z jednostek kodu na procesy i systemy. Omówmy, jak możesz zaimplementować kilka wzorców projektowych, które widziałeś w kodzie, w kontekście projektowania systemu.

#### Użycie wzorca Proxy do implementacji serwera proxy

Proxy serwery są powszechnie używane do optymalizacji ruchu sieciowego i ochrony wrażliwych danych. Wzorzec Proxy idealnie nadaje się do implementacji serwera proxy.

Wzorzec Proxy chroni dostęp do obiektów, przechwytując i redefiniując operacje na obiekcie docelowym. Jest to dokładnie to, czego potrzebujesz do implementacji serwera proxy, który może ukrywać Twoją tożsamość przed zdalnymi serwerami lub modyfikować żądania i odpowiedzi.

Wzorzec Proxy może zwiększyć wydajność żądań; jednym z jego zalet jest możliwość użycia proxy do buforowania wyników i obsługi żądań od wielu użytkowników.

#### Użycie wzorca Facade do implementacji mikroserwisów

Mikroserwisy to styl architektury, który strukturyzuje aplikację jako zbiór usług. Teoretycznie mikroserwisy ułatwiają jednostkom biznesowym pisanie własnych API, które mogą współpracować z innymi częściami bazy kodu.

Możesz użyć wzorca Facade do implementacji interoperacyjności między tymi izolowanymi usługami. Fasada działa jako interfejs, dzięki czemu poszczególne części nie stają się zależne ani ściśle powiązane, a klienci nie muszą znać wewnętrznej implementacji kodu innych usług.

### References:

https://www.codecademy.com/courses/learn-javascript-best-practices/articles/javascript-design-patterns
---



