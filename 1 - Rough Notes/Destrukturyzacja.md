--- 
tags: [[JS]]
date: 2024-08-20

---
**Destrukturyzacja** to wygodny sposób przypisywania wartości z tablic lub obiektów do zmiennych w JavaScript. Pozwala to na wydobycie danych bezpośrednio do zmiennych, co czyni kod bardziej czytelnym i zwięzłym.
#### <span style="color: #d11141;">Przykład z Tablicami</span>

Zamiast używać:
```js
const = ["Max", "Schwarzmüller"];
const firstName = userNameData[0];
const lastName = userNameData[1];
```
Można to zrobić w jednym kroku:
```js
const [firstName, lastName] = ["Max", "Schwarzmüller"];
```

#### <span style="color: #00b159;">Przykład z Obiektami</span>
Zamiast używać:
```js
const user = {
name: 'Max',
age: 34
};
const name = user.name;
const age = user.age;
```

Można to zrobić w jednym kroku:
```js
const {name: userName, age} = {
name: 'Max',
age: 34
};
```

>[!NOTE] Uwaga!
>Tutaj ważne są nazwy. Musimy użyć takich samych jak w obiekcie, a nie dowolnych przez nas wymyślonych. Bo w array są wyciągane za pomocą pozycji a z obiektu za pomocą property name. Jeżeli bardzo chcemy swoje nazwy możemy przypisać aliasy.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/38345330#overview

---



