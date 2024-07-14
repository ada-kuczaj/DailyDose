
--- 
tags: [[JS Functions]] [[Callback]]
date: 2024-07-12

---

```js
const order = 'SUCCESS';

function onSuccess(callback) {
    return callback(order);
}

function notify(order) {
    return { message: `${order}` };
}

console.log(onSuccess(notify));

module.exports = {
    onSuccess,
    notify
}
```

>[!NOTE]
>W JavaScript, kiedy przekazujesz funkcję jako argument do innej funkcji, nie dodajesz nawiasów, ponieważ nawiasy wywołują funkcję. Jeśli dodasz nawiasy, przekazujesz wynik wywołania funkcji, a nie samą funkcję.

**W tym przykładzie:**

1. **`onSuccess(callback)`**: Funkcja `onSuccess` przyjmuje jako argument `callback`, który jest funkcją.
2. **`onSuccess(notify)`**: Przekazujemy funkcję `notify` jako argument do `onSuccess` bez nawiasów, ponieważ chcemy przekazać samą funkcję, a nie jej wynik.
3. **`callback(order)`**: Wewnątrz `onSuccess`, `callback` jest wywoływane z argumentem `order`, co oznacza, że faktycznie wywołujemy funkcję `notify` z argumentem `order`.

---

#### Przykład z Wywołaniem Funkcji (Złe Przekazanie)

Jeśli przekazałbyś funkcję z nawiasami, tak jak poniżej:
```js
console.log(onSuccess(notify()));
```
**To co faktycznie się dzieje, to:**

1. **`notify()`**: Funkcja `notify` jest wywoływana natychmiast z aktualnym kontekstem (a nie z kontekstem wewnątrz `onSuccess`), co zwraca `{ message: 'SUCCESS' }`.
2. **`onSuccess(notify())`**: W wyniku tego `onSuccess` otrzymuje wynik funkcji `notify`, czyli obiekt `{ message: 'SUCCESS' }`, zamiast funkcji `notify`.


### Podsumowanie

- **Przekazywanie Funkcji jako Argument**: Używasz nazwy funkcji bez nawiasów, aby przekazać funkcję jako argument, ponieważ chcesz przekazać odniesienie do funkcji, a nie wynik jej wywołania.
- **Wywoływanie Funkcji**: Używasz nazwy funkcji z nawiasami, aby ją wywołać.

Dlatego w przykładzie `console.log(onSuccess(notify));` funkcja `notify` jest przekazywana jako argument bez nawiasów, aby `onSuccess` mogła ją wywołać w odpowiednim momencie z odpowiednimi argumentami.

### References:


---



