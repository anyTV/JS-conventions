# JavaScript Convention

All code in any code-base should look like a single person typed it, no matter how many people contributed.

Source codes should be like a book, understandable by reading from top to bottom.
Choose readability over performance in most cases.

Use `.jshintrc` to verify code quality. Use `.jsbeautifyrc` to format code.


Our sublime plugins:
- [JSHint Gutter](https://github.com/victorporof/Sublime-JSHint)
- [HTML-CSS-JS Prettify](https://github.com/victorporof/Sublime-HTMLPrettify)

Some of the conventions will be handled by HTML-CSS-JS Prettify plugin.

## Manifesto


1. Soft Indents (4 spaces)
2. Beautiful Syntax

    A. Parens, Braces, Linebreaks

    ```javascript
    // if/else/for/while/try always have spaces, braces and span multiple lines
    // this encourages readability

    // Bad
    if (condition) dothis;

    for (i = 0; i < max; i += 1)
        foo();

    // Good

    if (condition) {

    }
    else if (condition) {

    }
    else {

    }

    while (condition) {

    }

    for (i = 0; i < max; i += 1) {

    }

    try {

    }
    catch (e) {

    }

    ```

    B. Assignments, Declarations, Functions ( Named, Expression, Constructor )

    ```javascript
    // Using only one `var` per scope (function) promotes readability
    // and keeps your declaration list free of clutter (also saves a few keystrokes)
    // `var` statements should always be in the beginning of their respective scope (function).
    // it's like preparing ingredients before you cook

    // Bad
    function fn () {

        // some statements

        var a = 3;
    }

    // Good
    var fn = function () {
        var a = 3;

        // some statements
    }
    ```

    ```javascript
    // Forget about named functions, always create functions
    // by creating an anonymous one then assign to a variable.
    // This way, we only have one way of declaring things

    // not really bad, we just prefer the other way for uniformity
    function foo () {

    }

    // Good
    var foo = function () {

    };
    ```

    C. Exceptions, Slight Deviations

    ```javascript
    // None yet
    ```

    D. Consistency Always Wins

    ```javascript
    // Notice the spaces in the following snippets

    if (condition) {
        // statements
    }

    while (condition) {
        // statements
    }

    for (declaration; condition; increment/decrement) {
        // statements
    }

    if (condition) {
        // statements
    }
    else {
        // statements
    }

    switch (foo) {
        case 1 :
            // statements
            break;

        case 2 :
            // statements
            break;

        case 3 :
            // statements
            break;

        default :
            // statements
    }

    var foo = [1, 2, 3],
        bar = {
            prop1 : value,
            prop2 : value2
        };

    if (foo === bar) {

    }

    var foo = 1 + (1 * 2);
    ```

    E. Quotes

    ```javascript
    // Single quotes on strings
    var foo = 'string';
    ```

    F. End of Lines and Empty Lines

    ```javascript
    // Always trim trailing spaces

    var a = 1;
    // ^ There should not be a space after the semi-colon

    // Put an empty line before end of file
    ```
3. Type Checking

    A. Actual Types

    ```javascript
    // String :
    typeof variable === 'string'

    // Number :
    typeof variable === 'number'

    // Boolean :
    typeof variable === 'boolean'

    // Object :
    typeof variable === 'object'

    // Array :
    Array.isArray(variable)

    // null :
    variable === null

    // undefined :
    typeof variable === 'undefined'

    // null or undefined or 0 :
    !variable

    // property exists :
    object.hasOwnProperty(property)
    ```

    B. Typecasting / Coerced Types

    ```javascript
    // string to number
    +'1'; // 1

    // to boolean
    !!variable;

    // to string
    '' + variable;

    ```
4. Conditional Evaluation

    ```javascript
    // When only evaluating that an array has length,
    // instead of this:
    if (array.length > 0) ...

    // ...evaluate truthiness, like this:
    if (array.length) ...

    // property check
    if (obj.prop && obj.prop === foo) {

    }

    // always always always use triple equals when evaluating equality
    1 === 1
    ```
5. Practical Style

    ```javascript
    // Just apply everything
    ```

6. Naming

    ```javascript
    // snake_case on variables including functions
    var foo_bar;
    ```
7. Misc

    ```javascript

    // Use built-in functions as much as possible

    // Use forEach to traverse an array
    // promotes readability
    array.forEach(function (element, index, array) {

    });

    // Use filter to filter array
    // promotes readability

    array = array.filter(function (element, index, array) {
        return element.property === bar;
    });

    // Use map to modify an array
    // promotes readability

    array = array.map(function (element, index, array) {
        element.created_at = new Date;
        delete element.foo;
        return element;
    });

    // chain forEach, filter, map if possible
    // promotes readability

    array
        .filter(function (element) {
            return element.count > 50;
        })
        .map(function (element) {
            element.count += 100;
            return element;
        })
        .forEach(function (element) {
            foo(element);
        });
    ```
