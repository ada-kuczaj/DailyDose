--- 
tags: [[React]]
date: 2024-09-13

---
### <span style="color: #f37735">Co to jest prop drilling?</span>

**Prop drilling** (wiercenie przez propsy) to termin używany w React do opisu procesu przekazywania danych z komponentu nadrzędnego (rodzica) do komponentu zagnieżdżonego głęboko w drzewie komponentów, poprzez wiele pośrednich komponentów, które w rzeczywistości nie potrzebują tych danych. Dane (lub funkcje) są przekazywane jako "propsy" z komponentu rodzica do dziecka w dół drzewa.
### <span style="color: #d11141;">Rozwiązania problemu Prop Drilling</span>

1. **Context API**: React posiada Context API, które pozwala przekazywać dane głęboko przez drzewo komponentów bez potrzeby ręcznego przekazywania propsów na każdym poziomie. Pomaga to uniknąć prop drilling, oferując bardziej "globalny" sposób zarządzania stanem.

2. **Biblioteki zarządzania stanem**: Biblioteki takie jak Redux, Zustand czy MobX oferują centralne zarządzanie stanem, co pomaga w przechowywaniu i zarządzaniu stanem globalnie, redukując potrzebę przekazywania propsów przez wiele komponentów.

![[Pasted image 20240913214022.png]]

### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/8246378#questions

---



