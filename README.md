# JavaScript Style Guide

MercadoLibre JavaScript Style Guide.

## Intro
The main goal of this guide is to set standards for writing our JavaScript files and components, helping the readability and maintainability of our code. By doing this, we can significantly reduce the time required to understand any front-end implementation.

By writing clean code, we are able to:

- achieve a code that’s easier to understand;
- detect errors and potential problems;
- easily identify what code can be reused;
- build or update any functionality on any code already implemented;
- work on any file regardless of who wrote it.

> "Consistent code, even when written by a team, should look like one person wrote it."
by [Addy Osmani](http://addyosmani.com/blog/javascript-style-guides-and-beautifiers/)

Based on:
- [JavaScript: The Good Parts](http://shop.oreilly.com/product/9780596517748.do)
- [Popular Coding Convention on Github](http://sideeffect.kr/popularconvention/#javascript)
- [Maintainable JavaScript](http://shop.oreilly.com/product/0636920025245.do)

## Table of contents

- [Comments](#comments)
- [Spacing](#spacing)
- [Commas & Semicolons](#commas--semicolons)
- [Literals](#literals)
- [Operators](#operators)
- [Variables](#variables)
- [Functions](#functions)
- [Loops](#loops)
- [Events](#events)
- [Conditionals](#conditionals)
- [Module Pattern](#module-pattern)
- [Linting](#linting)

## Comments
- All your code should be documented.
- Use single-line comment to add hints, notes, suggestions or warnings.
- Use multiple-line comment for formal documentation.
- Use [JSDoc3](http://usejsdoc.org/).

    ```js
    /**
     * Returns a shallow-copied clone of a given object.
     * @param {Object} obj A given object to clone.
     * @returns {Object}
     * @example
     * clone(object);
     */
    function clone(obj) {
        // TODO: We need to develop it.
    };
    ```

## Spacing
- Don't put whitespace at the end of line or on blank lines.

    ```js
    // DON'T
    function foo() {
        console.log('foobar');····
    };··
    ```

- Don't mix spaces and tabs.

    ```js
    // DON'T
    function foo() {
    ····console.log('foobar');
    ----console.log('bar');
    };
    ```

- Use 4 spaces for indentation. Don't use tabs.

    ```js
    // DON'T
    function foo() {
    ----console.log('foobar');
    };

    // DON'T
    function foo() {
    ··console.log('foobar');
    };
    ```

    ```js
    // DO
    function foo() {
    ····console.log('foobar');
    };
    ```

## Commas & Semicolons

### Commas

- Don't start with comma.

    ```js
    // DON'T
    var map = {
        'foo': 'foo'
      , 'bar': 'bar'
      , 'foobar': 'foobar'
    };
    ```

- Don't put the comma at the end of the last property. [Trailing commas in object literals are legal in ECMAScript 5](http://www.2ality.com/2013/07/trailing-commas.html), but don't use it for the time being.

    ```js
    // DON'T
    var map = {
        'foo': 'foo',
        'bar': 'bar',
        'foobar': 'foobar',
    };
    ```

- Put the comma at the end of the line.

    ```js
    // DO
    var map = {
        'foo': 'foo',
        'bar': 'bar',
        'foobar': 'foobar'
    };
    ```

### Semicolons
- Don't put semicolons at the end of
    - loops statements (`for`, `for...in` and `while`)

        ```js
        // DON'T
        for (var i = 0; i < 10; i += 1) {
            console.log('foobar');
        };
        ```

        ```js
        // DO
        for (var i = 0; i < 10; i += 1) {
            console.log('foobar');
        }
        ```

    - conditionals statements (`if...else`, `switch`)

        ```js
        // DON'T
        if (foo !== undefined) {
            console.log('foobar');
        };
        ```

        ```js
        // DO
        if (foo !== undefined) {
            console.log('foobar');
        }
        ```

    - funcions declarations

        ```js
        // DON'T
        function foo() {
            console.log('foobar');
        };
        ```

        ```js
        // DO
        function foo() {
            console.log('foobar');
        }
        ```

- Always put a semicolon at the end of the line.

    ```js
    // DON'T
    (function () {
        var foo = 'foobar'
        return foo
    }())
    ```

    ```js
    // DO
    (function () {
        var foo = 'foobar';
        return foo;
    }());
    ```
## Literals

- Use the array literal notation.
    ```js
    // DON'T
    var foo = new Array();
    ```

    ```js
    // DO
    var foo = [];
    ```

- Use the object literal notation.
    ```js
    // DON'T
    var foo = new Object();
    ```

    ```js
    // DO
    var foo = {};
    ```

## Operators

### Logical

- Use one space between operators.
    ```js
    // DON'T
    foo||bar;
    ```

    ```js
    // DO
    foo·||·baz;
    ```

### Arithmetic

- Use the assignment operator instead the increment or decrement operator.
    ```js
    // DON'T
    foo++;
    ```

    ```js
    // DO
    foo += 1;
    ```

- Use one space between operators.
    ```js
    // DON'T
    (1+2)*3;
    ```

    ```js
    // DO
    (1·+·2)·*·3;
    ```

## Variables

- Variable names should be nouns (don't worry about length).

- Don't use global variables.

    ```js
    // DON'T
    foo = 'bar';
    ```
- Name it in *lowerCamelCase*.
- Use one space before and after assignment.

    ```js
    // DON'T
    var foo='bar';
    ```

    ```js
    // DO
    var foo·=·'bar';
    ```

- Declare many variables in one statement. Use different lines for each variable.

    ```js
    // DON'T
    var foo;
    var bar;
    var baz;

    // DON'T
    var foo, bar, baz;
    ```

    ```js
    // DO
    var foo,
        bar,
        baz;
    ```

- Begin with $ the name of variables that contains a jQuery/Zepto element.

    ```js
    // DON'T
    var container = $('#foo');
    ```

    ```js
    // DO
    var $container = $('#foo');
    ```

- Define all variables on top.
    ```js
    // DON'T
    var foo;
    bar();
    var baz = 'example';
    ```

    ```js
    // DO
    var foo,
        baz;
    bar();
    baz = 'example';
    ```

## Functions

### Naming
- Function names should begin with a verb.

    ```js
    // DON'T
    function name(){
        // ...
    }
    ```
    ```js
    // DO
    function getName(){
        // ...
    }
    ```

- Function return booleans should begin with `is` or `has`.

    ```js
    // DON'T
    function error(){
        // ...
    }
    ```
    ```js
    // DO
    function hasError(){
        // ...
    }
    ```

### Declaration

- Define all variables at the top of the function body.
- Indent the function body.
- Name it in *lowerCamelCase*, unless it be a constructor function. In that case name it in *CamelCase*.
- Return `this` in all your public methods.
- Keep the name and the parenthesis together. Use a space only after parenthesis.
    ```js
    // DON'T
    function foo·()·{
        // ...
    }

    // DON'T
    function foo·(){
        // ...
    }
    ```
    ```js
    // DO
    function foo()·{
        // ...
    }
    ```

- On function expressions, use a space before and after the parenthesis.
    ```js
    // DON'T
    var foo = function(){
        // ...
    }
    ```
    ```js
    // DO
    var foo = function·()·{
        // ...
    }
    ```

- Don't put semicolon at the end of the function declarations.
    ```js
    // DON'T
    function foo() {
        // ...
    };
    ```
    ```js
    // DO
    function foo() {
        // ...
    }
    ```

- Only put a semicolon at the end of the function expressions.
    ```js
    // DON'T
    var foo = function () {
        // ...
    }
    ```
    ```js
    // DO
    var foo = function () {
        // ...
    };
    ```

### Execution

- Constructor functions must be executed with `new`.
- Wrap the entire function execution in parenthesis.

    ```js
    // DON'T
    var foo = (function () {
        // ...
    })();
    ```

    ```js
    // DO
    var foo = (function () {
        // ...
    }());
    ```

### Scope

- Use `that` to grab the reference to `this` scope.
    ```js
    // DO
    var that = this;
    ```

- Use `that` only for contexts that `this` can't reach.
    ```js
    // DON'T
    var that = this;

    that.addEventListener('click', function () {
        that.foo = 'example';
    });
    ```
    ```js
    // DO
    var that = this;

    this.addEventListener('click', function () {
        that.foo = 'example';
    });
    ```

## Loops

### for

- Dont't use the increment operator.
- Don't calculate the length on each iteration.
- Don't put semicolon at the end of the for statement.
- Declare variables outside of the for statement.
- Put opening brace on the same line.
- Put a space between 'for' and '('.
- Put a space between ')' and '{'.

    ```js
    // DON'T
    for(i = 0; i < foo.length; i++){
        console.log('foobar');
    };

    // DON'T
    for(var i = 0; i < foo.length; i++){
        console.log('foobar');
    };

    // DON'T
    for(i = 0; i < foo.length; i++)
    {
        console.log('foobar');
    };

    // DON'T
    for(x in foo){
        console.log('foobar');
    };

    // DON'T
    for(var x in foo){
        console.log('foobar');
    };
    ```

    ```js
    // DO
    var i = 0,
        len = foo.length;

    for·(i; i < len; i += 1)·{
        console.log('foobar');
    }

    // DO
    var x;

    for·(x in foo)·{
        console.log('foobar');
    }
    ```

### while
- Don't calculate the length on each iteration.
- Don't put semicolon at the end of the while statement.
- Put opening brace on the same line.
- Put a space between 'while' and '('.
- Put a space between ')' and '{'.

    ```js
    // DON'T
    var i = 0;

    while(i < foo.length){
        console.log('foobar');
        i++;
    };

    // DON'T
    var i = 0;

    while(i < foo.length)
    {
        console.log('foobar');
        i++;
    };
    ```

    ```js
    // DO
    var i = 0,
        len = foo.length;

    while·(i < len)·{
        console.log('foobar');
        i += 1;
    }
    ```

### do...while
- Put semicolon at the end of the do...while statement.
- Don't calculate the length on each iteration.
- Put opening brace on the same line.
- Put a space between 'do' and '{'.
- Put a space between '}' and 'while'.
- Put a space between 'while' and '('.
- Put a space between ')' and '{'.

    ```js
    // DON'T
    var i = 0;

    do{
       i++;
       console.log(i);
    }while (i < 5)

    // DON'T
    var i = 0;

    do
    {
       i++;
       console.log(i);
    }while (i < 5)
    ```

    ```js
    // DO
    var i = 0;

    do·{
       i += 1;
       console.log(i);
    }·while·(i < 5);
    ```

    ### forEach
    - Use `forEach` statement to iterate an array.

        ```js
        arr.forEach(function (x) {
            console.log(x);
        });
        ```

## Events

- Name it in *lowercases* without spaces.
- Define namespaces on event names.
    ```js
    // DON'T
    $(document).on('click', function () { ... });
    $(document).on('mouseenter', function () { ... });
    $(document).on('scroll', function () { ... });

    $(document).off('click');
    $(document).off('mouseenter');
    ```
    ```js
    // DO
    $(document).on('click.foo', function () { ... });
    $(document).on('mouseenter.foo', function () { ... });
    $(document).on('scroll.bar', function () { ... });

    $(document).off('.foo');
    ```

## Conditionals

- Use one space wrapping the condition parenthesis.
    ```js
    // DON'T
    if(foo){
        bar();
    }

    // DON'T
    if(·foo·){
        bar();
    }
    ```
    ```js
    // DO
    if·(foo)·{
        bar();
    }
    ```

- Use a new line for statements.
    ```js
    // DON'T
    if (foo) { bar(); }
    ```
    ```js
    // DO
    if (foo) {
        bar();
    }
    ```

- Use curly braces always.
    ```js
    // DON'T
    if (foo) bar();

    // DON'T
    if (foo)
        bar();
    ```
    ```js
    // DO
    if (foo) {
        bar();
    }
    ```

- Don't put semicolon at the end.
    ```js
    // DON'T
    if (foo) {
        bar();
    };
    ```
    ```js
    // DO
    if (foo) {
        bar();
    }
    ```

- Compare with `undefined` when it's not a boolean.
    ```js
    // DON'T
    if (baz) {
        foo();
    }
    ```
    ```js
    // DO
    if (baz !== undefined) {
        foo();
    }
    ```

- Use `===` and `!==` operators.
    ```js
    // DON'T
    if (baz == 'example') {
        foo();
    }
    ```
    ```js
    // DO
    if (baz === 'example') {
        foo();
    }
    ```

- Avoid `else if` when possible. Use `if` and `else` instead.
    ```js
    // DON'T
    if (foo !== undefined) {
        // statement 1
    } else if (bar !== undefined) {
        // statement 2
    } else {
        // statement 3
    }
    ```
    ```js
    // DO
    if (foo !== undefined) {
        // statement 1
        return;
    }

    if (bar !== undefined) {
        // statement 2
        return;
    }

    // statement 3
    ```

## Module Pattern
- Create a component into a file with the same name.
- Should start with an Immediately-Invoked Function Expression (IIFE).
- Use `'use strict';` at the top of the IIFE.
- Declare methods on its `prototype` property.
- Private members should be named with a trailing underscore.
- Use `events` instead of `callbacks`.
- Keep your components small.

    ```js
    // myComponent.js
    (function (window) {
        'use strict';

        function MyComponent() {...};

        MyComponent.prototype._private = function () {...};

        MyComponent.prototype.public = function () {...};

        // Expose component
        window.MyComponent = MyComponent;

    }(this));
    ```

## Linting

- Use [JSLint](http://www.jslint.com), [JSHint](http://www.jshint.com) or [ESLint](http://eslint.org/) to:
    - detect errors and potential problems;
    - improves your quality code;
    - avoids unused variables;
    - identifies problematic styles and patterns in your code;
    - reduces any syntax confusion.

- Use `jslint` with the following configuration:

        /*jslint browser: true, ass: true, nomen: true, regexp: true, todo: true, indent: 4 */


- Use `jshint` with the following configuration:

    ```js
    {
        "curly": true,
        "eqeqeq": true,
        "es3": true,
        "forin": true,
        "freeze": true,
        "immed": true,
        "indent": true,
        "latedef": true,
        "newcap": true,
        "noarg": true,
        "plusplus": true,
        "quotmark": "single",
        "undef": true,
        "unused": true,
        "strict": true,
        "trailing": true,
        "asi": true,
        "eqnull": true,
        "evil": true,
        "expr": true,
        "funcscope": true,
        "globalstrict": true,
        "laxcomma": true,
        "loopfunc": true,
        "smarttabs": true,
        "shadow": true,
        "sub": true,
        "supernew": true  
    }
    ```

- Use `eslint` with the following basic configuration:

    ```json
    {
      "env": {
        "browser": true,
        "jquery": true
      },
      "rules": {
        "block-scoped-var": [0],
        "comma-dangle": [2],
        "comma-style": [2, "last"],
        "curly": [2],
        "dot-notation": [0],
        "eqeqeq": [2],
        "guard-for-in": [1],
        "indent": [2],
        "no-array-constructor": [2],
        "no-caller": [2],
        "new-cap": [2],
        "no-eq-null": [0],
        "no-eval": [2],
        "no-extend-native": [2],
        "no-extra-semi": [2],
        "no-loop-func": [0],
        "no-mixed-spaces-and-tabs": [2],
        "no-new-wrappers": [2],
        "no-new-object": [2],
        "no-plusplus": [2],
        "no-shadow": [0],
        "no-spaced-func": [2],
        "no-trailing-spaces": [2],
        "no-undef": [2],
        "no-unused-expressions": [2],
        "no-unused-vars": [1, {"vars": "all", "args": "after-used"}],
        "no-use-before-define": [2],
        "quotes": [2, "single", "avoid-escape"],
        "space-after-keywords": [2, "always"],
        "space-before-blocks": [2, "always"],
        "space-before-function-paren": [2, {"anonymous": "always", "named": "never"}],
        "space-in-parens": [2, "never"],
        "space-infix-ops": [2],
        "space-return-throw-case": [2],
        "strict": [2, "global"],
        "vars-on-top": [2]
      }
    }
    ```

## License

Licensed under the MIT license.

Copyright (c) 2013 [MercadoLibre](https://github.com/mercadolibre).
