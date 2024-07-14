
--- 
tags: [[Jest]] [[NodeJS]] [[Testing]] 
date: 2024-07-03

---
W JavaScript istnieją dwie główne konwencje dotyczące zarządzania modułami: **CommonJS i ES Modules.** Wybór jednej z nich zależy od kilku czynników, takich jak środowisko, w którym pracujesz, oraz narzędzia i biblioteki, których używasz. 

### CommonJS ✅

CommonJS jest szeroko stosowany w środowiskach Node.js i jest rozpoznawalny dzięki używaniu `require` i `module.exports`.
#### Przykład:

**hello.js**
```js
function hello() {
  return 'Hello, World!';
}

module.exports = hello;
```
**hello.test.js**
```js
const hello = require('./hello');

test('Say Hi!', () => {
  expect(hello()).toBe('Hello, World!');
});
```

W CommonJS, aby wyeksportować funkcję lub obiekt z modułu, można użyć obiektu `exports` lub `module.exports`.

Alternatywny zapis:
**functions.js**
```js
exports.generateText = (name, age) => {
  // Zwraca tekst wyjściowy
  return `${name} (${age} years old)`;
};

exports.createElement = (type, text, className) => {
  // Tworzy nowy element HTML i zwraca go
  const newElement = document.createElement(type);
  newElement.classList.add(className);
  newElement.textContent = text;
  return newElement;
};
```
**functions.test.js**
```js
const { generateText, createElement } = require('./functions'); // Zmien 'functions' na właściwą nazwę pliku

test('generateText returns proper output', () => {
  const text = generateText('John', 30);
  expect(text).toBe('John (30 years old)');
});

test('createElement creates an element with correct properties', () => {
  document.body.innerHTML = ''; // Wyczyszczenie dokumentu
  const element = createElement('div', 'Hello, World!', 'greeting');
  expect(element.tagName).toBe('DIV');
  expect(element.textContent).toBe('Hello, World!');
  expect(element.classList.contains('greeting')).toBe(true);
});

```

>[!warning]
>Zapis `exports.const EXPECTED_MINUTES_IN_OVEN = 40;` jest niepoprawny w konwencji CommonJS. W CommonJS **nie można bezpośrednio eksportować zmiennych** za pomocą `const` i `exports` w tej formie. Zamiast tego należy użyć `module.exports` lub `exports` w poprawny sposób.

```js
const API_KEY = '12345-abcde';
const MAX_USERS = 100;

module.exports = {
  API_KEY,
  MAX_USERS
};
```

### ES Modules (ESM) 

ES Modules są standardem w nowoczesnym JavaScript i są szeroko wspierane w przeglądarkach oraz w nowszych wersjach Node.js. Używają składni `import` i `export`.
#### Przykład:

**remainingMinutesInOven.js**
```js
export function remainingMinutesInOven(actualMinutesInOven) {
  const EXPECTED_MINUTES_IN_OVEN = 40;
  return EXPECTED_MINUTES_IN_OVEN - actualMinutesInOven;
}
```

**remainingMinutesInOven.test.js**
```js
import { remainingMinutesInOven } from './remainingMinutesInOven';

test('Calculate remaining minutes in oven', () => {
  expect(remainingMinutesInOven(20)).toBe(20);
});
```

### Którą konwencję wybrać?

1. ✅ **CommonJS**: 
    
    - **Zalety**: Szerokie wsparcie w Node.js, kompatybilność z wieloma istniejącymi bibliotekami Node.js.
    - **Wady**: Starsza składnia, mniej wsparcia w przeglądarkach (wymaga bundlera takiego jak Webpack).

1.  **ES Modules**:
    
    - **Zalety**: Nowoczesny standard, szerokie wsparcie w przeglądarkach i nowoczesnych narzędziach, lepsza integracja z narzędziami front-endowymi.
    - **Wady**: Wymaga nowszej wersji Node.js lub dodatkowej konfiguracji dla starszych wersji.
    - Nie jest to składnia w naturalnych warunkach wspierana przez Jest
    
### References:


---



