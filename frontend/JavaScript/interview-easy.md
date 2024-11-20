
# Interview - Easy

### Questions
1. [How to declare a variable in JavaScript?](#1-how-to-declare-a-variable-in-javascript)
2. [How to write a function in JavaScript?](#2-how-to-write-a-function-in-javascript)
3. [How to add an event listener to a button?](#3-how-to-add-an-event-listener-to-a-button)
4. [What is the difference between == and === in JavaScript?](#4-what-is-the-difference-between--and--in-javascript)
5. [How to select an element by its ID in JavaScript?](#5-how-to-select-an-element-by-its-id-in-javascript)
6. [How to check if an array includes a specific value in JavaScript?](#6-how-to-check-if-an-array-includes-a-specific-value-in-javascript)
7. [How to convert a string to an integer in JavaScript?](#7-how-to-convert-a-string-to-an-integer-in-javascript)
8. [How to iterate over an array in JavaScript?](#8-how-to-iterate-over-an-array-in-javascript)
9. [How to create a template string in JavaScript?](#9-how-to-create-a-template-string-in-javascript)
10. [Why var is not showing any errors while redeclaration but let does?](#10-why-var-is-not-showing-any-errors-while-redeclaration-but-let-does)
11. [How to split only the decimal part of a string format floating number?](#11-how-to-split-only-the-decimal-part-of-a-string-format-floating-number)

#### 1. How to declare a variable in JavaScript?

- **var**
    - **Scope** - Function-scoped
    - **Hoisting** - Variable declarations are hoisted, but their initialization is not
    - **Redeclaration** - Allowed in the same scope
    - **Reassignment** - Allowed in the same scope
    - **Usecase** - Rarely used in modern JavaScript due to potential scoping issues
- **let**
    - **Scope** - Block-scoped (within {})
    - **Hoisting** - Hoisted but not initialized (accessing before declaration throws an error)
    - **Redeclaration** - Not allowed in the same scope
    - **Reassignment** - Allowed in the same scope
    - **Usecase** - Use when needed to reassign values and want block-scoping
- **const**
    - **Scope** - Block-scoped (within {})
    - **Hoisting** - Hoisted but not initialized (accessing before declaration throws an error)
    - **Redeclaration** - Not allowed
    - **Reassignment** - Not allowed (creates immutable bindings, but object properties can still be modified)
    - **Usecase** - Use for values that should not change
- **Best Practices**
    - Prefer `const` for variables that don't change.
    - Use `let` for variables that need reassignment.
    - Avoid `var` in modern JavaScript unless working with older codebases
```code
function example() {
    if (true) {
        var x = 1;  // Function-scoped
        let y = 2;  // Block-scoped
        const z = 3; // Block-scoped
    }
    console.log(x); // Outputs: 1
    // console.log(y); // ReferenceError: y is not defined
    // console.log(z); // ReferenceError: z is not defined
}
example();
```

#### 2. How to write a function in JavaScript?
- **Function Declaration** - A named function that can be called anywhere after it's declared (due to hoisting)

    ```code
    function greet(name) {
        return `Hello, ${name}!`;
    }

    console.log(greet("Alice"));  // Outputs: Hello, Alice!
    ```
- **Function Expression** - A function assigned to a variable. This function is not hoisted and can only be called after its definition

    ```code
    const greet = function(name) {
        return `Hello, ${name}!`;
    };

    console.log(greet("Bob"));  // Outputs: Hello, Bob!
    ```
- **Arrow Function (ES6)** - A shorter syntax for writing functions, often used for callbacks or concise logic

    ```code
    const greet = (name) => `Hello, ${name}!`;

    console.log(greet("Charlie"));  // Outputs: Hello, Charlie!
    ```
    - Single Parameter - No need for parentheses around name.
    - Single Expression - No need for curly braces or return.
    - For multiple parameters or a block of code
    ```code
    const add = (a, b) => {
        const sum = a + b;
        return sum;
    };

    console.log(add(3, 5));  // Outputs: 8
    ```
-  **Immediately Invoked Function Expression (IIFE)** - A function executed immediately after it's defined

    ```code
    (function(name) {
        console.log(`Hello, ${name}!`);
    })("Daisy");
    // Outputs: Hello, Daisy!
    ```
- **Function with Default Parameters** - You can define default values for parameters

    ```code
    function greet(name = "Guest") {
        return `Hello, ${name}!`;
    }

    console.log(greet());  // Outputs: Hello, Guest!
    console.log(greet("Eve"));  // Outputs: Hello, Eve!
    ```
- **Function as a Method** - A function defined inside an object

    ```code
    const person = {
        name: "Alice",
        greet: function() {
            return `Hello, ${this.name}!`;
        },
    };

    console.log(person.greet());  // Outputs: Hello, Alice!
    ```
- **Using the Function Constructor (Rarely used)** - Defines a function dynamically. Not commonly used in modern JavaScript

    ```code
    const add = new Function("a", "b", "return a + b;");
    console.log(add(2, 3));  // Outputs: 5
    ```
- **Asynchronous Functions** - To work with async/await for asynchronous operations

    ```code
    const fetchData = async () => {
        const data = await fetch("https://api.example.com/data");
        return data.json();
    };

    fetchData().then((result) => console.log(result));
    ```
- **Best Practices**
    - Use arrow functions for shorter syntax, especially for callbacks
    - Use function declarations when a function needs to be hoisted
    - Use async/await for handling asynchronous code

#### 3. How to add an event listener to a button?

```code
<button id="myButton">Click Me!</button>

// Step 1: Select the button
const button = document.getElementById("myButton");

// Step 2: Add the event listener
button.addEventListener("click", () => {
    alert("Button clicked!");
});
```

#### 4. What is the difference between == and === in JavaScript?
- In JavaScript, `==` and `===` are comparison operators, but they differ in how they check equality
- **`==` (Equality Operator)**
    - Performs type coercion
    - Converts the operands to the same type before making the comparison
    - Can return `true` even if the types of the operands are different, as long as their values are "equal" after type conversion
    - Example

        ```code
        console.log(5 == "5"); // true, because "5" is coerced to a number before comparison
        console.log(true == 1); // true, because true is coerced to 1
        console.log(null == undefined); // true, because they are considered loosely equal
        ```
- **`===` (Strict Equality Operator)**
    - Does not perform type coercion
    - Compares both the value and the type of the operands
    - Returns `true` only if the operands are of the same type and have the same value
    - Example

        ```code
        console.log(5 === "5"); // false, because the types are different (number vs string)
        console.log(true === 1); // false, because the types are different (boolean vs number)
        console.log(null === undefined); // false, because their types are different
        ```
- **Key Takeaway**
    - Use `==` when you are okay with type conversion during comparison (rarely recommended for clarity and potential bugs)
    - Use `===` when you want to ensure strict type and value equality (best practice in most cases)

#### 5. How to select an element by its ID in JavaScript?
- To select an element by its ID in JavaScript, `document.getElementById()` method is used
- This method retrieves the first element in the DOM with the specified `id` attribute

    ```code
    <!DOCTYPE html>
    <html>
    <head>
    <title>Example</title>
    </head>
    <body>
    <h1 id="title">Hello, World!</h1>
    <script>
        // Select the element with ID "title"
        const titleElement = document.getElementById("title");

        // Manipulate the element
        console.log(titleElement.textContent); // Outputs: Hello, World!
        titleElement.style.color = "blue"; // Changes the text color to blue
    </script>
    </body>
    </html>
    ```
- **Note** 
    - **Case Sensitivity** - IDs are case-sensitive, so getElementById("Title") and getElementById("title") are different
    - **Uniqueness** - IDs in HTML are expected to be unique within the document. If there are multiple elements with the same ID, getElementById will return the first one it encounters
    - **Return Value** - It returns the element if found, otherwise `null`. Always check if the returned value is not `null` before trying to manipulate it

#### 6. How to check if an array includes a specific value in JavaScript?
- To check if a value is in the array, Array.prototype.includes() method
- It returns a boolean (`true` or `false`) based on the presence of element in search
- **Syntax**

    ```code
    array.includes(valueToFind[, fromIndex])
    // valueToFind - The value to search for in the array
    // fromIndex (optional) - The index at which to start the search. Defaults to 0
    ```
- **Example**

    ```code
    const fruits = ["apple", "banana", "cherry"];

    console.log(fruits.includes("banana")); // true
    console.log(fruits.includes("grape"));  // false

    const numbers = [1, 2, 3, 4, 5, 3];

    console.log(numbers.includes(3, 4)); // true, because 3 is found at index 5
    console.log(numbers.includes(3, 6)); // false, because there is no 3 at or after index 6

    const obj1 = { id: 1 };
    const obj2 = { id: 2 };
    const array = [obj1, obj2];

    console.log(array.includes({ id: 1 })); // false, different object reference
    console.log(array.includes(obj1));     // true, same object reference

    // for older environments that don't support `includes()`, `indexOf()` is used
    const fruits = ["apple", "banana", "cherry"];
    console.log(fruits.indexOf("banana") !== -1); // true
    console.log(fruits.indexOf("grape") !== -1);  // false
    ```
- **Notes**
    - `includes()` performs a strict equality comparison (`===`) when checking for the value
    - It works for primitive values and object references, but for objects, you must search for the exact reference

#### 7. How to convert a string to an integer in JavaScript?
- **Using `parseInt()`**
    - Parses a string and returns an integer
    - Handle strings that start with numbers and ignore `non-numeric` characters after the number
    - **Syntax**

        ```code
        parseInt(string, radix);
        string - the string to parse
        radix - The base (e.g., 10 for decimal, 16 for hexadecimal)
        ```
    - **Example**

        ```code
        const str = "123";
        console.log(parseInt(str)); // 123

        const strWithText = "123abc";
        console.log(parseInt(strWithText)); // 123 (stops parsing at the first non-numeric character)

        const hex = "0x1A";
        console.log(parseInt(hex, 16)); // 26 (interprets as hexadecimal)
        ```
- **Using `Number()`**
    - Converts a string to a number
    - If the string isn't a valid number, it returns `NaN`
    - **Example**

        ```code
        const str = "123";
        console.log(Number(str)); // 123

        const invalidStr = "123abc";
        console.log(Number(invalidStr)); // NaN (invalid conversion)
        ```
- **Using Unary `+` Operator**
    - Converts a string to a number
    - **Example**

        ```code
        const str = "123";
        console.log(+str); // 123

        const invalidStr = "123abc";
        console.log(+invalidStr); // NaN (invalid conversion)
        ```
- **Using `Math.floor()` or `Math.ceil()` (if needed for floats)**
    - If the string might contain a floating-point number but if only the integer part is needed means, `Math.floor()` or `Math.ceil()` with `parseFloat()` is used

    - **Example**
        ```code
        const floatStr = "123.45";
        console.log(Math.floor(parseFloat(floatStr))); // 123
        console.log(Math.ceil(parseFloat(floatStr)));  // 124
        ```
- **Notes**
    - Always validate or sanitize the input string to ensure it's suitable for conversion
    - If the string doesn't represent a valid number, the conversion methods will return `NaN`
    - Check for NaN can be done using `isNaN()`
    - **Example**

        ```code
        const str = "123";
        const num = parseInt(str);
        if (!isNaN(num)) {
        console.log("Valid integer:", num);
        } else {
        console.log("Invalid number");
        }
        ```

#### 8. How to iterate over an array in JavaScript?
- **`for` Loop**

    ```code
    const fruits = ["apple", "banana", "cherry"];

    for (let i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
    }
    ```
- **`for...of` Loop
    - A modern, cleaner way to iterate over array values.

    ```code
    const fruits = ["apple", "banana", "cherry"];

    for (const fruit of fruits) {
    console.log(fruit);
    }
    ```
- **`forEach` Method**
    - A functional approach that executes a provided function once for each array element

    ```code
    const fruits = ["apple", "banana", "cherry"];

    fruits.forEach((fruit, index) => {
    console.log(`${index}: ${fruit}`);
    });
    ```
    - **Pros** - Cleaner syntax for simple iterations
    - **Cons** - Cannot use break or continue
- **`map` Method**
    - Creates a new array by applying a function to each element

    ```code
    const fruits = ["apple", "banana", "cherry"];

    const uppercasedFruits = fruits.map(fruit => fruit.toUpperCase());
    console.log(uppercasedFruits); // ["APPLE", "BANANA", "CHERRY"]
    ```
    - **Usecase** - To transform elements into a new array
- **`filter` Method**
    - Filters the array based on a condition and returns a new array with elements that pass the condition

    ```code
    const numbers = [1, 2, 3, 4, 5];

    const evenNumbers = numbers.filter(number => number % 2 === 0);
    console.log(evenNumbers); // [2, 4]
    ```
- **`reduce` Method**
    - Reduces the array to a single value by applying a function to each element

        ```code
        const numbers = [1, 2, 3, 4, 5];

        const sum = numbers.reduce((accumulator, current) => accumulator + current, 0);
        console.log(sum); // 15
        ```
    - **usecase** - When needed to compute a single result from the array (e.g., sum, product)
- **`while` Loop**
    - Useful for more complex conditions or when you need greater control

        ```code
        const fruits = ["apple", "banana", "cherry"];
        let i = 0;

        while (i < fruits.length) {
        console.log(fruits[i]);
        i++;
        }
        ```
- **`do...while` Loop**
    - Executes the loop body at least once before checking the condition

        ```code
        const fruits = ["apple", "banana", "cherry"];
        let i = 0;

        do {
        console.log(fruits[i]);
        i++;
        } while (i < fruits.length);
        ```
- **Choosing the Right Method**
    - Use `for` or `while` loops when you need more control (e.g., breaking out of the loop)
    - Use `forEach` for simple side effects or actions
    - Use `map`, `filter`, or `reduce` when working with transformations or computations on arrays
    - Use `for...of` for clean, modern iteration over array values

#### 9. How to create a template string in JavaScript?
- Template strings (also called template literals) are created using backticks (`) instead of single (') or double (") quotes
- Provide enhanced features like multi-line strings, expression interpolation, and nesting
- **Syntax**

    ```code
    `string here`
    ```
- **Features**
    - **Expression Interpolation** - To embed expressions inside template strings using the `${expression}` syntax

        ```code
        const name = "Alice";
        const age = 25;

        const message = `Hello, my name is ${name} and I am ${age} years old.`;
        console.log(message);
        // Output: Hello, my name is Alice and I am 25 years old.
        ```
    - **Multi-line Strings** - To write strings across multiple lines without using escape characters

        ```code
        const multiLineString = `This is a multi-line string.
        It spans multiple lines.
        No need for \n characters!`;

        console.log(multiLineString);
        // Output:
        // This is a multi-line string.
        // It spans multiple lines.
        // No need for \n characters!
        ```
    - **Expression Nesting** - To include any valid JavaScript expressions, including function calls, arithmetic, and more

        ```code
        const a = 5;
        const b = 10;

        const result = `The sum of ${a} and ${b} is ${a + b}.`;
        console.log(result);
        // Output: The sum of 5 and 10 is 15.
        ```
    - **Tagged Templates (Advanced)** - a function (tag) to process a template string

        ```code
        function tag(strings, ...values) {
            console.log(strings); // Array of string literals
            console.log(values);  // Array of interpolated values
            return `Processed: ${strings.join("")}${values.join(", ")}`;
        }

        const name = "Bob";
        const age = 30;
        const taggedResult = tag`Name: ${name}, Age: ${age}`;
        console.log(taggedResult);
        // Output:
        // ["Name: ", ", Age: ", ""]
        // [ "Bob", 30 ]
        // Processed: Name: , Age: , Bob, 30
        ```
    - **When to use template strings**
        - Need to interpolate variables or expressions.
        - For multi-line strings to improve readability.
        - For embedding dynamic content in strings, such as generating HTML or logs

        ```code
        const user = { name: "Eve", role: "Admin" };
        const greeting = `Welcome ${user.name}! You have ${user.role} privileges.`;
        console.log(greeting);
        // Output: Welcome Eve! You have Admin privileges.
        ```


#### 10. Why var is not showing any errors while redeclaration but let does?
- `var` on redeclaration
    - `var` allows redeclaration of the same variable within the same scope

        ```code
        var a = 10;
        var a;
        console.log(a);
        ```
    - The second `var a;` is essentially ignored because the variable `a` is already declared
    - It doesn't redeclare or reinitialize `a`. Therefore, the value remains `10`
- `let` on redeclaration
    - Variables declared with let cannot be redeclared within the same scope
    - An attempt to redeclare a variable declared with let, JavaScript throws a SyntaxError

        ```code
        let a = 10;
        let a; // SyntaxError: Identifier 'a' has already been declared
        ```
- **Reason**
    - `var` is function-scoped and subject to hoisting, meaning its declarations are moved to the top of the function or global scope at runtime. However, its value assignment happens in place.
    - `let` is block-scoped and doesn't allow redeclaration, making it safer and helping avoid bugs caused by accidental overwrites.
- **Takeaway**
    - Use `let` or `const` for block scoping and better variable management.
    - Avoid `var` in modern JavaScript to reduce confusion and potential bugs.

#### 11. How to split only the decimal part of a string format floating number?
```code
function getDecimalPart(numberString) {
  // Split the number by the decimal point
  const parts = numberString.split(".");

  // Check if there's a decimal part and return it, otherwise return an empty string
  return parts.length > 1 ? parts[1] : "";
}

// Example usage
const num1 = "123.456";
const num2 = "789.00";
const num3 = "42";

console.log(getDecimalPart(num1)); // "456"
console.log(getDecimalPart(num2)); // "00"
console.log(getDecimalPart(num3)); // "" (no decimal part)
```