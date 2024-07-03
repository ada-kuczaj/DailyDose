
--- 
tags: [[JS]]
date: 2024-07-03

---

### 1. Stałe Wartości (tzw. Constant Values)

Dla stałych wartości, które są niezmienne przez cały czas trwania programu, zazwyczaj używa się wielkich liter (drukowanych liter) oraz podkreśleń do oddzielania wyrazów. Jest to podobne do konwencji stosowanej w innych językach programowania, takich jak C czy Java.

```js
const MAX_USERS = 100;
const API_KEY = '12345-abcde';
```

### 2. Zmiennie Konfiguracji (Configuration Variables)

Zmiennie konfiguracyjne, które mogą być ustawione raz, a potem niezmieniane, często również są zapisywane wielkimi literami.

```js
const DATABASE_URL = 'mongodb://localhost:27017/mydatabase';
const PORT = 3000;
```

### 3. Zmiennie, które nie są stałymi wartościami

Dla innych zmiennych, zadeklarowanych za pomocą `let`,które mogą zmieniać swoją wartość, zazwyczaj stosuje się camelCase,  

```js
let userAge = 25;
let userName = 'John Doe';
let userSettings = {
  theme: 'dark',
  language: 'en'
};
```


Podsumowując, stosowanie wielkich liter dla stałych wartości i zmiennych konfiguracyjnych jest dobrą praktyką, która pomaga odróżnić je od zwykłych zmiennych w kodzie. Warto jednak przestrzegać ustalonych konwencji w zespole lub projekcie, aby kod był spójny i czytelny dla wszystkich.

### References:


---



