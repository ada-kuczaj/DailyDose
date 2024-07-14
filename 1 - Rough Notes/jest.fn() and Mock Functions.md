
--- 
tags: [[Mock]] [[Jest]] [[Testing]]
date: 2024-07-12

---
`jest.fn()` to narzędzie dostarczone przez Jest, popularne środowisko testowe, które umożliwia tworzenie funkcji mockujących. Funkcja mockująca to funkcja, która pozwala testować, jak inne funkcje są wywoływane i co zwracają, bez korzystania z rzeczywistej implementacji. Jest to szczególnie przydatne do izolowania testowanej funkcji i weryfikowania interakcji z innymi funkcjami.

```js
const mockCallback = jest.fn(notify);
```

Ta linia tworzy funkcję mockującą o nazwie `mockCallback`, która naśladuje zachowanie funkcji `notify`. Oto jak to działa:

1. **Mockowanie Implementacji**: Przekazując `notify` do `jest.fn()`, funkcja mockująca będzie używać implementacji `notify`. Oznacza to, że gdy `mockCallback` zostanie wywołany, będzie zachowywać się tak samo jak `notify`.
    
2. **Śledzenie Wywołań**: Funkcja mockująca rejestruje, ile razy została wywołana, z jakimi argumentami i co zwróciła. Te informacje są niezbędne do pisania testów, które weryfikują interakcje między funkcjami.
    
3. **Izolacja Testów**: Używanie funkcji mockujących pomaga izolować testowaną funkcję od jej zależności. Ułatwia to znalezienie przyczyn błędów i zapewnia, że testy nie są wpływane przez zmiany w zależnościach.

#### Dlaczego Używamy Funkcji Mockujących?

Bez funkcji mockujących nie można by było zweryfikować, ile razy callback został wywołany i z jakimi argumentami. Nie można by też kontrolować zwracanych wartości w uporządkowany sposób. Utrudniałoby to testowanie interakcji i zapewnienie, że funkcje działają zgodnie z oczekiwaniami w różnych scenariuszach.

### Dlaczego Testy Zawodzą Bez Mocków

Oto dlaczego testy zawodzą bez użycia `jest.fn()`:

1. **Brak Możliwości Śledzenia Wywołań**: Bez mocka nie można śledzić, ile razy `notify` został wywołany ani z jakimi argumentami. Jest dostarcza specjalne matchery, takie jak `.toHaveBeenCalledTimes()` i `.toHaveBeenCalledWith()`, które działają tylko z funkcjami mockującymi.
    
2. **Brak Informacji o Wywołaniach**: Bez mockowania nie można zbierać informacji o wywołaniach funkcji, co uniemożliwia poprawne weryfikowanie interakcji i skutków ubocznych.

### Kluczowe Punkty

- **Funkcje Mockujące**: Pozwalają na śledzenie wywołań, argumentów i zwracanych wartości.
- **Izolacja**: Pomagają izolować testowaną funkcję od jej zależności.
- **Weryfikacja**: Umożliwiają weryfikację interakcji między funkcjami, nie tylko ich wyników.

Korzystając z funkcji mockujących, zyskujesz potężne narzędzia do tworzenia wszechstronnych i niezawodnych testów, zapewniając, że Twój kod działa poprawnie w różnych scenariuszach i interakcjach.

---
### Przykład Bez Funkcji Mockujących

Bez `jest.fn()` test mógłby wyglądać tak:

```js
test('nazwa testu', () => {
    const order = 'SUCCESS';

    // Wywołanie onSuccess bez mocka
    const result = onSuccess(notify);

    // Nadal można sprawdzić wynik
    expect(result).toEqual({ message: 'SUCCESS' });

    // Ale nie można sprawdzić, ile razy notify został wywołany
    // ani z jakimi argumentami
});
```

Ten test tylko weryfikuje zwracaną wartość, ale nie sprawdza interakcji (czyli wywołań i argumentów) z funkcją `notify`. Dlatego mocki są niezbędne do kompleksowego testowania.
### Kompletny Test z Funkcjami Mockującymi

```js
const { onSuccess, notify } = require('./fruitPicker');

test('nazwa testu', () => {
    const order = 'SUCCESS';
    const mockCallback = jest.fn(notify);  // Tworzenie funkcji mockującej

    // Wywołanie onSuccess z mockiem callbacka
    onSuccess(mockCallback);

    // Sprawdzenie, czy callback został wywołany raz
    expect(mockCallback).toHaveBeenCalledTimes(1);  // Weryfikacja liczby wywołań

    // Sprawdzenie, czy callback został wywołany z poprawnym argumentem
    expect(mockCallback).toHaveBeenCalledWith(order);  // Weryfikacja argumentów

    // Sprawdzenie wyniku zwracanego przez callback
    expect(mockCallback(order)).toEqual({ message: 'SUCCESS' });  // Weryfikacja zwracanej wartości
});
```


### References:



---



