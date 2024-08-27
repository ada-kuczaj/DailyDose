--- 
tags: [[React]]
date: 2024-08-26

---
Podczas pracy z Reactem (lub innymi frameworkami opartymi na komponentach), ważną praktyką jest aktualizowanie stanu obiektów w sposób niezmienny (immutably). Oznacza to, że zamiast bezpośrednio modyfikować obiekt stanu, tworzymy jego nową kopię z wprowadzonymi zmianami. Jest to szczególnie ważne przy pracy z obiektami i tablicami.

![[Pasted image 20240826151329.png]]

### <span style="color: #d11141;">Dlaczego jest to ważne?</span>

1. **Śledzenie zmian stanu**: React polega na porównywaniu poprzedniego i nowego stanu w celu efektywnego renderowania komponentów. Modyfikując stan bezpośrednio, możemy zmylić mechanizmy Reacta, co może prowadzić do błędów i nieprzewidywalnego zachowania aplikacji.

2. **Czystość funkcji**: Zachowanie niezmienności stanu wspiera funkcjonalny styl programowania, w którym funkcje są czyste, czyli nie zmieniają swoich argumentów i zawsze zwracają ten sam wynik dla tych samych danych wejściowych.

3. **Debugowanie**: Niezmienność ułatwia śledzenie błędów i zrozumienie zmian stanu, ponieważ możemy łatwo porównać różne stany w różnych momentach działania aplikacji.
### <span style="color: #00b159;">Jak to robić?</span>

**Spread Operator (`...`)**: Możemy używać operatora rozpraszania, aby utworzyć nową kopię obiektu lub tablicy z wprowadzonymi zmianami.

```js
const updatedState = {
    ...previousState,
    keyToUpdate: newValue
};
```

**Metody Array (np. `map`, `filter`)**: Zamiast modyfikować tablicę bezpośrednio, używaj metod, które zwracają nową tablicę.

```js
const updatedArray = previousArray.map(item => {
    return item.id === idToUpdate ? { ...item, updatedProp: newValue } : item;
});
```
### <span style="color: #00aedb;">Źle i dobrze - przykład</span>

![[Pasted image 20240826152558.png]]

Prawidłowa wersja:
![[Pasted image 20240826191246.png]]


### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39659798#content

---



