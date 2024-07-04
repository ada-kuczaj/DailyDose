
--- 
tags: [[JS]]
date: 2024-07-04

---
Prawidłowe nazywanie zmiennych, od razu wiadomo co się dzieje, wstawiasz nazwy zmiennych zamiast przedziałów matematycznych.

**DOBRZE**
```js
export function birdsInWeek(birdsPerDay, week) {
   let numberOfBirds = 0;
   let bottomBorder = (week-1)*7 ;
   let upperBorder  = bottomBorder+7 
    for(let i=bottomBorder ; i<upperBorder ; i++){
    numberOfBirds+= birdsPerDay[i];
    }
    return numberOfBirds;
}
```
**ŹLE**
```js
export function birdsInWeek(birdsPerDay, week) {
   let numberOfBirds = 0;
    for(let i=(week-1)*7 ; i<((week-1)*7)+7 ; i++){
    numberOfBirds+= birdsPerDay[i];
    }
    return numberOfBirds;
}
```
### References:


---



