
--- 
tags: [[Testing]] [[Jest]] [[NodeJS]] 
date: 2024-07-03

---
# Inne metody poza expect().toBe()

W Jest oprócz `expect` i `toBe` istnieje wiele innych funkcji i metod do testowania różnych przypadków. Oto kilka z najczęściej używanych:

### Metoda `toEqual`
Porównuje obiekty lub tablice rekursywnie.

```js
test('object assignment', () => {
  const data = {one: 1};
  data['two'] = 2;
  expect(data).toEqual({one: 1, two: 2});
});
```

### Metoda `toBeNull`
Sprawdza, czy wartość jest `null`.

```js
test('null', () => {
  const n = null;
  expect(n).toBeNull();
});
```

### Metoda `toBeDefined`
Sprawdza, czy wartość jest zdefiniowana.

```js
test('defined', () => {
  const a = 1;
  expect(a).toBeDefined();
});
```

### Metoda `toBeUndefined`
Sprawdza, czy wartość jest niezdefiniowana.

```js
test('undefined', () => {
  let a;
  expect(a).toBeUndefined();
});
```

### Metody `toBeTruthy` i `toBeFalsy`
Sprawdzają, czy wartość jest "prawdziwa" lub "fałszywa" w kontekście logicznym.

```js
test('true or false', () => {
  expect(true).toBeTruthy();
  expect(false).toBeFalsy();
});
```

### Metoda `toContain`
Sprawdza, czy tablica lub string zawiera określoną wartość.

```js
test('array contains', () => {
  const shoppingList = [
    'diapers',
    'kleenex',
    'trash bags',
    'paper towels',
    'milk',
  ];
  expect(shoppingList).toContain('milk');
});
```

### Metoda `toHaveLength`
Sprawdza, czy tablica lub string ma określoną długość.

```js
test('length', () => {
  const array = [1, 2, 3];
  expect(array).toHaveLength(3);
});
```

### Metoda `toMatch`
Sprawdza, czy string pasuje do określonego wyrażenia regularnego.

```js
test('string matching', () => {
  expect('team').toMatch(/t/);
});
```

### Metoda `toThrow`
Sprawdza, czy funkcja rzuca określony wyjątek.

```js
function compileAndroidCode() {
  throw new Error('you are using the wrong JDK');
}

test('compiling android goes as expected', () => {
  expect(compileAndroidCode).toThrow('you are using the wrong JDK');
});
```

### Metoda `jest.fn()
Tworzy funkcję mock.

```js
const mockCallback = jest.fn(x => 42 + x);

test('mock callback', () => {
  forEach([0, 1], mockCallback);
  expect(mockCallback.mock.calls.length).toBe(2);
  expect(mockCallback.mock.calls[0][0]).toBe(0);
  expect(mockCallback.mock.results[0].value).toBe(42);
});
```

### Metoda `describe`
Grupuje powiązane testy razem.

```js
describe('matching cities to foods', () => {
  test('Vienna <3 sausage', () => {
    expect(isValidCityFoodPair('Vienna', 'Wiener Schnitzel')).toBe(true);
  });

  test('San Juan <3 plantains', () => {
    expect(isValidCityFoodPair('San Juan', 'Mofongo')).toBe(true);
  });
});
```

### References:

https://jestjs.io/docs/expect
---



