# JavaScript Convention

All code in any code-base should look like a single person cided it, no matter how many people contributed.
Source codes should be like a book, understandable by reading from top to bottom.
Choose readability over performance in most cases.

Sublime plugin for checking code quality:
- [JSHint Gutter](https://github.com/victorporof/Sublime-JSHint)
> Use `.jshintrc` provided in this repository

Sublime plugin for formatting code:
- [HTML-CSS-JS Prettify](https://github.com/victorporof/Sublime-HTMLPrettify)
> To be honest, self-discipline in coding should be enough. This doesn't produce the prettiest code. There are still plenty of ways to present the code in a better manner.

## DRY Principle

[Don't Repeat Yourself](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

## Manifesto

1. Soft Indents (4 spaces)
2. Beautiful Syntax

    A. Parentheses, Spacing, Braces, Linebreaks

    ```javascript
    /*
        if/else/for/while/try always have braces and span multiple lines
    */

    // Bad
    if (condition)
        dothis();

    // Good
    if (condition) {
        dothis();
    }
    ```

    ```javascript
    /*
        Insert spaces between reserved words and (), {} and operators
    */

    // Bad
    for(i=0;i<len;i+=1){

    }

    // Good
    for (i = 0; i < len; i += 1) {

    }
    ```

    ```javascript
    /*
        If the code block contains a lot of statements, apply proper linebreaks
    */

    // Bad
    if (condition) {
        my_var = my_object.do_something(in_this, and_this);
        my_second_var = your_object.thing.do_things(my_var);
        if (another_condition) {
            third_var = something();
        }
    }

    // Good
    if (condition) {

        my_var = my_object.do_something(in_this, and_this);
        my_second_var = your_object.thing.do_things(my_var);

        if (another_condition) {
            third_var = something();
        }
    }

    ```

    B. Assignments, Declarations, Functions ( Named, Expression, Constructor )

    ```javascript
    /*
        Use only one `var` per function
        Variable declaration should always the first statement
        It's like listing ingredients before you cook
    */
    // Bad
    var fn = function () {
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
    /*
        Declare initialized non-function variables first
        Followed by uninitialized non-function variables
        Followed by functions
        Sorting lines by character length can also add more readability
        If there are a lot of variables, group them by linebreaks
    */

    // Bad
    var do = function () {

        },
        my_thing,
        my_third_thing,
        my_second_thing,
        thing = '';

    // Good
    var thing = '',

        my_second_thing,
        my_third_thing,
        my_thing,

        do = function () {

        };
    ```

    ```javascript
    /*
        Create functions by assigning it to a variable
        This way, we only have one way of declaring things
    */

    // not really Bad
    function foo () {

    }

    // Good
    var foo = function () {

    };
    ```

    C. Consistency Always Win

    ```javascript
    /*
        Notice the spaces in the following snippets
    */

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
            prop1: value,
            prop2: value2
        };

    if (foo === bar) {

    }

    var foo = 1 + (1 * 2);
    ```

    D. Quotes

    ```javascript
    /*
        Single quotes on strings
    */
    var foo = 'string';
    ```

    E. End of Lines and End of File

    ```javascript
    // Always trim trailing spaces

    var a = 1;

    // There should not be anymore character after the semi-colon
    // Put an empty line before end of file
    ```

    F. Forming and accessing objects and arrays

    ```javascript
    /*
        When forming an object, don't put quotes on the property unless needed 
    */

    // Bad
    var obj = {
        'prop1': 'value',
        'prop2': 'value2'
    };

    // Good
    var obj = {
        prop1: 'value',
        prop2: 'value2',
        'special-property': 'value3'
    };
    ```

    ```javascript
    /*
        Always always always access properties using dot notation unless not allowed
    */

    // Bad
    obj['prop'] = 'new_value';

    // Good
    obj.prop = 'new_value';
    obj['special-property'] = 'new_value';
    ```

    ```javascript
    /*
        When forming an array, just try to have a good alignment
    */

    // Bad
    var obj = ['something', 'something_again'];

    // Good
    var obj = [
        'something',
        'something_again'
    ];
    ```

    ```javascript

    /*
        Make the object/array a one-liner if there's only 1 property/element
        and the value is not that long
    */

    // Bad
    var obj = {
        prop1 : 'value1'
    };

    var array = [
        'something'
    ];

    // Good
    var obj = {prop1: 'value1'};

    var array = ['something'];
    ```
    
    G. Ternary operators
    
    ```javascript

    // on a normal condition

    temp = condition
        ? value
        : value2;
        
        
    // on variable declaration:
    
    var temp = condition
            ? value
            : value2,
        temp2 = null,
        more_variables..
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

    // null or undefined or 0 or '':
    !variable

    // property exists :
    object.hasOwnProperty(property)
    ```

    B. Typecasting / Coerced Types

    ```javascript
    // string to number
    +'1'; // 1
    // or
    parseInt('1'); // 1

    // to boolean
    !!variable;

    // to string
    '' + variable;
    // or
    variable.toString();

    ```
4. Conditional Evaluation

    ```javascript
    // When evaluating if an array has elements,
    // instead of this:
    if (array.length > 0) {

    // ...evaluate truthiness, like this:
    if (array.length) {

    // property check
    if (obj.prop && obj.prop === foo) {

    }

    // always always always use triple equals when evaluating equality
    1 === 1
    ```

5. Naming

    ```javascript
    /*
        snake_case on variables including functions
    */
    var foo_bar;
    ```

6. Misc

    ```javascript
    /*
        If the function has a lot of arguments,
        try adding line breaks to make it more readable
    */

    // Bad
    do_this(this_one, plus_this_one, true, [this_also, this_also2]);

    // Good
    do_this(
        this_one,
        plus_this_one,
        true,
        [this_also, this_also2]
    );
    ```

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

    // If lodash is available, use its full potential

