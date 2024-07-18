
--- 
tags: [[Methods]]
date: 2024-07-17

---
## String.prototype.charCodeAt()

The **`charCodeAt()`** method of [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) values returns an integer between `0` and `65535` representing the UTF-16 code unit at the given index.

`charCodeAt()` always indexes the string as a sequence of [UTF-16 code units](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_characters_unicode_code_points_and_grapheme_clusters), so it may return lone surrogates.

```js
"ABC".charCodeAt(0); // returns 65
```

## String.prototype.charAt()

The **`charAt()`** method of [`String`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) values returns a new string consisting of the single UTF-16 code unit at the given index.

`charAt()` always indexes the string as a sequence of [UTF-16 code units](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_characters_unicode_code_points_and_grapheme_clusters), so it may return lone surrogates.

```js
const anyString = "Brave new world";
console.log(`The character at index 0   is '${anyString.charAt(0)}'`);
The character at index 0   is 'B'
```

--- 

```js
const sentence = 'The quick brown fox jumps over the lazy dog.';

const index = 4;

console.log(
  `Character code ${sentence.charCodeAt(index)} is equal to ${sentence.charAt(
    index,
  )}`,
);
// Expected output: "Character code 113 is equal to q"
```

### References:
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt
---



