--- 
tags: [[React]]
date: 2024-08-23

---
### <span style="color: #d11141;">Do czego służy Fragment?</span>

Fragment w React służy do grupowania listy elementów potomnych (children) bez dodawania dodatkowego węzła (noda) do drzewa DOM.

W standardowej sytuacji, gdy chcemy zwrócić więcej niż jeden element z komponentu React, musimy je owinąć w jeden wspólny element, np. `<div>`. Problem z tym podejściem polega na tym, że takie dodatkowe elementy mogą niepotrzebnie zaśmiecać strukturę DOM, co może wpływać na układ CSS, wydajność lub nawet semantykę strony.

![[Pasted image 20240823201154.png]]![[Pasted image 20240823201117.png]]![[Pasted image 20240823201451.png]]
![[Pasted image 20240823201427.png]]

### <span style="color: #00b159;">Jak temu zaradzić?</span>

### Wersja 1:
![[Pasted image 20240823201525.png]]
![[Pasted image 20240823201710.png]]
### Wersja 2:
![[Pasted image 20240823201755.png]]
![[Pasted image 20240823201815.png]]


### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659742#overview

---



