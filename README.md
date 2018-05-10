# awesome-workshop
A workshop code collection that can be used in version 3.x
*Please consider that this is a work in progress.*

## Globals

### Functions / Prototypes

- `equals(a, b)`: Boolean
  - Applies to:
    - Math
      - `Math.equals(4, 5)` - Static
    - Number
      - `Number.equals(1, 1)`- Static
      - `1.equals(1)` - Prototype
    - Object
      - `Object.equals({a:1}, {b:2}[, {c:3}[, ...]])` - Static
      - `{a:1}.equals({b:2}[, {c:3}[, ...]])` - Prototype
    - String
      - `String.equals("1", 1.toString(10))` - Static
      - `"1".equals(1.toString(10))` - Prototype
- `format(a : String [, b : *[, c : *[, ...]]])`: String
  - Applies to:
    - String
      - `String.format("{0}, {1}", "Discord", "b1nzy")` - Static
      - `"{0}, {1}".format("Discord", "b1nzy")` - Prototype
- `gcd(...x: Number[])`: String
  - Applies to:
    - Math
- `isNullOrUndefined(obj)`: Boolean
  - Applies to:
    - Object
- `merge(a, b[, c[, ...]])`: Object
  - Applies to:
    - Object
      - `Object.merge({a:1}, {b:2}, {c:3})` - Static
      - `{a:1}.merge({b:2}, {c:3})` - Prototype
- `range(start[, end[, step])`: Number\[]
  - Applies to:
    - Math
      - `Math.range(5) // [0, 1, 2, 3, 4]` - Static
      - `Math.range(5, 20) // [5, 6, ..., 18, 19]` - Static
      - `Math.range(5, 20, 5) // [5, 10, 15]` - Static
    - Number
      - `Number.range(5) // [0, 1, 2, 3, 4]` - Static
      - `Number.range(5, 20) // [5, 6, ..., 18, 19]` - Static
      - `Number.range(5, 20, 5) // [5, 10, 15]` - Static
      - `5.range() // [0, 1, 2, 3, 4]` - Prototype
      - `5.range(20) // [5, 6, ..., 19, 20]` - Prototype
      - `5.range(20, 5) // [5, 10, 15]` - Prototype

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
- cli-table
- chance
- cheerio?
- fuzzy
- inquirer *equivalent for discord*
- jimp
- lodash
- mathjs
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
