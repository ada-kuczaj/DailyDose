
--- 
tags: [[Internet]]
date: 2024-07-19

---
## **DNS (Domain Name System)**

DNS tłumaczy nazwy domen na adresy IP, umożliwiając przeglądarkom nawiązanie połączenia z serwerami, na których hostowane są strony internetowe. Kiedy użytkownik wpisuje adres URL w przeglądarce, DNS odpowiada za znalezienie odpowiedniego adresu IP serwera.

System nazw domen (DNS) to książka telefoniczna Internetu.

## Różnica między autorytatywnym serwerem DNS a rekurencyjnym resolverem DNS

Oba pojęcia odnoszą się do serwerów, które są integralne dla infrastruktury DNS, ale każdy z nich pełni inną rolę i znajduje się w innym miejscu w procesie zapytania DNS. Rekurencyjny resolver DNS jest na początku zapytania, a autorytatywny serwer DNS jest na końcu.

- **Rekurencyjny resolver DNS:** Rekurencyjny resolver to komputer, który odpowiada na rekurencyjne zapytanie od klienta i śledzi rekord DNS. Wysyła serię zapytań, aż dotrze do autorytatywnego serwera DNS dla żądanego rekordu. Dzięki procesowi buforowania (caching), rekurencyjne resolvery nie zawsze muszą wysyłać wiele zapytań, ponieważ mogą wcześniej zwrócić zapisany rekord.

- **Autorytatywny serwer DNS:** Autorytatywny serwer DNS to serwer, który faktycznie przechowuje i odpowiada za rekordy zasobów DNS. Jest to serwer na końcu łańcucha zapytań DNS, który odpowiada na zapytanie docelowym rekordem, umożliwiając przeglądarce dotarcie do potrzebnego adresu IP. Autorytatywny serwer DNS może odpowiadać na zapytania z własnych danych, bez konieczności odpytywania innego źródła.

**Kroki w procesie zapytania DNS:**

1. Klient wysyła zapytanie do rekurencyjnego resolvera DNS.
2. Rekurencyjny resolver, jeśli nie ma odpowiedzi w swojej pamięci podręcznej, wysyła zapytania do różnych serwerów DNS (root, TLD, itp.).
3. Proces kontynuuje, aż zapytanie dotrze do autorytatywnego serwera DNS.
4. Autorytatywny serwer DNS zwraca żądany rekord do rekurencyjnego resolvera.
5. Rekurencyjny resolver zwraca odpowiedź do klienta.

![[Pasted image 20240719144702.png]]
## Omówienie schematu

Proces pozyskania adresu IP w ramach zapytania DNS (Domain Name System) przedstawia się następująco:

Proces pozyskiwania adresu IP zaczyna się od wpisania przez użytkownika adresu URL (np. google.com) w przeglądarce. Przeglądarka najpierw sprawdza swoją pamięć podręczną (cache) w poszukiwaniu adresu IP. Jeśli go nie znajdzie, sprawdza lokalną pamięć podręczną DNS na komputerze użytkownika oraz plik hosts. Gdy te kroki nie przyniosą rezultatu, przeglądarka wysyła zapytanie do serwera DNS rekurencyjnego.

Serwer DNS rekurencyjny sprawdza swoją pamięć podręczną. Jeśli adres IP nie jest tam dostępny, serwer wysyła zapytanie do serwera głównego DNS (Root DNS), który zwraca informacje o serwerach TLD (Top-Level Domain). Następnie serwer DNS rekurencyjny wysyła zapytanie do odpowiedniego serwera TLD, który zwraca informacje o serwerach nazw (NS) odpowiedzialnych za daną domenę.

Serwer DNS rekurencyjny wysyła zapytanie do autorytatywnego serwera nazw, który zwraca adres IP dla danej domeny. Ostatecznie, serwer DNS rekurencyjny zwraca uzyskany adres IP do przeglądarki użytkownika, która łączy się z adresem IP i wyświetla żądaną stronę internetową.

## Rodzaje zapytań DNS

W typowym zapytaniu DNS występują trzy rodzaje zapytań. Korzystając z kombinacji tych zapytań, zoptymalizowany proces rozwiązywania DNS może skutkować skróceniem przebywanej odległości. W idealnej sytuacji dostępne będą dane z pamięci podręcznej, co pozwoli serwerowi nazw DNS na zwrócenie zapytania nierekurencyjnego.

### 3 rodzaje zapytań DNS:

1. **Zapytanie rekurencyjne**:

    - W zapytaniu rekurencyjnym klient DNS wymaga, aby serwer DNS (zazwyczaj rekurencyjny resolver DNS) odpowiedział klientowi albo żądanym rekordem zasobów, albo komunikatem o błędzie, jeśli resolver nie może znaleźć rekordu.

2. **Zapytanie iteracyjne**:

    - W tej sytuacji klient DNS pozwala serwerowi DNS zwrócić najlepszą odpowiedź, jaką może. Jeśli zapytany serwer DNS nie ma odpowiedniego rekordu, zwróci odwołanie do serwera DNS autorytatywnego dla niższego poziomu przestrzeni nazw domeny. Klient DNS następnie wysyła zapytanie do adresu z odwołania. Proces ten kontynuuje się z dodatkowymi serwerami DNS w łańcuchu zapytań, aż wystąpi błąd lub przekroczenie czasu.

3. **Zapytanie nierekurencyjne**:

    - Zazwyczaj ma miejsce, gdy klient resolvera DNS wysyła zapytanie do serwera DNS o rekord, do którego ten ma dostęp, ponieważ jest autorytatywny dla tego rekordu lub rekord znajduje się w jego pamięci podręcznej. Zwykle serwer DNS buforuje rekordy DNS, aby zapobiec dodatkowej konsumpcji pasma i obciążeniu serwerów wyższego poziomu.

**Podsumowanie:** Zapytania rekurencyjne wymagają pełnej odpowiedzi lub błędu, iteracyjne kierują klienta do kolejnych serwerów, a nierekurencyjne korzystają z dostępnych danych z pamięci podręcznej lub danych autorytatywnych.


## Buforowanie DNS: Co to jest i gdzie występuje?

Buforowanie DNS polega na tymczasowym przechowywaniu danych DNS bliżej klienta, co przyspiesza czas odpowiedzi na zapytania DNS i zmniejsza obciążenie sieci. Rekordy DNS są przechowywane przez określony czas, zależny od parametru TTL (time-to-live).

**Główne lokalizacje buforowania DNS:**

1. **Przeglądarka internetowa**:

    - Przeglądarki buforują rekordy DNS, aby przyspieszyć czas odpowiedzi. Przykład: status bufora DNS w Chrome można sprawdzić pod adresem chrome://net-internals/#dns.

2. **System operacyjny (OS)**:
   
    - System operacyjny buforuje rekordy DNS za pomocą tzw. „stub resolvera”. Gdy rekord nie jest dostępny lokalnie, zapytanie wysyłane jest do rekurencyjnego resolvera DNS dostawcy usług internetowych (ISP).

3. **Dostawca usług internetowych (ISP)**:
   
    - Rekurencyjny resolver w ISP sprawdza swoją pamięć podręczną przed wysłaniem zapytania dalej. Dzięki temu zmniejsza się liczba zapytań do serwerów wyższego poziomu.

Buforowanie na każdym z tych poziomów poprawia wydajność i niezawodność zapytań DNS.

### References:

https://www.youtube.com/watch?v=Wj0od2ag5sk
https://www.cloudflare.com/en-gb/learning/dns/what-is-dns/
---



