
--- 
tags: [[JS]]
date: 2024-07-14

---
# Cykl życia pamięci 

To proces alokacji, używania i zwalniania pamięci. Kiedy wykonujemy program, zmienne i wszystkie obiekty muszą być przechowywane w pamięci i dostępne. 

W JavaScript podstawowe problemy z pamięcią, które się pojawiają, dotyczą **wycieków pamięci (memory leaks)**, czyli sytuacji, gdy pamięć, która powinna zostać zwolniona, nadal działa.

## JavaScript ma dwie struktury danych dla pamięci:

- Sterta (The heap)
- Stos (The stack)

Kiedy przypisujesz wartości do zmiennych, zadaniem silnika JavaScript jest ustalenie, czy wartość jest wartością pierwotną, czy wartością referencyjną. Wynik określa, czy wartość jest przechowywana na stercie, czy na stosie.

## The Stack

Stos jest używany do przechowywania danych statycznych, gdzie rozmiar obiektu jest znany w momencie kompilacji kodu. Ponieważ rozmiar jest znany, dla obiektu zarezerwowana jest stała ilość miejsca, a stos pozostaje uporządkowany. Stos ma ograniczoną ilość miejsca dostarczaną przez system operacyjny, którą zazwyczaj przekracza się tylko w przypadku problemów w kodzie, takich jak nieskończona rekursja lub wycieki pamięci.

Wartości prymitywne, referencje do wartości nieprymitywnych i ramki wywołań funkcji (function call frames) są przechowywane na stosie. Referencje można porównać do numerów miejsc parkingowych w ogromnym (ale nieuporządkowanym) garażu, które wskazują, gdzie w pamięci JavaScript można znaleźć obiekty i funkcje.

## The Heap

Sterta zapewnia dynamiczną alokację pamięci w czasie wykonywania dla typów danych, które nie mają stałego rozmiaru, takich jak obiekty i funkcje. Są to wartości referencyjne, a do ich lokalizacji w nieuporządkowanej stercie używamy referencji o stałym rozmiarze przechowywanych na stosie. Jeśli modyfikujesz obiekt, modyfikujesz referencję do obiektu, a nie sam obiekt.

```js
const cat = {
    name: "Jupiter"
}

const pets = ["Jupiter", "Moshi", "Hercules"]
```

W tym przykładzie, `cat` jest przechowywany w stercie (heap), referencja do `cat` jest przechowywana na stosie (stack) i właściwość `name` jest przechowywana na stosie (stack). Tablica `pets` jest przechowywana w stercie (heap), a referencja do niej jest przechowywana na stosie (stack).

```js
let object = new Object();  
let object2 = object;  
object.greeting = "Hello, world";  
  
console.log(object2); // { greeting: 'Hello, world' }
```

W tym przykładzie, `object` i `object2` wskazują na ten sam obiekt w pamięci w stercie, ale za pomocą różnych zmiennych zapisanych na stosie.

### Podsumowanie

Stos służy do przechowywania danych o znanym rozmiarze w czasie kompilacji, takich jak wartości prymitywne i referencje do obiektów. Sterta jest używana do dynamicznej alokacji pamięci dla obiektów i funkcji, których rozmiar nie jest znany w momencie kompilacji. Referencje do obiektów w stercie są przechowywane na stosie, a modyfikacje obiektów dotyczą referencji, a nie samych obiektów.

---
# Cykl życia pamięci 

Cykl życia pamięci obejmuje trzy części:

1. **Alokacja pamięci (Memory allocation)**: Wartości są deklarowane i przechowywane w pamięci.
2. **Użycie pamięci (Memory in use)**: Wartości są odczytywane lub nadpisywane.
3. **Zwalnianie pamięci (Releasing memory)**: Wartości przestają być używane i są usuwane z pamięci.

## Alokacja pamięci

Gdy tworzymy zmienną lub deklarujemy wartości, następuje alokacja pamięci. Może to się odbywać na wiele sposobów:

- Regularne przypisanie zmiennej
- Przypisanie właściwości do obiektu
- Deklaracja funkcji wywoływalnych
- Wywoływanie funkcji

