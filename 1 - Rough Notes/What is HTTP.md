
--- 
tags: [[Internet]]
date: 2024-07-15

---
# Hypertext Transfer Protocol (HTTP)

Służy do ładowania stron internetowych za pomocą łączy hipertekstowych. HTTP to protokół warstwy aplikacji przeznaczony do przesyłania informacji między urządzeniami sieciowymi i działający na innych warstwach stosu protokołów sieciowych. Typowy przepływ przez protokół HTTP polega na tym, że komputer kliencki wysyła żądanie do serwera, który następnie wysyła komunikat odpowiedzi.

Każde żądanie HTTP wysłane przez Internet niesie ze sobą serię zakodowanych danych, które zawierają różne typy informacji. 

![[Pasted image 20240715155511.png]]

![[Pasted image 20240715155559.png]]
## Typowe żądanie HTTP zawiera:

1. Typ wersji HTTP
2. adres URL
3. metoda HTTP
4. Nagłówki żądań HTTP
5. Opcjonalna treść HTTP

## Co to jest metoda HTTP?
Metoda HTTP, czasami nazywana czasownikiem HTTP, wskazuje akcję, jakiej oczekuje żądanie HTTP od serwera, do którego kierowane jest zapytanie. Na przykład dwie najpopularniejsze metody HTTP to „GET” i „POST”; żądanie „GET” oczekuje w zamian informacji (zwykle w postaci strony internetowej), podczas gdy żądanie „POST” zazwyczaj wskazuje, że klient przesyła informacje do serwera WWW (takie jak informacje z formularza, np. przesłana nazwa użytkownika i hasło ).
## Co to są nagłówki żądań HTTP?
Nagłówki HTTP zawierają informacje tekstowe przechowywane w parach klucz-wartość i są dołączane do każdego żądania HTTP (i odpowiedzi). Nagłówki te przekazują podstawowe informacje, takie jak przeglądarka, z której korzysta klient i jakie dane są wymagane.

Przykład nagłówków żądań HTTP z karty sieciowej przeglądarki Google Chrome:

![[Pasted image 20240715131304.png]]

## Co znajduje się w treści żądania HTTP?
Treść żądania to część zawierająca „treść” informacji, które przekazuje żądanie. Treść żądania HTTP zawiera wszelkie informacje przesyłane do serwera WWW, takie jak nazwa użytkownika i hasło, lub inne dane wprowadzone do formularza.

---

## Co zawiera odpowiedź HTTP?
Odpowiedź HTTP to odpowiedź, którą klienci WWW (często przeglądarki) otrzymują z serwera internetowego w odpowiedzi na żądanie HTTP. Odpowiedzi te przekazują cenne informacje na podstawie tego, o co poproszono w żądaniu HTTP.

### Typowa odpowiedź HTTP zawiera:

1. kod stanu HTTP
2. Nagłówki odpowiedzi HTTP
3. opcjonalna treść HTTP

#### Kod stanu HTTP
Kody stanu HTTP to 3-cyfrowe kody najczęściej używane do wskazania, czy żądanie HTTP zostało pomyślnie zakończone. Kody stanu są podzielone na następujące 5 bloków:

- 1xx Informacje
- 2xx Sukces
- 3xx Przekierowanie 
- 4xx Błąd klienta
- 5xx Błąd serwera

„xx” odnosi się do różnych liczb od 00 do 99.

#### Co to są nagłówki odpowiedzi HTTP?
Podobnie jak żądanie HTTP, odpowiedź HTTP zawiera nagłówki zawierające ważne informacje, takie jak język i format danych wysyłanych w treści odpowiedzi.

Przykład nagłówków odpowiedzi HTTP z karty sieciowej przeglądarki Google Chrome:

![[Pasted image 20240715131744.png]]

#### Co znajduje się w treści odpowiedzi HTTP?
Pomyślne odpowiedzi HTTP na żądania „GET” zazwyczaj mają treść zawierającą żądane informacje. W większości żądań internetowych są to dane HTML, które przeglądarka internetowa przetłumaczy na stronę internetową.


### References:
https://www.youtube.com/watch?v=iYM2zFP3Zn0
https://www.cloudflare.com/en-gb/learning/ddos/glossary/hypertext-transfer-protocol-http/
https://cs.fyi/guide/http-in-depth
https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview

---



