
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-07-23

---

**KLUCZOWE INFORMACJE W ROZDZIALE 3:**
	 • Tablice i ich właściwości 
	 • Tablice i ich metody
	 • Tablice wielowymiarowe
	 • Obiekty w JavaScript 
	 • Praca z obiektami i tablicami


### Tablice i ich właściwości

Tablice to listy wartości. Wartości mogą być każdego typu. Tablica może przechowywać wartości różnych typów np. string i number.

```js
arr1 = new Array("purple", "green", "yellow"); //niepoprawnie
arr2 = ["black", "orange", "pink"]; //poprawnie
```

```js
arr3 = new Array(10); // => [ <10 empty items> ] 
arr4 = [10]; // => [ 10 ]
```

UWAGA: Jeżeli zdefiniujemy tablicę z const można zmienić wartości stałej tablicy, ale nie można zmienić samej tablicy.

```js
const arr = ["hi there"]; 
arr[0] = "new value"; 
console.log(arr[0]); 

arr = ["nope, now you are overwriting the array"];

// => new value 
// => TypeError: Assignment to constant variable.
```


Mamy dostęp do elementów poprzez wskazanie odpowiedniego indeksu `cars[0]`. 
Możemy nadpisywać elementy `cars[0] = "Tesla"`. 
Length property `colors.length`
 - możemy jej użyć do dostania się do ostatniego elementu `lastElement = colors[colors.length - 1];`

UWAGA: Jeżeli przypiszemy nowy element pod niewłaściwym indeksem, który nie występuje w tablicy, zostaną utworzone puste miejsca i i tak będzie on dodany na odpowiednią pozycję.

```js
numbers = [12, 24, 36]; 
numbers[5] = 48; 
console.log(numbers.length);
console.log("numbers", numbers);

// => 6
// => numbers [ 12, 24, 36, <2 empty items>, 48 ]
```

### Tablice i ich metody

Metody wykonują akcje.
.push()
.splice()
.concat()
.pop()
.shift()
.splice()
delete

```js
delete arr8[0];
// => [ <1 empty item>, 6, 7, 8 ]
```

.find()
```js
arr8 = [ 2, 6, 7, 8 ]; 
let findValue = arr8.find(function(e) { return e === 6}); 
let findValue2 = arr8.find(e => e === 10); 
console.log(findValue, findValue2);
```

.indexOf()
lastIndexOf().
.sort()
.reverse()


### Tablice wielowymiarowe

Elementami tablicy są np. inne tablice. Stosujemy do wyszukiwania podwójne indeksy.

```js
let arrOfArrays2 = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
let value1 = arrOfArrays[0][1];
```


### Obiekty w JavaScript 

Tablice są specjalnym typem obiektów, który ma indeksowane właściwości. Wszystkie pozostałe obiekty, to obiekty o nazwanych właściwościach - nadajemy im niestandardową nazwę opisową zamiast   automatycznie wygenerowanego numeru indeksu.

```js
let dog = { dogName: "JavaScript", 
		    weight: 2.4, 
		    color: "brown", 
		    breed: "chihuahua", 
		    age: 3, 
		    burglarBiter: true 
		  };
```

Możemy zmienić wartość właściwości obiektów. Mamy dwie możliwości, aby to zrobić:
```js
dog["color"] = "blue"; 
dog.weight = 2.3;
```

Możemy także używać zmiennych aby odwoływać się do właściwości obiektu:
```js
let variable = "age"; 
console.log(dog[variable]);
```


### Praca z obiektami i tablicami

Możemy zagnieżdżać obiekty w innych obiektach. A także tablice w obiektach.

```js
company = { companyName: "Healthy Candy", 
		    activities: ["food manufacturing", "improving kids' health", "manufacturing toys"], 
		   address: { 
		       street: "2nd street", 
		       number: "123", 
		       zipcode: "33116", 
		       city: "Miami", 
		       state: "Florida" 
		   }, 
		   yearOfEstablishment: 2021 };
```

Jak dostać się do wybranej właściwości:
```js
company.address.zipcode = "33117"; 
company["address"]["number"] = "100";
let activity = company.activities[1];
```

Można także zagnieżdżać obiekty w tablicach, wtedy dostajemy się do niuch stosując: 
`let streetName = addresses[0].street;` indeks tablicy, następnie właściwość obiektu.



### References:
Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



