# QM.js
A NodeJS project for simplifying logical expressions using the Quine-McCluskey Algorithm

## How to Use
There are 2 different ways to get a simplified logical expression:
 * Minterm method
 * Maxterm method
 
Both methods will get you the same function but they differ by how they are connected together
 * `A' + B'` (Minterm method) is the exact same as `AB` (Maxterm method)

### Minterm Method

```js
f = new QuineMcCluskey("ABC", [4, 5, 6, 7]);
console.log(f.getFunction()); // --> A

g = new QuineMcCluskey("ABC", [3, 4, 5, 6, 7]);
console.log(g.getFunction()); // --> A + B*C
```

### Maxterm Method

```js
f = new QuineMcCluskey("ABC", [0, 1, 2, 3], [], isMaxterm = true);
console.log(f.solve()); // --> A'

g = new QuineMcCluskey("ABC", [0, 1, 2], [], isMaxterm = true);
console.log(g.solve()); // --> (A'+B')*(A'+C')
```
Note that the parameters for `QuineMcCluskey` are `QuineMcCluskey(variables, values, dontCares = [], isMaxterm = false);`
Also, when using the maxterm method, do not forget to invert the values (`[0, 1, 2, 3]` becomes `[4, 5, 6, 7]`) or else you will get
an incorrect simplified expression.

### Using Don't Cares

```js
f = new QuineMcCluskey("ABC", [0, 1], dont_cares = [4, 5, 6, 7]);
console.log(f.solve()); // --> B'

g = new QuineMcCluskey("ABCD", [0, 2, 4, 8, 12], dont_cares = [6, 10, 11, 14, 15]);
console.log(g.solve()); // --> D'
```

## Feedback, Suggestions, Bugs

Any feedback, suggestions, or bugs can be mentioned in my [Discord Server](https://discord.gg/W8yVrHt).
