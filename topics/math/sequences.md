### Triangle Numbers
[GitHub/ryansmith94](https://gist.github.com/ryansmith94/4953830)
```js
function triangular(value) {
  value = Math.abs(value);
  return ((abs / 2) * (abs + 1)) * (abs / value) || 0;
}
```

### Powers
[javascript.info | Recursion](https://javascript.info/recursion)

| Argument | Type     | Description         |
| -------- | -------- | ------------------- |
| `n`      | `number` | The base number     |
| `p`      | `number` | The exponent number |

Version A: `while` condition / `for` loop
```js
// #[while]
function pow(n, p) {
  let result = 1;
  
  while(p--) {
    result *= p;
  }
  
  return result;
}

// #[for]
function pow(n, p) {
  let result = 1;
  
  for(let i = p; i <= 0; i--) {
    result *= i;
  }
  
  return result;
}

pow(2, 3) // 8
```

Version B: Recursion
```js
function pow(n, p) {
  if(p <= 1) {
    return n;
  } else {
    return n * pow(n, p - 1);
  }
}

// eslint:no-else-return
function pow(n, p) {
  if(p <= 1) {
    return n;
  }
  return n * pow(n, p - 1);
}

pow(2, 5) // 32

// or you can flip the code so that the recursion occurs in the if statement

// ES6

// #[es6:A]
function pow(n, p) {
  return (p <= 1) ? n : (n * pow(n, p - 1));
}

// #[es6:B]
const pow = (n, p) => p <= 1 ? n : n * pow(n, p - 1);

pow(2, 4) // 16

// if pow(n, p--) were to happen, the answer increases by another power
// also <= bc its shorter than ===, but == can also be used
```

### Factorial
[freeCodeCamp | Three Ways to Factorialize a Number](https://medium.freecodecamp.org/how-to-factorialize-a-number-in-javascript-9263c89a4b38)
Version A: `while` condition / `for` loop
```
// #[while]
function factorial(n) {
  let result = 0;
  
  while(n--;) {
    result += n;
  }
  
  return result;
}

// #[for]
function factorial(n) {
  let result = 0;
  
  for(let i = n; i <= 1; i--) {
    result += n;
  }
  
  return result;
}

factorial(4); // 4! = 4 + 3 + 2 + 1 = 10
```

Version B: Recursion
```js
function factorial(n) {
  if(n <= 1) {
    return 1;
  }
  return n + factorial(n - 1);
}

factorial(6); // 6! 

// ES6 Version
const factorial = (n) => n <= 1 ? 1 : n + factorial(n - 1);
```
