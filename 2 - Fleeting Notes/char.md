
--- 
tags: [[JS]]
date: 2024-07-16

---
W JavaScript `char` nie jest specjalnym typem danych, ale możemy operować na pojedynczych znakach w ciągu znaków (stringu) za pomocą różnych metod i technik. W kontekście JavaScript, "char" zazwyczaj odnosi się do pojedynczego znaku w ciągu znaków.

Aby uzyskać pojedynczy znak z ciągu znaków, możemy użyć indeksowania lub metod takich jak `charAt` lub bezpośredniego indeksowania ciągu:

```js
let str = "Hello";
let char1 = str.charAt(0); // "H"
let char2 = str[1];        // "e"
```

### `charAt` vs Indeksowanie

- `charAt(index)` zwraca znak na podanej pozycji.
- Indeksowanie `str[index]` jest skrótem do uzyskania znaku na danej pozycji, ale może zwrócić `undefined` jeśli indeks jest poza zakresem.

### References:


---



