
--- 
tags: [[JS Functions]] [[Mock]]
date: 2024-07-10

---
Memoizacja to technika optymalizacji, która pozwala na zapamiętywanie wyników kosztownych obliczeń i zwracanie zapamiętanych wyników, gdy te same wejścia pojawiają się ponownie. Jest szczególnie użyteczna w funkcjach czystych (pure functions), które dla tych samych argumentów zawsze zwracają ten sam wynik.

```js
function memoizeTransform(f) {
    let lastArgs = null;
    let lastResult = null;

    return function(x, y) {
        if (lastArgs && x === lastArgs[0] && y === lastArgs[1]) {
            return lastResult;
        } else {
            lastResult = f(x, y);
            lastArgs = [x, y];
            return lastResult;
        }
    };
}
```

Testowanie funkcji memoizujących obejmuje sprawdzanie, czy wyniki są prawidłowe i czy funkcja źródłowa nie jest wywoływana ponownie, gdy argumenty są te same.

```js
// Definicja funkcji mock 
const fakeTransform = jest.fn((x, y) => [1, 1]); 

test('should not call the memoized function if the input is the same', () => { const memoizedTransform = memoizeTransform(fakeTransform); expect(memoizedTransform(5, 5)).toEqual([1, 1]); 								expect(memoizedTransform(5, 5)).toEqual([1, 1]); 								expect(fakeTransform).toBeCalledTimes(1); });
```

### References:


---



