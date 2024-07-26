
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-07-24

---

**KLUCZOWE INFORMACJE W ROZDZIALE 5:**
	• while loop 
	• do while loop 
	• for loop 
	• for in 
	• for of 
	• break and continue



### While loop

Pętla while będzie wykonywana tylko wtedy, gdy warunek będzie spełniony, więc jeśli warunek będzie na początku fałszywy, znajdujący się w nim kod zostanie pominięty.

```js
let someArray = ["Mike", "Antal", "Marc", "Emir", "Louiza", "Jacky"]; 
let notFound = true; 

while (notFound && someArray.length > 0) { 
	if (someArray[0] === "Louiza") { 
		console.log("Found her!"); 
		notFound = false; 
	} else { 
		someArray.shift(); 
	} 
}
```

W warunku while dodano && SomeArray.length > 0. Gdybyśmy to pominęli, a szukanej wartości nie było w tablicy, utknęlibyśmy w nieskończonej pętli. Dlatego upewniamy się, że kończymy pętlę, jeśli nasza wartość nie jest obecna, aby nasz kod mógł być kontynuowany.


### Do while loop

Wykonuje to, co jest w bloku do, a następnie ocenia warunek w while. Jeśli warunek jest prawdziwy, ponownie wykonuje kod w bloku do. Będzie to kontynuowane, dopóki warunek w while nie zmieni się na fałsz.

```js
let number; 
do { 
	number = prompt("Please enter a number between 0 and 100: "); 
} while (!(number >= 0 && number < 100));
```

Możemy użyć metody `prompt()`, aby uzyskać dane wejściowe od użytkownika. Użyjmy pętli do while, aby poprosić użytkownika o podanie liczby między 0 a 100.


### For loops

Składniki pętli `for`: 
- **Inicjalizacja**: Jest to pierwszy element pętli, który wykonuje się tylko raz na początku. Służy do ustawienia początkowej wartości zmiennej sterującej pętlą.
- **Warunek**: Jest to wyrażenie logiczne, które jest sprawdzane przed każdą iteracją pętli. Jeśli warunek jest prawdziwy, blok kodu wewnątrz pętli jest wykonywany. Jeśli warunek jest fałszywy, pętla kończy swoje działanie.
- **Iteracja**: Jest to wyrażenie, które wykonuje się na końcu każdej iteracji pętli. Najczęściej służy do zmiany wartości zmiennej sterującej pętlą. 

```js
for (let i = 0; i < 10; i++) { 
	console.log(i); 
}
```

Jeśli nie zwiększymy wartości `i`, utkwimy w nieskończonej pętli, ponieważ wartość `i` by się nie zmieniała i byłaby mniejsza niż 10 na zawsze. Jest to coś, na co należy uważać we wszystkich pętlach!



### Nested loops

Zagnieżdżanie można  stosować z pętlami `while`, `for`, lub z kombinacją pętli `for` i `while`, a nawet z innymi rodzajami pętli; mogą być zagnieżdżane na kilka poziomów. Przykładem, w którym możemy użyć zagnieżdżonych pętli, jest sytuacja, gdy chcemy utworzyć tablicę tablic. Przy pomocy zewnętrznej pętli tworzymy tablicę najwyższego poziomu, a przy pomocy wewnętrznej pętli dodajemy wartości do tej tablicy.

```js
let outerArray = [];

for (let i = 0; i < 3; i++) {
    let innerArray = [];
    for (let j = 0; j < 3; j++) {
        innerArray.push(j);
    }
    outerArray.push(innerArray);
}

console.log(outerArray);

```

Użyliśmy zagnieżdżonych pętli, aby utworzyć tablicę w tablicy, co oznacza, że możemy pracować z wierszami i kolumnami po utworzeniu tej pętli. Oznacza to, że zagnieżdżone pętle mogą być używane do tworzenia danych tabelarycznych. Możemy wyświetlić ten wynik jako tabelę, korzystając z metody `console.table()`.


### Loops and arrays

```js
let names = ["Chantal", "John", "Maxime", "Bobbi", "Jair"];

for (let i = 0; i < names.length; i++) {
    if (names[i].startsWith("M")) {
        delete names[i];
        continue;
    }
    names[i] = "hello " + names[i];
}

console.log(names);
```

Trzeba uważać w tym miejscu. Jeśli mielibyśmy usunąć element zamiast tylko skasować jego zawartość i pozostawiać pusty element, przypadkowo pomijalibyśmy następną wartość, ponieważ ta wartość otrzymuje indeks niedawno usuniętej, a `i` jest inkrementowane i przechodzi do następnego indeksu.



### For of loop (arrays)

Istnieje inna pętla, której możemy użyć do iteracji po elementach tablicy: pętla `for...of`. Nie można jej użyć do zmiany wartości skojarzonej z indeksem, tak jak możemy to zrobić w zwykłej pętli, ale do przetwarzania wartości jest bardzo przyjazna i czytelna.

```js
let arr = [some array]; 
for (let variableName of arr) { 
//code to be executed 
//value of variableName gets updated every iteration 
//all values of the array will be variableName once 
}

let names = ["Chantal", "John", "Maxime", "Bobbi", "Jair"]; 
for (let name of names){ 
	console.log(name); 
}
```

Istnieją pewne ograniczenia; nie możemy modyfikować tablicy, ale możemy zapisać wszystkie elementy do bazy danych, pliku lub wysłać je gdzie indziej. Zaletą tego jest to, że nie możemy przypadkowo utknąć w nieskończonej pętli ani pominąć wartości.



### For in loop (objects)

