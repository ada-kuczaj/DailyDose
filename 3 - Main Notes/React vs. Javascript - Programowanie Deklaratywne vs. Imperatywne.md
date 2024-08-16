
--- 
tags: [[React]]
date: 2024-08-16

---
## Programowanie Deklaratywne vs. Imperatywne

![[Pasted image 20240816225632.png]]

### <span style="color: #00aedb;">Deklaratywne Programowanie (React):</span>

W React definiujesz docelowy stan interfejsu użytkownika, a nie kroki, które prowadzą do tego stanu. React samodzielnie wykonuje niezbędne kroki, aby osiągnąć zdefiniowany cel. W przykładzie po lewej stronie z Reactem:
- Definiujesz, jak UI ma wyglądać w zależności od stanu (czy użytkownik jest zalogowany).
- Wykorzystujesz JSX, by bezpośrednio określić strukturę interfejsu.

### <span style="color: #ffc425;">Imperatywne Programowanie (JavaScript):</span>
 
 W tradycyjnym JavaScript musisz zdefiniować kroki, które doprowadzą do pożądanego stanu interfejsu użytkownika. Programista musi manualnie manipulować DOM-em, by osiągnąć pożądany efekt. W przykładzie po prawej stronie:
- Musisz ręcznie wybierać elementy, zmieniać ich zawartość tekstową i dodawać je do DOM-u.

### Kluczowe różnice:

- **Deklaratywność:** W React skupiasz się na tym, **co** chcesz osiągnąć, a nie **jak** to zrobić.
- **Imperatywność:** W tradycyjnym JavaScript musisz dokładnie określić **jak** coś zrobić, krok po kroku.

To porównanie pokazuje, że React upraszcza proces tworzenia interfejsów użytkownika, abstrahując złożoność operacji na DOM-ie i skupiając się na ostatecznym wyglądzie interfejsu, co czyni go bardziej zrozumiałym i łatwiejszym w utrzymaniu.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/38345146#content
https://codesandbox.io/p/sandbox/react-vs-vanilla-demo-uc08fv?file=%2Fsrc%2Fstyles.css 
https://codesandbox.io/p/sandbox/vanilla-js-demo-6049kj?file=%2Findex.js
---



