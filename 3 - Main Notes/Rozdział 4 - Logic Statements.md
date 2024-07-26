
--- 
tags: [[JAVASCRIPT_FROM_BEGINNER_TO_PROFESSIONAL]]
date: 2024-07-24

---

**KLUCZOWE INFORMACJE W ROZDZIALE 4:**
	 • if and if else statements
	 • else if statements
	 • Conditional ternary operators
	 • switch statements


Uwaga na operatory porównania i przypisania w nawiasach z if (x === y).

### Conditional ternary operators

```js
const id = true;
const message = (id) ? "Allowed In" : "Denied Entry";
console.log(message);
```


### Switch statements and combining cases


```js
let grade = "F";

switch(grade){
  case "F":
  case "D":
    console.log("You've failed!");
    break;
  case "C":
  case "B":
    console.log("You've passed");
    break;
  case "A":
    console.log("Nice!");
    break;
  default:
    console.log("I don't know this grade.");
}
```


### References:
Makovey, L. and Moiseev, A., 2021. _JavaScript from Beginner to Professional: Learn JavaScript quickly by building fun, interactive, and dynamic web apps, games, and pages_. BPB Publications.

---



