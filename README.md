# awesome-workshop
A workshop code collection that can be used in version 3.x
*Please consider that this is a work in progress.*

## Globals

### Expressions

- Array Swap  
  https://stackoverflow.com/questions/16201656/how-to-swap-two-variables-in-javascript  
  ```js
  let a = 1, b = 2;
  // all of the below are the same
  console.log('Before: %i, %i', a, b);
  console.log('Before: ' + a + ', ' + b);
  console.log(`Before: ${a}, ${b}`);
  
  b = [a, a = b][0];
  [b, a] = [a, b];
  // or you can be boring (apparently faster)
  var c = a; // var, let, const
  b = c;
  a = b;
  
  console.log(`After: ${a}, ${b}`)
  ```

### Functions / Prototypes

- `equals(a, b[, c[, ...]])`: Boolean  
  ```js
  function equals(a, b) {
    // ...
  }
  ```
  - Notes
    - Attempt to allow multiple arguments.  
      `arguments` or `...args` can be used
  - Applies to:
    - Array  
      ```js
      /** Static */
      Array.equals = function(a, b) {
        if(a.length !== b.length) { return false; }
        for(let i = this.length; i--;) {
          if(a[i] !== b[i]) { return false; }
        }
        return true;
      }
      
      /** Prototype */
      Array.prototype.equals = function(arr) {
        if(this.length !== arr.length) { return false; }
        for(let i = this.length; i--;) {
          if(this[i] !== arr[i]) { return false; }
        }
        return true;
      } 
      ```
      - `Array.equals([1, 2, 3], ['1', '2', '3']) // false` - Static
      - `[1, 2, 3].equals(['1', '2', '3']) // false` - Prototype
      - `[1, 2, 3].equals('1', '2', '3') // false` - Prototype
    - Math
      ```ts
      Math.equals = function(a : Number, b : Number) : Boolean {
        return !(isNaN(a) && isNaN(b)) && (a === b);
      }
      ```
      - `Math.equals(4, 5)` - Static
    - Number
      ```ts
      // Static
      Number.equals = function(...numbers: Number[]) {
        
      }
      
      // Prototype
      Number.prototype.equals = function(num) {
        return Math.equals(this, num);
      }
      ```
      - `Number.equals(1, 1)`- Static
      - `1.equals(1)` - Prototype
    - Object
      ```js
      Object.equals = function(a, b) {
        // ...
      }
      
      Object.prototype.equals = function(obj) {
        // ...
      }
      ```
      - `Object.equals({a:1}, {b:2}[, {c:3}[, ...]])` - Static
      - `{a:1}.equals({b:2}[, {c:3}[, ...]])` - Prototype
    - String
      ```js
      String.equals = function(a: String, b: String): Boolean {
        return Array.equals(a, b);
      }
      
      String.prototype.equals = function(a) {
        return Array.prototype.equals.call(this, a);
      }
      ```
      - `String.equals("1", 1.toString(10))` - Static
      - `"1".equals(1.toString(10))` - Prototype
- `format(a : String [, b : *[, c : *[, ...]]])`: String
  - Applies to:
    - String
      - `String.format("{0}, {1}", "Discord", "b1nzy")` - Static
      - `"{0}, {1}".format("Discord", "b1nzy")` - Prototype
- `format(n: Number) || formatNumber(n: Number | String)`: String
  - Applies to:
    - Number
      ```ts
      Number.format = function(n: Number): String {
        return n.toString().replace(/(\d)(?=(\d{3})+(?!\d)/g, "$1,")
      }
      
      Number.prototype.format = function(): String {
        return Number.format.call({}, this);
      }
      ```
    - String
      ```ts
      String.formatNumber = function(n: String | Number): String {
        return Number.format.call({}, Number(this));
      }
      
      String.prototype.formatNumber = function(): String {
        return // not implimented
      }
      ```
- `gcd(...x: Number[])`: String
  - Applies to:
    - Math
      ```ts
      Math.gcd = function(...arr : Number[]) {
      
      }
      ```
    - Number
      ```ts
      Number.gcd = function() {
        // arguments
      }
      
      Number.prototype.gcd = function() {
        // [this, ...arguments]
      }
      ```
- `isNullOrUndefined(obj)` : Boolean
  - Applies to:
    - Object
