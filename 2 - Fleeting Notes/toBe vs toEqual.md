
--- 
tags: [[Jest]] [[Jest methods]] [[Testing]] 
date: 2024-07-09

---
Obie metody służą do porównywania wartości, ale działają nieco inaczej i mają różne zastosowania.

### `toBe`

**Co robi**: `toBe` sprawdza, czy dwie wartości są identyczne przy użyciu operatora ścisłego porównania (`===`).

**Kiedy używać**: Używaj `toBe` do porównywania wartości prymitywnych (takich jak liczby, łańcuchy znaków, wartości logiczne, `null` i `undefined`).

**Przykład**:
```js
test('number comparison with toBe', () => {
    expect(3).toBe(3); // Test przejdzie, ponieważ 3 === 3
});

test('string comparison with toBe', () => {
    expect('hello').toBe('hello'); // Test przejdzie, ponieważ 'hello' === 'hello'
});
```

### `toEqual`

**Co robi**: `toEqual` sprawdza, czy dwie wartości są równe pod względem struktury i zawartości. Działa rekurencyjnie dla obiektów i tablic, sprawdzając ich klucze i wartości.

**Kiedy używać**: Używaj `toEqual` do porównywania obiektów, tablic i innych złożonych struktur danych.

**Przykład**:
```js
test('object comparison with toEqual', () => {
    const obj1 = { name: 'Alice', age: 25 };
    const obj2 = { name: 'Alice', age: 25 };
    expect(obj1).toEqual(obj2); // Test przejdzie, ponieważ obj1 i obj2 mają taką samą strukturę i zawartość
});

test('array comparison with toEqual', () => {
    const arr1 = [1, 2, 3];
    const arr2 = [1, 2, 3];
    expect(arr1).toEqual(arr2); // Test przejdzie, ponieważ arr1 i arr2 mają taką samą strukturę i zawartość
});
```

### Porównanie

- **`toBe`** używa operatora ścisłego porównania (`===`), więc sprawdza, czy dwie wartości są dokładnie takie same. Przydatne do porównywania prymitywów i sprawdzania tożsamości referencji obiektów.

- **`toEqual`** sprawdza, czy dwie wartości są strukturalnie równoważne, więc porównuje obiekty i tablice rekurencyjnie, aby upewnić się, że mają takie same wartości.
### References:


---



