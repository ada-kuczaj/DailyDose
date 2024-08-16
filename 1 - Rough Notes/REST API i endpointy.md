
--- 
tags: 
date: 2024-08-16

---
### <span style="color: #00aedb;">Co to jest REST API?</span>

**REST API (Representational State Transfer Application Programming Interface)** - to styl architektoniczny dla tworzenia usług webowych, który umożliwia komunikację klient-serwer i mikrousług.

Koncepcje REST API zostały opracowane dla sieci WWW i stanowiły podstawę jej rozwoju w chmurze, Edge, internecie mobilnym i internecie rzeczy (IoT).

### <span style="color: #f37735">Do czego służy REST API?</span>

REST API jest używane do:
- **Tworzenia, odczytywania, aktualizowania i usuwania danych** (operacje CRUD) w aplikacjach webowych.
- **Komunikacji między różnymi systemami i aplikacjami** w sposób niezależny od języka programowania.
- **Integracji różnych usług** – REST API może być używane do połączenia aplikacji z bazą danych, systemami zewnętrznymi, jak np. płatności online, mapy, serwisy pogodowe, itp.

![[Pasted image 20240816145319.png]]

Korzystanie z REST API polega na wysyłaniu żądań HTTP do serwera. Najczęściej używane metody to:

- `GET` – pobieranie danych (np. lista użytkowników, szczegóły produktu).
- **`POST`** – tworzenie nowych zasobów (np. dodanie nowego użytkownika).
- `PUT` – aktualizowanie istniejących zasobów (np. edycja informacji o produkcie).
- `DELETE` – usuwanie zasobów (np. usunięcie użytkownika).
- `PATCH` - częściowa aktualizacja zasobu.

Każde żądanie zawiera adres URL, który wskazuje na zasób, oraz opcjonalne dane, takie jak parametry lub ciało żądania.

### <span style="color: #ffc425;">Działanie API REST</span>

Interfejsy API REST mogą obsługiwać praktycznie każde żądanie dostępu, format danych, kontrolę zasobów lub komunikaty o stanie, ale reguła bezstanowości oznacza, że każde żądanie musi zawierać uwierzytelnienie niezbędne do jego zweryfikowania, dokładną definicję wymaganego zasobu i dokładne działanie, które jest wymagane.

API REST przekazuje wszystkie te informacje za pośrednictwem kombinacji nagłówków i pól parametrów i może wymieniać rzeczywiste dane w dowolnym formacie. Bardzo popularnym standardem jest JSON, czyli format Javascript Object Notation, który mimo swojej nazwy jest czytelny zarówno dla ludzi, jak i dla maszyn, przez ludzkie oko lub przy użyciu któregokolwiek z popularnych języków programowania.

### <span style="color: #00b159;">Request</span>

1. **Metoda HTTP**: Określa, co chcemy zrobić z zasobem. Najczęściej używane metody to:
   - `GET` ,`POST`,`PUT`, `DELETE`, `PATCH`

2. **URL (Uniform Resource Locator)**: Adres, pod którym dostępny jest zasób. Składa się z:
   - Protokół (np. `https://`)
   - Host (np. `api.example.com`)
   - Ścieżka (np. `/users/{id}`)
   - Opcjonalnie parametry zapytania (Query Parameters), np. `?sort=asc&limit=10`

3. **Nagłówki (Headers)**: Dodatkowe informacje przesyłane w żądaniu. Przykłady:
   - `Content-Type`: Określa format danych wysyłanych lub oczekiwanych w odpowiedzi (np. `application/json`).
   - `Authorization`: Token autoryzacyjny, jeśli API wymaga uwierzytelnienia.
   - `Accept`: Format danych, który klient jest w stanie przetworzyć (np. `application/json`).

4. **Body**: Zawartość przesyłana w żądaniu, najczęściej w formacie JSON 
   (w przypadku metod `POST`, `PUT`, `PATCH`). Przykład:

```json
{
  "name": "John Doe",
  "email": "john.doe@example.com"
}
```

### <span style="color: #d11141;">Response</span>

1. **Status HTTP**: Kod statusu HTTP, który informuje o rezultacie przetwarzania żądania. Przykłady: 
   - `200 OK`: Sukces.
   - `201 Created`: Zasób został utworzony.
   - `400 Bad Request`: Błąd w żądaniu (np. niepoprawne dane).
   - `401 Unauthorized`: Brak autoryzacji.
   - `404 Not Found`: Zasób nie został znaleziony.
   - `500 Internal Server Error`: Błąd po stronie serwera.

2. **Nagłówki (Headers)**: Dodatkowe informacje zwrócone przez serwer. Przykłady:
- `Content-Type`: Format danych w odpowiedzi (np. `application/json`).
- `Location`: Wskazuje URL do nowo utworzonego zasobu (gdy użyto `POST`).

3. **Body**: Dane zwracane przez serwer, najczęściej w formacie JSON. Przykład:

```json
{
  "id": 123,
  "name": "John Doe",
  "email": "john.doe@example.com",
  "createdAt": "2024-08-16T12:00:00Z"
}
```


### References:
https://www.youtube.com/watch?v=lsMQRaeKNDk

---



