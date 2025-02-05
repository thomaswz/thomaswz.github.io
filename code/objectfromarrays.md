# Creating an object from two arrays

###### Created 3 May 2020, Updated 9 May 2020

> reference

### the Magic

The arrays must be the same length:

```javascript
columns.forEach((key, i) => (result[key] = rows[i]));
```

### Working with Objects

```javascript
let abc = { a: 1, b: 2, c: 3 };

Object.keys(abc) = [a, b, c];
Object.values(abc) = [1, 2, 3];
Object.entries(abc) = { a: 1, b: 2, c: 3 };