Możemy iterować po właściwościach obiektu. Może to być pomocne, gdy musimy przejść przez wszystkie właściwości, ale nie znamy dokładnych właściwości obiektu, który iterujemy. Iterowanie po obiekcie można zrobić na kilka sposobów. Możemy użyć pętli `for...in`, aby iterować bezpośrednio po obiekcie, lub możemy przekształcić obiekt na tablicę i iterować po tej tablicy. Rozważymy oba podejścia w następnych sekcjach.

Pętla `for...in` jest nieco podobna do pętli `for...of`. Tutaj również musimy określić tymczasową nazwę, nazywaną także kluczem, aby przechowywać każdą nazwę właściwości obiektu. Musimy użyć `prop` z każdej iteracji pętli, aby uzyskać wartość z obiektu `car`.

```js
let car = {
    model: "Golf",
    make: "Volkswagen",
    year: 1999,
    color: "black"
};

for (let prop in car) {
    console.log(car[prop]);
}

//Golf 
//Volkswagen 
//1999 
//black
```

Jeśli po prostu zalogujemy `prop`, tak jak poniżej:

```js
for (let prop in car) {
    console.log(prop);
}

//model
//make
//year
//color
```

>[!IMPORTANT] **RÓŻNICA:**
>Jak widać, wszystkie nazwy właściwości są wypisane, a nie wartości. Dzieje się tak, ponieważ pętla `for...in` pobiera nazwy właściwości (klucze), a nie wartości. Pętla `for...of` robi odwrotnie; pobiera wartości, a nie klucze.
#### Przykład:

```js
const obj = {
    a: 1,
    b: 2,
    c: 3
};
for (let prop in obj) {
    console.log(prop, obj[prop]);
}
//`prop` to nazwa bieżącej właściwości
//`obj[prop]` to wartość bieżącej właściwości

const arr = ["a", "b", "c"];
for (let w = 0; w < arr.length; w++) {
    console.log(w, arr[w]);
}
//`w` to bieżący indeks
//`arr[w]` to wartość na bieżącym indeksie

for (el in arr) {
    console.log(el, arr[el]); 
} 
//`el` to bieżący indeks
//`arr[el]` to wartość na bieżącym indeksie


// Output:
//a 1
//b 2
//c 3

//0 a
//1 b
//2 c

//0 a
//1 b
//2 c

```

---
---
# Looping over objects by converting to an array (kilka sposobów)

Można użyć dowolnej pętli na obiektach, gdy tylko przekonwertujesz obiekt na tablicę. Można to zrobić na trzy sposoby:

1. Przekonwertować klucze obiektu na tablicę 
2. Przekonwertować wartości obiektu na tablicę
3. Przekonwertować wpisy klucz-wartość na tablicę (zawierającą tablice z dwoma elementami: klucz obiektu i wartość obiektu)

```js
let car = {
    model: "Golf",
    make: "Volkswagen",
    year: 1999,
    color: "black",
};
```


1. Przekonwertować klucze obiektu na tablicę 

Robimy to, używając wbudowanej funkcji ==`Object.keys(nazwaObiektu)`==.

```js
let arrKeys = Object.keys(car);
console.log(arrKeys);

//[ 'model', 'make', 'year', 'color' ]
```

Możemy iterować po właściwościach tej tablicy w ten sposób, używając pętli `for...of`:

```js
for(let key of Object.keys(car)) {
    console.log(key);
}
//model
//make
//year
//color
```

Podobnie możemy użyć pętli `for...of`, aby iterować po wartościach obiektu, konwertując wartości na tablicę. Główna różnica polega na tym, że używamy ==`Object.values(nazwaObiektu)`==:

```js
for(let value of Object.values(car)) {
    console.log(value);
}
//Golf
//Volkswagen
//1999
//black

```

Można iterować po tych tablicach w taki sam sposób, w jaki iterujesz po każdej tablicy. Możesz użyć strategii długości i indeksu w zwykłej pętli `for`:

```js
let arrKeys = Object.keys(car);
for(let i = 0; i < arrKeys.length; i++) {
    console.log(arrKeys[i] + ": " + car[arrKeys[i]]);
}
//model: Golf
//make: Volkswagen
//year: 1999
//color: black
```

Ciekawsze jest to, jak iterować po obu tablicach jednocześnie, używając pętli `for...of`. Aby to zrobić, musimy użyć ==`Object.entries()`==. Zademonstrujmy, co to robi:

```js
let arrEntries = Object.entries(car);
console.log(arrEntries);

//[ [ 'model', 'Golf' ], [ 'make', 'Volkswagen' ], [ 'year', 1999 ], [ 'color', 'black' ] ]

```

Jak widać, zwraca to tablicę dwuwymiarową, zawierającą pary klucz-wartość. Możemy iterować po niej w ten sposób:

```js
for (const [key, value] of Object.entries(car)) {
    console.log(key, ":", value);
}

//model: Golf
//make: Volkswagen
//year: 1999
//color: black
```

---
---
### break and continue

`break` i `continue` to dwa słowa kluczowe, których możemy używać do kontrolowania przepływu wykonania pętli. 

`break` zatrzyma pętlę i przejdzie do kodu poniżej pętli. Kiedy instrukcja `break` jest wykonana, pętla zakończy swoje działanie, nawet jeśli warunek pętli nadal jest prawdziwy. 

`continue` zatrzyma bieżącą iterację i wróci na początek pętli, sprawdzając warunek (lub w przypadku pętli `for`, wykonując instrukcję i następnie sprawdzając warunek).

Instrukcje `break` i `continue` mogą być również używane w zagnieżdżonych pętlach, ale ważne jest, aby wiedzieć, że kiedy `break` lub `continue` są używane w zagnieżdżonej pętli, pętla zewnętrzna nie zostanie przerwana.



### References:
Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



