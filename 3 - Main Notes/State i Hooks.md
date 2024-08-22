--- 
tags: [[React]]
date: 2024-08-22

---
### <span style="color: #d11141;">Nieprawidłowy sposób aktualizowanie UI</span>

Nie możemy używać zwykłych zmiennych wewnątrz komponentów do aktualizacji
interfejsu użytkownika, ponieważ domyślnie dany komponent jest ładowany tylko raz i UI nie zostanie zaktualizowane. Musimy powiedzieć Reactowi, żeby ponownie załadował konkretny komponent zawierający nową treść.

![[Pasted image 20240822155658.png]]
### <span style="color: #00b159;">State w React</span>

W React, **state** jest mechanizmem, który pozwala komponentom na przechowywanie i zarządzanie danymi dynamicznymi, które mogą się zmieniać w czasie. State umożliwia komponentom reagowanie na zmiany i dynamiczne aktualizowanie interfejsu użytkownika w odpowiedzi na te zmiany.

State jest zazwyczaj inicjalizowany w konstruktorze (w przypadku klasowych komponentów  (`class components`) stan jest zarządzany przy użyciu `this.state` i aktualizowany przez `this.setState()`) lub za pomocą hooka `useState` (w przypadku komponentów funkcyjnych).

 Wartości w stanie mogą się zmieniać na podstawie interakcji użytkownika lub innych czynników, co automatycznie powoduje ponowne renderowanie komponentu z nowymi danymi.

![[Pasted image 20240822162428.png]]
### <span style="color: #00aedb;">Hooks w React</span>

React Hook to funkcja wprowadzona w bibliotece React od wersji 16.8, która umożliwia korzystanie z funkcji Reacta, takich jak stan (`state`) oraz efekty uboczne (`side effects`), w komponentach funkcyjnych. Przed wprowadzeniem hooków, zarządzanie stanem i cyklem życia komponentu było możliwe tylko w komponentach klasowych. Hooki pozwalają na bardziej elastyczne i prostsze podejście do zarządzania logiką w komponentach funkcyjnych.

Oto kilka popularnych hooków w React:

1. ==**`useState`**== - pozwala na zarządzanie stanem w komponencie funkcyjnym. Zwraca aktualny stan oraz funkcję do jego aktualizacji.
```js
const [count, setCount] = useState(0);
```

2. ==**`useEffect`**== - pozwala na wykonywanie efektów ubocznych (np. operacje asynchroniczne, manipulacje DOM) po renderowaniu komponentu. Można go używać do obsługi cyklu życia komponentu, takiego jak `componentDidMount`, `componentDidUpdate`, i `componentWillUnmount`.
```js
useEffect(() => {   
	document.title = `You clicked ${count} times`; 
	}, [count]);
```

3. ==**`useContext`**== - pozwala na dostęp do wartości z kontekstu Reacta bez potrzeby korzystania z render props czy wyższych komponentów (HOC).
```js
const value = useContext(MyContext);
```

4. ==**`useReducer`**== - alternatywa dla `useState` przy bardziej skomplikowanym zarządzaniu stanem, podobna do reduktorów znanych z biblioteki Redux.
```js
const [state, dispatch] = useReducer(reducer, initialState);
```

5. ==**`useRef`**== - pozwala na tworzenie odwołań (referencji) do elementów DOM lub przechowywanie wartości, która nie wymaga ponownego renderowania komponentu przy jej zmianie.
```js
const inputEl = useRef(null);
```

6. ==**`useMemo`**== - służy do optymalizacji wydajności poprzez pamiętanie wyniku obliczeń między renderami, jeśli zależności nie zmieniają się.
```js
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

### <span style="color: #f37735">Zalety Hooks</span>

- **Prostota i czytelność**: Umożliwiają pisanie prostych komponentów funkcyjnych, które są łatwiejsze do zrozumienia i testowania.
- **Ponowne użycie logiki**: Hooks pozwalają na łatwe dzielenie logiki stanu pomiędzy różne komponenty bez potrzeby korzystania z render props lub HOC (Higher-Order Components).
- **Kompaktowa struktura**: Eliminują konieczność używania klas, co upraszcza składnię i redukuje ilość boilerplate'u.


### <span style="color: #ffc425;">Zasady tworzenia hooks</span>

Szczególną cechą tych React Hooks jest to, że są one technicznie zwykłymi funkcjami, ale mogą być wywoływane tylko wewnątrz funkcji komponentu React lub wewnątrz innych React Hooks.

Nie mogą być zagnieżdżone w innym kodzie. w np. `handleClick()`, tylko należy je wywoływać na samej górze, na najwyższym poziomie funkcji w danym komponencie.

![[Pasted image 20240822162637.png]]

![[Pasted image 20240822160307.png]]

`useState` to jeden z najważniejszych hooków w React, ponieważ umożliwia on zarządzanie stanem komponentu, czyli danymi, które po zmianie wywołają ponowne załadowanie komponentu.

`useState` akceptuje argument, który jest domyślną wartością, którą React ma przechowywać i której ma użyć przy pierwszym renderowaniu tego komponentu.

A następnie `useState` zwróci wartość, którą można przechowywać w zmiennej lub stałej. Wartość, którą otrzymasz z powrotem, będzie tablicą zawierającą zawsze dokładnie dwa elementy. Dlatego tutaj możemy również użyć destrukturyzacji tablicy, standardowej funkcji JavaScript, aby przechowywać te dwa elementy w dwóch oddzielnych stałych. 

This Hook returns an array with exactly (!) two elements:
1. The current state value
2. A function that should be called to update the state value

![[Pasted image 20240822163811.png]]
![[Pasted image 20240822163800.png]]
![[Pasted image 20240822170035.png]]




### References:
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649230#overview
https://www.udemy.com/course/react-the-complete-guide-incl-redux/learn/lecture/39649238#overview

---



