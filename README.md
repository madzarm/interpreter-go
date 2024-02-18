<h1>Monkey Interpreter</h1>

This is an interpreter for a 'Monkey' programming language written in <b><i>Go</i></b><br/>
I've created this based on the Thorsten Ball's book on writing interpreters.<br/>

in order to use the interpreter, locate and move into the root folder and run:
    
    go run .\main\main.go

<h2>Features</h2>
<li>C-like syntax</li>
<li>variable bindings</li>
<li>integers and booleans</li>
<li>arithmetic expressions</li>
<li>first-class and higher-order functions</li>
<li>closures</li>

<h3>Value binding</h3>

    let age = 1
    let result = 10 * (20 / 2) + age
    let found = true

Besides integers and booleans, in Monkey, you can also bind functions to names:

    let add = fn(a, b) { return a + b }

Implicit return values are also possible which means we can leave out the _return_:

    let add = fn(a, b) { a + b }

Function calling works as expected:

    add(1, 2);

More complex functions can also be written:

    let fibonacci = fn(x) {
        if (x == 0) {
            0
        } else {
            if (x == 1) {
                1
            } else {
                fibonacci(x - 1) + fibonacci(x - 2);
            }
        }
    };

<h3>Higher order functions</h3>
Monkey also supports higher order functions. These are functions that take other functions as arguments:

    let twice = fn(f, x) {
        return f(f(x));
    };
    let addTwo = fn(x) {
        return x + 2;
    };
    twice(addTwo, 2); // => 6

Monkey has _first class functions_. That means functions in Monkey are just values, like integers or booleans.<br/>

<h3>Closures</h3>
Monkey also supports <b><i>closures</i></b>. Closure is a function that references variables from outside its body allowing
it to encapsulate state and behaviour within functions:

    let newAdder = fn(x) {
        fn(y) { x + y };
    };
    let addTwo = newAdder(3);
    addTwo(2); // => 5
