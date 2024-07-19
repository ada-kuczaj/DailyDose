
--- 
tags: [[Testing]]
date: 2024-07-02

---
## Rodzaje Testów w Oprogramowaniu

1. **Testy jednostkowe (Unit Tests)**

    - Testują pojedyncze metody i funkcje klas, komponentów lub modułów. Są tanie w automatyzacji i szybkie w wykonaniu.
      
2. **Testy integracyjne (Integration Tests)**
    
    - Sprawdzają, czy różne moduły lub usługi działają poprawnie razem, np. interakcje z bazą danych. Wymagają wielu działających części aplikacji, co czyni je droższymi.
      
3. **Testy funkcjonalne (Functional Tests)**
    
    - Skupiają się na wymaganiach biznesowych aplikacji, weryfikując tylko wynik działania bez sprawdzania stanów pośrednich.
      
4. **Testy end-to-end (End-to-End Tests)**
    
    - Replikują zachowanie użytkownika w pełnym środowisku aplikacji, weryfikując całe procesy użytkownika, np. logowanie.
      
5. **Testy akceptacyjne (Acceptance Tests)**
    
    - Formalne testy weryfikujące, czy system spełnia wymagania biznesowe i mierzące wydajność systemu.
      
6. **Testy wydajnościowe (Performance Tests)**
    
    - Ocena wydajności systemu pod określonym obciążeniem, mierzenie szybkości, skalowalności i niezawodności.
      
7. **Testy dymne (Smoke Tests)**
    
    - Podstawowe testy sprawdzające podstawową funkcjonalność aplikacji, szybkie do wykonania, używane po nowych kompilacjach lub wdrożeniach.



![[types of tests pyramid.png]]

## Testowanie ręczne a automatyczne

Ważne jest, aby rozróżnić testy ręczne i automatyczne. Testowanie ręczne odbywa się osobiście, poprzez kliknięcie aplikacji lub interakcję z oprogramowaniem i interfejsami API za pomocą odpowiednich narzędzi. Jest to bardzo kosztowne, ponieważ wymaga od kogoś skonfigurowania środowiska i samodzielnego wykonania testów, a także może powodować błędy ludzkie, ponieważ tester może popełnić literówki lub pominąć kroki w skrypcie testowym.

Z kolei testy automatyczne wykonywane są przez maszynę, która wykonuje wcześniej napisany skrypt testowy. Testy te mogą mieć różny stopień złożoności – od sprawdzenia pojedynczej metody w klasie po sprawdzenie, czy wykonanie sekwencji złożonych działań w interfejsie użytkownika prowadzi do tych samych wyników. Są znacznie solidniejsze i bardziej niezawodne niż testy ręczne, ale jakość testów automatycznych zależy od tego, jak dobrze zostały napisane skrypty testowe.

### References:
https://www.freecodecamp.org/news/how-to-start-unit-testing-javascript/
https://www.atlassian.com/continuous-delivery/software-testing/types-of-software-testing 
---



