```js
function add() {
    var args = Array.prototype.slice.call(arguments);
    if (args.length <= 1) {
        return args[0];
    }
    return !!(args[0] + and.apply(this, args.slice(1)))
}

function add() {
    /**
     * @type {Number[]}
     */
    var args = Array.prototype.slice.call(arguments);
    return args.reduce((p, c) => p + c, 0);
}

// ES6
const add = (...args) => args[1] ? args[0] + and(...args.slice(1)) : args[0];
const add = (...args) => args[1] ? args.reduce((p, c) => p + c, 0) : args[0];
```
The same can be done with the following:
- Addition `a + b`
- Subtraction `a - b`
- Division `a / b`
- Multiplication `a * b`
- Remainder `a % b`
- Expoentiation `a ** b`
- Increment `a++`
- Decrement `a--`
- Bitwise AND `a & b`
- Bitwise OR `a | b`
- Bitwise XOR `a ^ b`
- Bitwise NOT `~ a`
- Left shift `a << b`
- Sign-propagating right shift `a >> b`
- Zero-fill right shift `a >>> b`