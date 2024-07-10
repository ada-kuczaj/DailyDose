
--- 
tags: [[Object]]
date: 2024-07-09

---

If you try to retrieve a nested value in an object but the parent key does not exist, JavaScript will throw an error. To easily avoid this, optional chaining was added to the language specification in 2020. With the optional chaining operator `?.` you can ensure that JavaScript only tries to access the nested key if the parent was not `null` or `undefined`. Otherwise, `undefined` is returned.

```javascript
const obj = {
  address: {
    street: 'Trincomalee Highway',
    city: 'Batticaloa',
  },
};

obj.address.zipCode;
// => undefined

obj.residence.street;
// => TypeError: Cannot read property 'street' of undefined

obj.residence?.street;
// => undefined
```

### References:


---



