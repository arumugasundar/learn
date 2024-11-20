
# Interview - Intermediate

### Questions
1. [How to use the `map()` function on an array?](#1-how-to-use-the-map-function-on-an-array)
2. [How to create a promise in JavaScript?](#2-how-to-create-a-promise-in-javascript)
3. [Realtime example for a promise in JavaScript?](#3-realtime-example-for-a-promise-in-javascript)
4. [How does the `this` keyword work in JavaScript?](#4-how-does-the-this-keyword-work-in-javascript)
5. [What are arrow functions, and how are they different from regular functions?](#5-what-are-arrow-functions-and-how-are-they-different-from-regular-functions)
6. [How to perform destructuring of an object in JavaScript?](#6-how-to-perform-destructuring-of-an-object-in-javascript)
7. [How to use the `reduce()` function on an array?](#7-how-to-use-the-reduce-function-on-an-array)
8. [How to set a timeout to delay execution in JavaScript?](#8-how-to-set-a-timeout-to-delay-execution-in-javascript)
9. [How to use the rest and spread operators in JavaScript?](#9-how-to-use-the-rest-and-spread-operators-in-javascript)
10. [Explain hoisting in JavaScript?](#10-explain-hoisting-in-javascript)

#### 1. How to use the `map()` function on an array?
- `map()` function in JavaScript is used to transform elements of an array and create a new array
- It applies a given callback function to each element of the original array and returns a new array with the transformed elements
- The original array is not modified
- **Syntax**
    ```code
    array.map(callback(element, index, array), thisArg);
    ```
    - **callback** - A function that is called for each element in the array. It takes the following arguments
        - **element** - The current element being processed
        - **index** (optional) - The index of the current element
        - **array** (optional) - The original array being traversed
    - **thisArg (optional)** - A value to use as `this` when executing the callback
- **Examples**
    - **Basic Example** - Transform an array of numbers by multiplying each number by 2

        ```code
        const numbers = [1, 2, 3, 4];
        const doubled = numbers.map(num => num * 2);

        console.log(doubled); // Output: [2, 4, 6, 8]
        ```

    - **Using Index** - Include the index of each element in the transformation

        ```code
        const numbers = [10, 20, 30];
        const result = numbers.map((num, index) => `Index ${index}: ${num}`);

        console.log(result);
        // Output: ["Index 0: 10", "Index 1: 20", "Index 2: 30"]
        ```
    
    - **With Objects** - Extract a specific property from an array of objects

        ```code
        const users = [
            { name: 'Alice', age: 25 },
            { name: 'Bob', age: 30 },
            { name: 'Charlie', age: 35 },
        ];

        const names = users.map(user => user.name);

        console.log(names); // Output: ["Alice", "Bob", "Charlie"]
        ```
    
    - **Chaining with Other Methods** - `map()` with other array methods like `filter()`

        ```code
            const numbers = [1, 2, 3, 4, 5];
            const doubledEvenNumbers = numbers
            .filter(num => num % 2 === 0) // Filter even numbers
            .map(num => num * 2); // Double them

            console.log(doubledEvenNumbers); // Output: [4, 8]
        ```
    
    - **Points to Remember**
        - `map()` does not mutate the original array; it returns a new array
        - Always return a value in the callback function, as `undefined` will be used if nothing is returned
        - It's often used for transformations, not for filtering or reducing, which have their own methods (`filter()` and `reduce()`)

#### 2. How to create a promise in JavaScript?
- A promise in JavaScript is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value
- To create a promise, you use the `Promise` constructor, passing a function (called the executor function) as an argument
- The executor function takes two arguments: `resolve` and `reject`
- **Syntax**

    ```code
    const promise = new Promise((resolve, reject) => {
        // asynchronous operation
        if (/* operation is successful */) {
            resolve(value); // when the operation is successful
        } else {
            reject(error); // when the operation fails
        }
    ```

- **Examples**
    - **Basic Promise**

    ```code
    const myPromise = new Promise((resolve, reject) => {
        let success = true; // Simulating an operation
        if (success) {
            resolve("Operation successful!");
        } else {
            reject("Operation failed.");
        }
    });

    // Handling the promise
    myPromise
    .then(result => {
        console.log(result); // Output: "Operation successful!"
    })
    .catch(error => {
        console.error(error); // This won't run because success is true
    });
    ```

    - **Simulating an Asynchronous Operation** - Simulate a delay with setTimeout to mimic an async task

    ```code
    const delayedPromise = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Task completed after 2 seconds.");
        }, 2000);
    });

    // Handling the promise
    delayedPromise
    .then(message => {
        console.log(message); // Output: "Task completed after 2 seconds."
    })
    .catch(error => {
        console.error(error);
    });
    ```

    - **Rejecting a Promise**

    ```code
    const errorPromise = new Promise((resolve, reject) => {
        let errorOccurred = true; // Simulating an error
        if (errorOccurred) {
            reject("Something went wrong!");
        } else {
            resolve("Everything is fine!");
        }
    });

    // Handling the promise
    errorPromise
    .then(result => {
        console.log(result);
    })
    .catch(error => {
        console.error(error); // Output: "Something went wrong!"
    });
    ```

    - **Using Promises in a Function** - Wrap an asynchronous operation in a promise for reuse

    ```code
    function fetchData() {
        return new Promise((resolve, reject) => {
            const success = true; // Simulated operation status
            setTimeout(() => {
            if (success) {
                resolve("Data fetched successfully!");
            } else {
                reject("Failed to fetch data.");
            }
            }, 1500);
        });
    }

    fetchData()
    .then(data => {
        console.log(data); // Output: "Data fetched successfully!"
    })
    .catch(error => {
        console.error(error);
    });
    ```

    - **Key Points**
        - A promise has three states
            - **Pending** - Initial state, neither fulfilled nor rejected
            - **Fulfilled** - The operation was completed successfully
            - **Rejected** - The operation failed
        - Use `resolve(value)` to fulfill a promise and `reject(error)` to reject it
        - Use `.then()` for handling resolved values and `.catch()` for handling error
        - Use `.finally()` for cleanup tasks that should run regardless of the promise's outcome


#### 3. Realtime example for a promise in JavaScript?

```code
// Define a function that fetches data
function fetchUserData() {
  return new Promise((resolve, reject) => {
    fetch('https://jsonplaceholder.typicode.com/users') // API call
      .then(response => {
        if (!response.ok) {
          // Handle HTTP errors
          reject(`Error: ${response.status} - ${response.statusText}`);
        }
        return response.json(); // Parse JSON if successful
      })
      .then(data => resolve(data)) // Pass parsed data to resolve
      .catch(error => reject(`Fetch failed: ${error.message}`)); // Handle fetch errors
  });
}

// Call the function and handle the promise
fetchUserData()
  .then(users => {
    console.log("User data fetched successfully:", users); // Process the data
  })
  .catch(error => {
    console.error("Error fetching user data:", error); // Handle errors
  });
```

 - **Enhancements: Asynchronous Functions**
    - Modern JavaScript allows you to simplify this with `async`/`await`
    - This approach is simpler and more readable, but it still uses promises under the hood!

    ```code
    async function fetchUserData() {
        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/users');
            if (!response.ok) {
            throw new Error(`HTTP error: ${response.status} - ${response.statusText}`);
            }
            const users = await response.json();
            console.log("User data fetched successfully:", users);
        } catch (error) {
            console.error("Error fetching user data:", error);
        }
    }

    fetchUserData();
    ```


#### 4. How does the `this` keyword work in JavaScript?
- The `this` keyword in JavaScript refers to the object it belongs to
- Its value is determined dynamically, based on the execution context (how and where it is used)
- Understanding how `this` behaves in different contexts is crucial
- **Key Rules for `this`**
    - **Global Context (Non-Strict Mode)**
        - In the global context or in a simple function call, this refers to the global object (window in browsers or global in Node.js)

        ```code
        console.log(this); // In a browser, this points to the global window object
        function showThis() {
        console.log(this);
        }
        showThis(); // window (global object in non-strict mode)
        ```
    
    - **Global Context (Strict Mode)**
        - In strict mode (`'use strict';`), this in a function defaults to `undefined`

        ```code
        'use strict';
        function showThis() {
            console.log(this);
        }
        showThis(); // undefined
        ```

    - **Inside an Object Method**
        - When a function is called as a method of an object, `this` refers to the object that owns the method

        ```code
        const person = {
            name: 'Alice',
            greet() {
                console.log(this.name);
            },
        };
        person.greet(); // 'Alice'
        ```

    - **Arrow Functions**
        - Arrow functions do not have their own `this`. Instead, they inherit `this` from the surrounding lexical context

        ```code
        const person = {
            name: 'Alice',
            greet: () => {
                console.log(this.name);
            },
        };
        person.greet(); // undefined, as `this` refers to the global object

        const obj = {
            outerFunction() {
                const innerArrowFunction = () => {
                console.log(this); // Inherits `this` from `outerFunction`
                };
                innerArrowFunction();
            },
        };

        obj.outerFunction(); // `this` refers to `obj`
        ```

    - **In a Constructor Function or Class**
        - When used in a constructor function or class, `this` refers to the newly created instance

        ```code
        function Person(name) {
            this.name = name;
        }
        const alice = new Person('Alice');
        console.log(alice.name); // 'Alice'

        class Animal {
            constructor(type) {
                this.type = type;
            }
        }

        const cat = new Animal('Cat');
        console.log(cat.type); // 'Cat'
        ```
    
    - **Event Listeners**
        - In event listeners, `this` refers to the element that triggered the event

        ```code
        const button = document.querySelector('button');
        button.addEventListener('click', function () {
            console.log(this); // The button element
        });
        ```

    - **Explicit Binding**
        - It can be explicitly set the value of `this` using `.call()`, `.apply()`, or `.bind()`

        ```code
        function showName() {
            console.log(this.name);
        }
        const user = { name: 'Alice' };

        showName.call(user); // 'Alice'
        showName.apply(user); // 'Alice'

        const boundFunction = showName.bind(user);
        boundFunction(); // 'Alice'
        ```

- **Common Scenarios and Gotchas**
    - **Losing Context** - If a method is extracted from an object and called independently, this may lose its reference to the original object

        ```code
        const person = {
            name: 'Alice',
            greet() {
                console.log(this.name);
            },
        };

        const greetFunction = person.greet;
        greetFunction(); // undefined (or error in strict mode)
        ```

    - **Fixing Context** - Use .bind() to permanently bind this to a specific value

        ```code
        const greetBound = person.greet.bind(person);
        greetBound(); // 'Alice'
        ```

- **Summary of `this` in Different Contexts**

    | Context | `this` Value |
    |:-------:|:------------:|
    | Global (non-strict mode) | Global object (window or global) |
    | Global (strict mode) | undefined |
    | Object method | Object that owns the method |
    | Arrow function | Lexical `this` (inherits from parent scope) |
    | Constructor function / Class | Newly created object |
    | Event listener | Element that triggered the event |
    | Explicit binding | Value provided by `.call()`, `.apply()`, `.bind()` | 


#### 5. What are arrow functions, and how are they different from regular functions?
- Arrow functions in JavaScript are a more concise syntax for writing functions, introduced in ES6.
- They are often used for shorter, cleaner function expressions and have some key differences compared to regular functions, particularly regarding how they handle the this keyword
- **Syntax**
    - **Arrow Function**

        ```code
        const add = (a, b) => a + b;
        ```

    - **Equivalent Regular Function**

        ```code
        function add(a, b) {
            return a + b;
        }
        ```

- **Features**
    - **Concise Syntax** - Single-line return is implicit; no need for {} or return

        ```code
        const square = x => x * x; // Implicit return
        ```
    - **No `this` Binding** - Arrow functions do not have their own `this`. Instead, they inherit `this` from the surrounding (lexical) scope

        ```code
        const obj = {
            value: 10,
            regularFunction: function() {
                console.log(this.value); // Refers to obj
            },
            arrowFunction: () => {
                console.log(this.value); // Refers to outer scope, not obj
            }
        };

        obj.regularFunction(); // 10
        obj.arrowFunction(); // undefined (or global object value in non-strict mode)
        ```

    - **No `arguments` Object**
        - Arrow functions do not have their own `arguments` object. Use rest parameters (`...args`) if needed

            ```code
            function regularFunction() {
                console.log(arguments); // Arguments object available
            }

            const arrowFunction = () => {
                console.log(arguments); // ReferenceError: arguments is not defined
            };

            regularFunction(1, 2, 3);
            arrowFunction(1, 2, 3); // Error
            ```
    
    - **Cannot Be Used as Constructors**
        - Arrow functions cannot be used with `new` because they lack a `prototype` property

            ```code
            const ArrowConstructor = () => {};
            const obj = new ArrowConstructor(); // TypeError: ArrowConstructor is not a constructor
            ```
    
    - **Always Anonymous**
        - Arrow functions are always anonymous. If you assign them to a variable, the variable name becomes the function name

- **Key Differences: Regular Functions vs. Arrow Functions**

    | Feature | Regular Function | Arrow Function |
    |:-------:|:----------------:|:--------------:|
    | Syntax | Longer | Concise |
    | `this` Context | Dynamically determined | Lexically inherited |
    | `arguments` Object | Available | Not available |
    | Constructors | Can be used as constructors | Cannot be used as constructors |
    | Prototype Property | Has `prototype` | Does not have `prototype` |
    | Implicit Return | Must use `return` for output | Implicit return for single-line |


#### 6. How to perform destructuring of an object in JavaScript?
- Destructuring allows you to extract properties from an object and assign them to variables in a concise way. 
- Powerful feature introduced in ES6.
- **Basic Syntax**
    ```code
    const { property1, property2 } = object
    ```
- **Example**
    - **Simple Destructuring**

        ```code
        const person = { name: 'Alice', age: 25, city: 'New York' };

        // Destructure the object
        const { name, age } = person;

        console.log(name); // 'Alice'
        console.log(age);  // 25
        ```

    - **Renaming Variables** - rename variables while destructuring by using : after the property name
        
        ```code
        const person = { name: 'Alice', age: 25 };

        // Rename `name` to `fullName`
        const { name: fullName } = person;

        console.log(fullName); // 'Alice'
        ```

    - **Default Values** - If the property does not exist in the object, default value can be setted

        ```code
        const person = { name: 'Alice' };

        // `age` is not in the object, so it defaults to 18
        const { name, age = 18 } = person;

        console.log(name); // 'Alice'
        console.log(age);  // 18
        ```
    
    - **Nested Object Destructuring** - For objects within objects, nested properties can be destructured

        ```code
        const person = {
            name: 'Alice',
            address: {
                city: 'New York',
                zip: 10001,
            },
        };

        // Destructure `city` and `zip` from `address`
        const { address: { city, zip } } = person;

        console.log(city); // 'New York'
        console.log(zip);  // 10001
        ```
    
    - **Rest Properties** - Use the rest operator (...) to collect remaining properties into a new object

        ```code
        const person = { name: 'Alice', age: 25, city: 'New York' };

        // Extract `name`, collect the rest
        const { name, ...rest } = person;

        console.log(name); // 'Alice'
        console.log(rest); // { age: 25, city: 'New York' }
        ```
    
    - **Using Destructuring in Functions** - Object destructuring is often used in function parameters to extract specific properties

        ```code
        function greet({ name, age }) {
            console.log(`Hello, ${name}. You are ${age} years old.`);
        }

        const person = { name: 'Alice', age: 25 };
        greet(person); // "Hello, Alice. You are 25 years old."
        ```
    
    - **Combining with Arrays** - object destructuring can be combined with arrays for more complex structures

        ```code
        const data = {
            users: [
                { id: 1, name: 'Alice' },
                { id: 2, name: 'Bob' },
            ],
        };

        // Extract the first user's name
        const { users: [{ name: firstName }] } = data;

        console.log(firstName); // 'Alice'
        ```
- **Common Use Cases**
    - Extracting API Response Data
    - Setting Component Props in React
- **Things to Remember**
    - **Property names must match** - The variable names must match the property names in the object unless its renamed
    - **Default values work only for `undefined`** - They don’t apply if the property is explicitly set to null or other falsy values
    - **Rest operator gathers remaining properties** - Useful for handling objects with many properties dynamically


#### 7. How to use the `reduce()` function on an array?
- A powerful method used to iterate through an array and reduce it to a single value 
- e.g., a sum, product, or even a new object or array
- **Syntax**

    ```code
    array.reduce(callback, initialValue);
    ```
    - **`callback`** - A function executed on each element in the array
        - It takes four arguments
        - `accumulator` - The accumulated result from previous iterations.
        - `currentValue` - The current element being processed.
        - `currentIndex (Optional)` - The index of the current element.
        - `array (Optional)` - The array being traversed.
    - `initialValue (Optional)` - An initial value for the accumulator
        - If omitted, the first element of the array is used as the initial value, and iteration starts from the second element
- **Examples**
    - **Sum of Array Elements**

        ```code
        const numbers = [1, 2, 3, 4, 5];

        const sum = numbers.reduce((accumulator, currentValue) => {
        return accumulator + currentValue;
        }, 0); // Initial value is 0

        console.log(sum); // Output: 15
        ```

    - **Find Maximum Value**

        ```code
        const numbers = [10, 25, 5, 30, 15];

        const max = numbers.reduce((accumulator, currentValue) => {
        return currentValue > accumulator ? currentValue : accumulator;
        });

        console.log(max); // Output: 30
        ```

    - **Group Items by Property**

        ```code
        const people = [
            { name: 'Alice', age: 30 },
            { name: 'Bob', age: 25 },
            { name: 'Charlie', age: 30 },
        ];

        const groupedByAge = people.reduce((accumulator, person) => {
        const { age } = person;
        if (!accumulator[age]) {
            accumulator[age] = [];
        }
        accumulator[age].push(person);
        return accumulator;
        }, {});

        console.log(groupedByAge);
        // Output:
        // {
        //   30: [{ name: 'Alice', age: 30 }, { name: 'Charlie', age: 30 }],
        //   25: [{ name: 'Bob', age: 25 }]
        // }
        ```

    - **Flatten an Array**

        ```code
        const arrays = [[1, 2], [3, 4], [5, 6]];

        const flattened = arrays.reduce((accumulator, currentValue) => {
            return accumulator.concat(currentValue);
        }, []);

        console.log(flattened); // Output: [1, 2, 3, 4, 5, 6]
        ```

    - **Count Occurrences of Items**

        ```code
        const fruits = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];

        const fruitCounts = fruits.reduce((accumulator, fruit) => {
            accumulator[fruit] = (accumulator[fruit] || 0) + 1;
            return accumulator;
        }, {});

        console.log(fruitCounts);
        // Output: { apple: 3, banana: 2, orange: 1 }
        ```

    - **Build a New Object**

        ```code
        const entries = [
            ['name', 'Alice'],
            ['age', 30],
            ['city', 'New York'],
        ];

        const obj = entries.reduce((accumulator, [key, value]) => {
            accumulator[key] = value;
            return accumulator;
        }, {});

        console.log(obj);
        // Output: { name: 'Alice', age: 30, city: 'New York' }
        ```

    - **Chaining with Other Methods**

        ```code
        const numbers = [1, 2, 3, 4, 5];

        // Sum of squares
        const sumOfSquares = numbers
        .map(num => num ** 2) // Square each number
        .reduce((accumulator, currentValue) => accumulator + currentValue, 0);

        console.log(sumOfSquares); // Output: 55
        ```

- **Key Points**
 - **Initial Value** - Always set an initialValue if your array might be empty to avoid errors.
 - **Immutable Operations** - `reduce()` doesn’t mutate the original array.
 - **Versatility** - It can be used for a wide variety of operations, from arithmetic to object manipulation.
 - **Performance** - Be cautious when working with large arrays, as `reduce()` involves iteration over all elements.


#### 8. How to set a timeout to delay execution in JavaScript?
- `setTimeout()` function to delay the execution of a piece of code
- **Syntax**
    ```code
    setTimeout(callback, delay, arg1, arg2, ...);
    ```
    - `callback` - The function to execute after the delay.
    - `delay` - Time in milliseconds to wait before executing the function.
    - `arg1, arg2, ... (Optional)` - Arguments to pass to the callback function
- **Examples**
    - **Basic Usage**

        ```code
        setTimeout(() => {
            console.log('This message is displayed after 2 seconds.');
        }, 2000);
        ```

    - **Using a Named Function**

        ```code
        function greet(name) {
            console.log(`Hello, ${name}!`);
        }

        setTimeout(greet, 3000, 'Alice');
        // Output after 3 seconds: Hello, Alice!
        ```
    
    - **Clearing a Timeout**

        ```code
        const timeoutId = setTimeout(() => {
            console.log('This will not be executed');
        }, 5000);

        clearTimeout(timeoutId); // Cancels the timeout
        ```

    - **Chaining with Other Code**

        ```code
        console.log('Start');
        setTimeout(() => {
            console.log('Delayed Message');
        }, 1000);
        console.log('End');

        // Output:
        // Start
        // End
        // Delayed Message
        ```
- **Practical Applications**
    - **Simulating a Loading Message**

        ```code
        console.log('Loading...');
        setTimeout(() => {
            console.log('Loaded!');
        }, 2000);
        ```
    
    - **Repeating with Recursion** -  `setInterval` can be simulated using `setTimeout` recursively

        ```code
        function repeatMessage() {
            console.log('Hello, again!');
            setTimeout(repeatMessage, 1000);
        }

        repeatMessage();
        ```
- **Tips**
    - **Delay Resolution** - The delay is not guaranteed to be precise due to JavaScript's event loop and other asynchronous tasks
    - **Zero Delay** - Using `setTimeout(callback, 0)` queues the callback to execute as soon as possible after the current script finishes
    - **Avoid Long Delays** - For very long delays, `setTimeout` might not be reliable due to browser constraints or system limitations.

#### 9. How to use the rest and spread operators in JavaScript?
- The rest (`...`) and spread (`...`) operators in JavaScript are versatile tools for handling arrays, objects, and function arguments more efficiently. 
- Both use the same syntax (`...`), but their purposes differ

- **Rest Operator**
    - The rest operator collects multiple elements into a single array or object
    - It's used to handle function arguments or destructure objects and arrays
    - **Syntax**

        ```code
        function func(...rest) { }
        const [a, ...rest] = array;
        const { a, ...rest } = object;
        ```

- **Spread Operator**
    - The spread operator spreads (or unpacks) elements of an array or object into individual elements
    - It's used to clone, merge, or pass array elements or object properties
    - **Syntax**
    
        ```code
        const arr = [...array];
        const obj = { ...object };
        ```

- **Combining Rest and Spread**

    ```code
    function greet(greeting, ...names) {
        return `${greeting} ${names.join(', ')}`;
    }

    const people = ['Alice', 'Bob', 'Charlie'];
    console.log(greet('Hello', ...people));
    // Output: Hello Alice, Bob, Charlie
    ```

- **Tips**
    - **Rest in Functions** - Always appears last in the parameter list
    - **Spread on Immutable Data** - Use `...` to safely copy objects or arrays to avoid mutating the original data

#### 10. Explain hoisting in JavaScript?
- Hoisting is a JavaScript mechanism where variable and function declarations are moved (or "hoisted") to the top of their containing scope during the compile phase
- This means variables and functions were usable before declaring them in the code
- However, only the declarations are hoisted—not the initializations
- This behavior can sometimes lead to unexpected results if not well understood
- **Key Points about Hoisting**
    - Functions and var-declared variables are hoisted.
    - Variables declared with let and const are also hoisted, but they remain in a temporal dead zone (TDZ) from the start of the block until the declaration is encountered.
- **Practical Use of Hoisting**
    - **Declaring Functions Anywhere** - Hoisting allows you to write your function declarations at the bottom of your code for better readability

        ```code
        printMessage();

        function printMessage() {
        console.log('This is hoisting!');
        }
        ```

    - **Avoiding Temporal Dead Zone** - To prevent hoisting issues, always declare let and const variables at the top of their scope

        ```code
        let x = 10;
        console.log(x); // Output: 10
        ```

