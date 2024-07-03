
--- 
tags: [[Testing]] [[Jest]] [[NodeJS]] [[JS]]
date: 2024-07-03

---

W pliku `package.json` zmieniamy linię:
`"test": "echo \"Error: no test specified\" && exit 1"`
na:
`"test": "jest --coverage"`
>(dodatkowa wersja do wybierania sobie co chcemy uruchomić)
>`"test": "jest --watch"`

(coverage zapewnia pokrycie i generowanie raportu HTML)
Aby odpalić testy w konsoli bash wpisujemy: `npm test` 

![[run test jest.png]]
### Składnia - podstawowy test jednostkowy:

```js
// sum.js
function sum(a, b) {
  return a + b;
}
module.exports = sum;

// sum.test.js
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

### Testowanie wartości zwracanych przez funkcję:

```js
// multiply.js
function multiply(a, b) {
  return a * b;
}
module.exports = multiply;

// multiply.test.js
const multiply = require('./multiply');

test('multiplies 2 * 3 to equal 6', () => {
  expect(multiply(2, 3)).toBe(6);
});

test('multiplies 0 * 5 to equal 0', () => {
  expect(multiply(0, 5)).toBe(0);
});

```

### Testowanie wartości obiektów:

```js
// user.js
function createUser(name, age) {
  return {
    name,
    age,
  };
}
module.exports = createUser;

// user.test.js
const createUser = require('./user');

test('creates a user object with name and age', () => {
  const user = createUser('John', 30);
  expect(user).toEqual({ name: 'John', age: 30 });
});

```

### Testowanie funkcji asynchronicznych:

```js
// fetchData.js
async function fetchData() {
  return 'peanut butter';
}
module.exports = fetchData;

// fetchData.test.js
const fetchData = require('./fetchData');

test('the data is peanut butter', async () => {
  const data = await fetchData();
  expect(data).toBe('peanut butter');
});

// Using Promises
test('the data is peanut butter with promises', () => {
  return fetchData().then(data => {
    expect(data).toBe('peanut butter');
  });
});

```

### Użycie mocków do testowania zależności:

```js
// forEach.js
function forEach(items, callback) {
  for (let index = 0; index < items.length; index++) {
    callback(items[index]);
  }
}
module.exports = forEach;

// forEach.test.js
const forEach = require('./forEach');

test('mock callback', () => {
  const mockCallback = jest.fn(x => x + 42);

  forEach([0, 1], mockCallback);

  // Funkcja mock jest wywoływana dwa razy
  expect(mockCallback.mock.calls.length).toBe(2);

  // Pierwsze wywołanie funkcji mock dostaje 0 jako argument
  expect(mockCallback.mock.calls[0][0]).toBe(0);

  // Drugie wywołanie funkcji mock dostaje 1 jako argument
  expect(mockCallback.mock.calls[1][0]).toBe(1);

  // Pierwsze wywołanie funkcji mock zwraca 42
  expect(mockCallback.mock.results[0].value).toBe(42);
});

```

### References:

https://www.youtube.com/watch?v=FgnxcUQ5vho 
https://www.youtube.com/watch?v=r9HdJ8P6GQI  
[JavaScript Testing Introduction Tutorial - Unit Tests, Integration Tests & e2e Tests](https://www.youtube.com/watch?v=r9HdJ8P6GQI) 

---



