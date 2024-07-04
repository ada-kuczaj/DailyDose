
--- 
tags: [[Internet]]
date: 2024-07-04

---
Opiera się głównie na modelu klient-serwer, gdzie przeglądarka internetowa użytkownika działa jako klient, a serwer dostarcza zasoby (strony, dane, multimedia itp.). Proces ten obejmuje kilka kluczowych technologii i protokołów:

1. HTTP/HTTPS
	- HTTP (Hypertext Transfer Protocol) i jego bezpieczna wersja HTTPS (HTTP Secure) to protokoły komunikacyjne używane do przesyłania danych między klientem a serwerem. Klient wysyła żądanie HTTP do serwera, a serwer odpowiada przesyłając odpowiedź HTTP zawierającą żądane dane lub zasoby.
	- HTTPS dodaje warstwę szyfrowania SSL/TLS, zwiększając bezpieczeństwo przesyłanych danych.

2. DNS (Domain Name System)
	- DNS tłumaczy nazwy domen na adresy IP, umożliwiając przeglądarkom nawiązanie połączenia z serwerami, na których hostowane są strony internetowe. Kiedy użytkownik wpisuje adres URL w przeglądarce, DNS odpowiada za znalezienie odpowiedniego adresu IP serwera.

3. TCP/IP
	- TCP (Transmission Control Protocol) i IP (Internet Protocol) to podstawowe protokoły internetowe umożliwiające komunikację w sieci. IP odpowiada za adresowanie i routowanie pakietów danych, natomiast TCP zapewnia niezawodne dostarczenie tych danych, kontrolując kolejność pakietów i sprawdzając błędy.

4. WebSockets
	- WebSockets to zaawansowany protokół, który umożliwia dwukierunkową, trwałą komunikację między przeglądarką a serwerem w czasie rzeczywistym. Jest używany w aplikacjach wymagających ciągłej wymiany danych, np. w grach online, czatach.

5. AJAX (Asynchronous JavaScript and XML)
	- AJAX to technika umożliwiająca stronom internetowym asynchroniczne wysyłanie żądań do serwera i aktualizowanie części strony bez konieczności przeładowywania całej strony. Umożliwia to dynamiczną interakcję użytkownika ze stroną.

6. API (Application Programming Interface)
	- Serwery często udostępniają API, które umożliwiają programistom pobieranie danych lub interakcję z serwisem za pomocą zdefiniowanych żądań HTTP. API mogą być publiczne (dostępne dla wszystkich) lub prywatne (dla określonych użytkowników).

7. REST i GraphQL
	- REST (Representational State Transfer) i GraphQL to popularne podejścia do budowania API, które określają, jak zasoby są udostępniane i zarządzane przez HTTP. REST opiera się na konwencji URL-i i metod HTTP, natomiast GraphQL pozwala klientom dokładnie określić, jakie dane chcą otrzymać.

### References:


---



