
--- 
tags: [[Javascript Methods]]
date: 2024-07-18

---
Zastosowanie `Map` zamiast `Switch Case` w niektórych przypadkach pozwala na bardziej schludny, zwięzły, elegancki zapis.

### Przykład użycia `switch case`

```js
function getDayMessage(day) {
  let message;
  switch (day) {
    case 'Monday':
      message = 'Start of the work week';
      break;
    case 'Tuesday':
      message = 'Second day of the work week';
      break;
    case 'Wednesday':
      message = 'Midweek';
      break;
    case 'Thursday':
      message = 'Almost the weekend';
      break;
    case 'Friday':
      message = 'Last work day';
      break;
    case 'Saturday':
      message = 'Weekend!';
      break;
    case 'Sunday':
      message = 'Rest day';
      break;
    default:
      message = 'Invalid day';
  }
  return message;
}

console.log(getDayMessage('Monday')); // Output: Start of the work week
```

### Przykład użycia `Map`

```js
const dayMessages = new Map([
  ['Monday', 'Start of the work week'],
  ['Tuesday', 'Second day of the work week'],
  ['Wednesday', 'Midweek'],
  ['Thursday', 'Almost the weekend'],
  ['Friday', 'Last work day'],
  ['Saturday', 'Weekend!'],
  ['Sunday', 'Rest day']
]);

function getDayMessage(day) {
  return dayMessages.get(day) || 'Invalid day';
}

console.log(getDayMessage('Monday')); // Output: Start of the work week
```

### Wyjaśnienie

1. **Tworzenie `Map`**: Tworzymy mapę `dayMessages`, która mapuje dni tygodnia na odpowiednie wiadomości. Wykorzystujemy do tego metodę `new Map()`, przekazując tablicę par klucz-wartość.

2. **Pobieranie wartości z `Map`**: W funkcji `getDayMessage` używamy metody `get()` mapy `dayMessages`, aby uzyskać wiadomość dla danego dnia. Jeśli klucz nie istnieje w mapie, zwracamy domyślną wartość `'Invalid day'` za pomocą operatora `||`.
    

### Zalet użycia `Map`

- **Czytelność**: Kod z użyciem `Map` jest często bardziej zwięzły i czytelny.
- **Wydajność**: Wyszukiwanie w `Map` ma złożoność czasową O(1), co może być bardziej efektywne w porównaniu do `switch case` dla dużej liczby przypadków.
- **Elastyczność**: `Map` pozwala na używanie dowolnych typów jako kluczy, nie tylko ciągów znaków lub liczb.


### References:


---