- `merge(a, b[, c[, ...]])` : Object
  - Applies to:
    - Object
      ```ts
      Object.merge = function(...arr : Object[]) {
        arr.reduce((prev : Object, curr : Object) => Object.assign(prev, curr), arr[1] /*: Object*/)
      }
      ```
      - `Object.merge({a:1}, {b:2}, {c:3})` - Static
      - `{a:1}.merge({b:2}, {c:3})` - Prototype
- `pow(n, power)` : Number
  - Applies to:
    - Math
      ```ts
      Math.pow = function (n : Number, p : Number) : Number {
        return Array(p - 1).fill(0).reduce((c : Number) => c * n, n);
      }
      ```
      - `Math.pow(2, 3) // 8` - Static
      - `Math.pow(8, 1/3) // Error (real integer required)` - Static
- `range(start[, end[, step])`: Number\[]
  - Applies to:
    - Math
      ```ts
      Math.range = function(start : Number = 0, end : Number = 5, step : Number = 1) : Number[] {
        return Array(end - start / step).fill(start).map(i => i * step + start);
      }
      ```
      - `Math.range(5) // [0, 1, 2, 3, 4]` - Static
      - `Math.range(5, 20) // [5, 6, ..., 18, 19]` - Static
      - `Math.range(5, 20, 5) // [5, 10, 15]` - Static
    - Number
      ```ts
      Number.range = function(start : Number, end : Number, step : Number) : Number[] {
        return Math.range(start, end, step);
      }
      
      Number.prototype.range = function(/* start : Number, */ end : Number, step : Number) : Number {
        // ???
      }
      ```
      - `Number.range(5) // [0, 1, 2, 3, 4]` - Static
      - `Number.range(5, 20) // [5, 6, ..., 18, 19]` - Static
      - `Number.range(5, 20, 5) // [5, 10, 15]` - Static
      - `5.range() // [0, 1, 2, 3, 4]` - Prototype
      - `5.range(20) // [5, 6, ..., 19, 20]` - Prototype
      - `5.range(20, 5) // [5, 10, 15]` - Prototype
    - String
      ```ts
      String.range = function(start : Number = "A", end : String = "D", step : Number = 1) {}
      String.prototype.range = function() {}
      ```

### Classes

## Environment Changes
*These changes are based on mozilla's documentation.*

- `eval()` and `uneval()` forbidden.
- Errors will only output the local environment folder.  
Parent folder paths will be removed.
- Some npm modules may be included in the environment by default.
- Considerations to make a package manager for the workshop as a way to improve response times.

## Package imports (scripts)
*None of the below are guaranteed to stay.*

- bluebird
- chance
- cheerio?
- fuzzy
- inquirer *equivalent for discord*
- jimp
- lodash
- mathjs
- pureimage
- snekfetch?
- underscore

- Restricted modules
  - *our version of the discord client*
  - *our version of a database driver*

## Package imports (pages)
*None of the below are guaranteed to stay.*

- axios
- jquery

## Package imports (debug)
*None of the below are guaranteed to stay.*

- babel
- eslint
- mocha
- semver

## Script compilers
*None of the below are guaranteed to stay.  
Conflicts exists in file extensions.*

- [Bizubee (.jsl?)](https://github.com/bizubee/bizubee)
- [CoffeeScript (.coffee)](http://coffeescript.org/)
- [LiveScript (.ls)](http://livescript.net)
- [IcedCoffeeScript (.iced)](http://maxtaco.github.io/coffee-script/)
- [LispyScript (.ls)](http://lispyscript.com/)
- [HotCocoaLisp (.hcl)](https://github.com/olleicua/hcl)

## Other languages to consider
*None of the below are guaranteed to stay.*

- C#
- Clojure
- ColdFusion
- Crystal
- Dart
- Elixir
- Elm
- Haskell
- Haxe
- Java
- JScript (ECMA3)
- Julia
- Kotlin
- Nim
- Python
- Rust
- TypeScript
- Visual Basic

## Page compilers

- Angular
- Ember
- Ejs
- [GrapesJS](https://github.com/artf/grapesjs) - Page Editor (like wix)
- ReactJS
- VueJS
- [CycleJS](https://cycle.js.org/)
- MarkoJS
- [MithrilJS](https://mithril.js.org/)
- PugJS
- Handlebars

## References

[Mozilla JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)  
[JavaScript Extensions](https://github.com/salsanfilippo/js-extensions)  
[Prototype Extensions](https://github.com/magnaar/prototype-extension/blob/master/object-extension.js)
