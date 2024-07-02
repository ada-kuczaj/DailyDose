
--- 
tags: [[Testing]] [[Visual Studio]] [[Jest]]
date: 2024-07-02

---
Pokazuje raport, który mówi jak duża część kodu jest objęta testami jednostkowymi.

Aby zobaczyć raport pokrycia kodu, wpisz w terminalu następujące polecenie:

```js
jest --coverage
```

Lub używając Visual Studio Code z rozszerzeniem Jest, można uruchomić polecenie (CTRL+SHIFT+P) _Jest: Toggle Coverage Overlay_ 
Pokaże to już w implementacji, które linie kodu nie są objęte testami.

![[lines of code not covered by tests.png]]

Jest utworzy też raport HTML, który znajdziemy w folderze: `coverage/lcov-report/index.html`.

![[code coverage raport.png]]

### References:

https://www.freecodecamp.org/news/how-to-start-unit-testing-javascript/
---