W poniższym przykładzie obiekt jest tworzony przy użyciu funkcji konstruktora `Instrument()`.Nazwy zmiennych zajmują miejsce w stosie, podczas gdy definicje funkcji i obiekty mają pamięć w stercie. Podczas wykonywania funkcji, rama jest dodawana do stosu, aż funkcja zostanie zakończona, po czym może zostać usunięta ze stosu.

![[Pasted image 20240714185957.png]]
![[Pasted image 20240714190029.png]]
![[Pasted image 20240714190049.png]]


___

## Wywoływanie funkcji

JavaScript alokuje pamięć podczas wykonywania funkcji. Gdy funkcja jest wywoływana, do stosu dodawana jest rama funkcji i alokowana jest pewna pamięć. Następnie, w miarę deklarowania kolejnych zmiennych lokalnych w trakcie wykonywania funkcji, więcej pamięci stosu jest alokowane na ramę funkcji. Nowe obiekty są przechowywane w stercie, z referencjami w ramie funkcji na stosie. Jeśli inna funkcja jest wywoływana wewnątrz tej funkcji, do stosu jest dodawana kolejna rama funkcji.

Gdy funkcja kończy wykonywanie, jej rama funkcji jest usuwana ze stosu, a używana przez nią pamięć jest dealokowana i ponownie dostępna dla reszty kodu. Po zakończeniu wykonywania funkcji, obiekty przechowywane w stercie, które nie mają już referencji ze stosu, mogą być zbierane przez system zarządzania pamięcią (**garbage collector**).

Podczas wykonywania, argumenty są przekazywane przez wartość lub referencję. Gdy przekazujesz wartości prymitywne, wartość jest przypisywana do argumentu w funkcji tak samo, jakbyś przypisywał ciąg znaków do innej zmiennej, co oznacza, że tworzona jest nowa wersja ciągu znaków.

```js
let str = "Hi"; 
let str2 = str;
```

W tym fragmencie kodu, `str` i `str2` są dwoma oddzielnymi prymitywami, oba przechowywane na stosie z przypisaną stałą ilością pamięci na przechowywanie ciągu znaków "Hi". Istnieją dwie oddzielne wersje ciągu "Hi".

Z drugiej strony, obiekty są przekazywane przez kopię zmiennej referencyjnej. Może to być źródłem błędów w kodzie, więc ważne jest, aby być świadomym, jak to działa. Jeśli przekażesz obiekt i zmodyfikujesz go w funkcji, oryginalny obiekt zostanie zmodyfikowany, ponieważ zarówno oryginalna zmienna, jak i wewnętrzna zmienna funkcji odwołują się do tego samego obiektu w pamięci.

```js
let aaliyah = {  
    name: "Aaliyah"  
}  
  
function nameObjectModification(obj, name) {  
    obj.name = name;  
    return obj;  
}  
  
let sarah = nameObjectModification(aaliyah, "Sarah");  
  
console.log(aaliyah); // { name: 'Sarah' }  
console.log(sarah); // { name: 'Sarah' }
```

W tym przykładzie, stworzyliśmy obiekt `aaliyah`, który JavaScript zapisał w stercie z referencją do niego na stosie. Następnie wywołaliśmy funkcję `nameObjectModification()` i przypisaliśmy ją do zmiennej `sarah`.

Kiedy stworzyliśmy obiekt `sarah` za pomocą funkcji `nameObjectModification()`, użyliśmy kopii referencji do obiektu `aaliyah`. W wywołaniu funkcji, obiekt, którego używamy i tworzymy, nadal odwołuje się do obiektu `aaliyah`, mimo że przypisujemy wartość zwrotną do nowej zmiennej. W rezultacie obie zmienne odwołują się do tego samego obiektu, a nazwa jest aktualizowana zarówno w obiekcie `aaliyah`, jak i w nowym obiekcie `sarah`.

### Podsumowanie

Podczas wykonywania funkcji w JavaScript, pamięć jest dynamicznie alokowana i dealokowana. Zmienna przekazywana jako wartość jest kopiowana, natomiast obiekty są przekazywane przez referencję, co może prowadzić do nieoczekiwanych modyfikacji w obiektach. Ważne jest zrozumienie tego mechanizmu, aby unikać potencjalnych błędów w kodzie.


---

## Memory in Use

Pamięć jest w użyciu, gdy odczytujesz i zapisujesz przydzieloną pamięć, co obejmuje następujące zadania:

