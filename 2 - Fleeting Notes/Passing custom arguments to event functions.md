--- 
tags: [[React]]
date: 2024-08-22

---
Dzięki temu, że funkcja `handleSelect()` akceptuje teraz parametr, mamy możliwość otrzymania jednego z 4 stringów (na zielono) jako wartość naszego parametru.

Aby kontrolować jak funkcja` handleSelect()` zostanie wyegzekwowana przez React, możemy przekazać funkcję strzałkową jako wartość do `onSelect`.

Teraz możemy wpisać nawiasy do `handleSelect()`, które jest wewnątrz ciała funkcji strzałkowej, ponieważ zostanie wywołane dopiero po naciśnięciu guzika.

![[Pasted image 20240822150720.png]]

![[Pasted image 20240822150711.png]]

![[Pasted image 20240822150745.png]]

Dzięki takiemu zabiegowi możemy zamienić place holder Dynamic kontent w zależności od tego, który z guzików został naciśnięty.

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649214#overview

---



