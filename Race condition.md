
--- 
tags: [[React]]
date: 2024-07-26

---
**Race condition** to sytuacja, która występuje w programowaniu wielowątkowym, gdy dwa lub więcej wątków lub procesów próbuje jednocześnie uzyskać dostęp do wspólnego zasobu (np. zmiennej lub pliku) i co najmniej jeden z tych wątków próbuje zmienić ten zasób. Jeśli dostęp do zasobu nie jest odpowiednio zsynchronizowany, może to prowadzić do nieprzewidywalnych wyników lub błędów w programie.


W kontekście React, **race condition** może wystąpić, gdy różne asynchroniczne operacje (np. fetch API, zapytania do serwera) konkurują o zmianę stanu komponentu. W React problem pojawia się, gdy jedna operacja zostaje zakończona i próbuje zaktualizować stan, podczas gdy inna operacja, która była zainicjowana później, ale zakończyła się szybciej, również próbuje zmodyfikować ten sam stan. W efekcie, wynik działania komponentu może być nieprzewidywalny i prowadzić do błędów lub wyświetlania nieaktualnych danych.

### **Rozwiązania:**

1. **Zarządzanie anulowaniem (cleanup) w `useEffect`**: Jak pokazano w powyższym przykładzie, można ustawić flagę `isCancelled`, aby upewnić się, że nieaktualne zapytania nie będą próbowały zaktualizować stanu komponentu.

2. **AbortController**: Możesz użyć `AbortController`, aby anulować nieaktualne zapytania HTTP, które nie są już potrzebne.

3. **Asynchroniczne operacje z flagą aktualności**: Można ręcznie śledzić, czy odpowiedź, która przychodzi, jest odpowiednia dla aktualnego zapytania. Taka flaga jest efektywniejsza, gdy mamy do czynienia z wieloma asynchronicznymi operacjami, które potencjalnie mogą wpłynąć na stan komponentu.

4. **Użycie bibliotek zarządzających asynchronicznością**: Biblioteki takie jak `React Query`, `SWR` lub inne narzędzia do zarządzania zapytaniami i pamięcią podręczną (cache) mogą pomóc w uniknięciu problemów związanych z race condition.



### References:
https://en.wikipedia.org/wiki/Race_condition#In_software

---