- Przypisanie zmiennej
- Używanie zmiennych
- Przekazywanie argumentów do funkcji

## Releasing Memory: Garbage Collection

_Garbage collection_ odnosi się do procesu oczyszczania pamięci. Silnik JavaScript zarządza zbieraniem śmieci przy użyciu dwóch kluczowych algorytmów:

- Liczenie referencji (Reference-counting)
- Oznaczanie i zamiatanie (Mark-and-sweep)

Algorytmy zbierania śmieci wykorzystują różne podejścia do wykrywania, czy jakaś część pamięci nie jest już potrzebna programowi. Gdy pamięć nie jest już potrzebna, jest zwalniana i może być ponownie użyta. (Pamiętaj, że cała pamięć odnosi się do RAM, więc przestrzeń jest ograniczona).

### Liczenie referencji (Reference-counting)

Wszystkie obiekty, które tworzymy w swoim programie, mają przypisane referencje i pamięć.

Algorytm liczenia referencji wykorzystuje referencje do zmiennych, które znajdują się na stosie. Gdy tworzony jest obiekt, jego liczba referencji wynosi jeden. Jeśli utworzysz drugą zmienną wskazującą na ten obiekt, liczba referencji wynosi dwa. Jeśli funkcja korzysta z obiektu, liczba referencji zwiększa się o jeden.

Zazwyczaj wewnętrzne elementy wywołań funkcji są zbierane przez **garbage collector** po zakończeniu wykonywania funkcji, chyba że wewnętrzne elementy są nadal referencjonowane.

```js
let obj = new Object(); // reference count of one  
let obj2 = obj; // reference count of two  
obj2 = "string"; // obj has a reference count of one again
```

W algorytmie liczenia referencji, jeśli liczba referencji spada do zera, w  programie nie ma więcej referencji do obiektu, więc silnik JavaScript może oznaczyć ten blok pamięci jako wolny, aby przyszłe alokacje mogły go wykorzystać i nadpisać.


### Oznaczanie i zamiatanie (Mark-and-sweep)

Algorytm oznaczania i zamiatania działa okresowo i zaczyna od korzenia twojego kodu, globalnego obiektu. Od korzenia "przesuwa się" przez twój kod, aby znaleźć i oznaczyć wszystko, co jest "osiągalne" poprzez przemierzanie wszystkich zmiennych. Oznaczenie jest zazwyczaj czymś w rodzaju wartości logicznej. Po tym procesie, wszystkie zmienne, które nie są oznaczone (tzn. nie zostały oznaczone w pierwszym kroku i dlatego nie były osiągalne) będą zbierane przez system zarządzania pamięcią podczas fazy zamiatania. Proces ten jest powtarzany w trakcie wykonywania kodu.

### Co się dzieje gdy brakuje pamięci?

Gdy twój kod zużywa coraz więcej pamięci, może to wpływać na wydajność i powodować awarie aplikacji Node lub kart przeglądarki, lub opóźnienia. Jednym z powodów może być wyciek pamięci. Jeśli masz wyciek pamięci, program może próbować przydzielić więcej pamięci niż jest rzeczywiście dostępne, co może prowadzić do błędów pamięci. W przeglądarce, będzie to skutkować awarią karty.
### Wyciek pamięci

Gdy pamięć, która nie jest już potrzebna programowi, nadal istnieje, nazywamy to wyciekiem pamięci. Pamięć powinna zostać zwrócona do puli wolnej pamięci na przyszłe obiekty. Wyciek pamięci może wystąpić, gdy system zarządzania pamięcią nie znajdzie obiektu, który stracił swoje połączenie z obiektem korzenia, lub gdy obiekty rosną w rozmiarze i są referencjonowane przez inne obiekty. Może to powodować spowolnienia, awarie i wysokie opóźnienia w twoim kodzie.

### Typowe scenariusze powodujące wycieki pamięci

- **Niedomknięcia** (Messy Closures)
- **Zwisające timery i nasłuchiwacze zdarzeń** (Dangling Timers and Event Listeners)
- **Cykliczne referencje** (Circular References)


### References:
https://www.codecademy.com/courses/learn-javascript-best-practices/articles/javascript-intro-to-memory-management

---



