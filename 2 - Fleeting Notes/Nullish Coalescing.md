
--- 
tags:  [[Undefined]] [[Object]]
date: 2024-07-09

---

There are situations where you want to apply a default value in case a variable is null or undefined (but only then). To address this, the nullish coalescing operator `??` was introduced in 2020. It returns the right-hand side operand only when the left-hand side operand is `null` or `undefined`. Otherwise, the left-hand side operand is returned.

```javascript
let amount = null;
amount = amount ?? 1;
// => 1

amount = 0;
amount = amount ?? 1;
// => 0
```

### References:


---



