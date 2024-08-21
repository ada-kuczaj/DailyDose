--- 
tags: [[React]]
date: 2024-08-21

---

#### 1. **Folder główny projektu**

- **`src/`**: Główny folder źródłowy, w którym znajduje się cała logika aplikacji.
- **`public/`**: Folder zawierający statyczne zasoby, takie jak pliki HTML, obrazy, ikony, itp. Zawiera główny plik `index.html`, który jest punktem wejściowym aplikacji.
- **`node_modules/`**: Folder automatycznie tworzony przez npm/yarn, zawierający wszystkie zainstalowane zależności.

#### 2. **Struktura folderów w `src/`**

- **`components/`**: Zawiera wszystkie komponenty, które są wielokrotnie używane w różnych częściach aplikacji.
    - **`common/`**: Zbiór komponentów ogólnego użytku (np. przyciski, formularze, nagłówki).
    - **`specific/`**: Komponenty specyficzne dla poszczególnych modułów lub funkcji.
- **`containers/`**: Kontenerowe komponenty, które łączą logikę biznesową z prezentacyjną. Często zarządzają stanem aplikacji lub integrują różne komponenty.
- **`hooks/`**: Własne hooki React, które mogą być ponownie używane w różnych komponentach.
- **`context/`**: Zawiera pliki związane z Context API, które umożliwiają globalne zarządzanie stanem aplikacji.
- **`services/`**: Logika biznesowa aplikacji, jak np. API do komunikacji z backendem, funkcje pomocnicze, itp.
- **`redux/` lub **`state/`: Jeżeli aplikacja korzysta z Redux lub innego narzędzia do zarządzania stanem globalnym, tutaj znajdują się odpowiednie pliki (akcje, reduktory, middleware).
- **`styles/`**: Pliki CSS, SASS, lub Styled Components, które zawierają style aplikacji.
- **`assets/`**: Pliki takie jak obrazy, czcionki, itp., które są wykorzystywane w aplikacji.
- **`utils/`**: Narzędzia i funkcje pomocnicze, które mogą być używane w różnych miejscach aplikacji.
- **`pages/`**: Zawiera komponenty reprezentujące całe strony lub widoki aplikacji. Każdy widok może mieć swój własny folder, zawierający specyficzne dla niego komponenty, style, itp.

#### 3. **Przykładowa struktura**

![[Pasted image 20240821204601.png]]

#### 4. **Dobre praktyki**

- **Modularność**: Grupuj pliki i komponenty według funkcjonalności, co ułatwia ich odnajdywanie i zarządzanie.
- **Reużywalność**: Komponenty i hooki umieszczaj w odpowiednich folderach, aby można było je łatwo odnaleźć i ponownie użyć w różnych częściach aplikacji.
- **Czytelność**: Utrzymuj strukturę prostą i zrozumiałą dla zespołu, nawet jeśli oznacza to więcej folderów. Unikaj nadmiernego zagnieżdżania.
- **Skalowalność**: Struktura powinna być łatwa do rozszerzenia w miarę rozwoju aplikacji.


### References:


---



