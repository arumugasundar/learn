
# Interview - Hard

### Questions
1. [How to debounce a function in JavaScript?](#)
2. [What are closures, and how are they used in JavaScript?](#)
3. [How to use the async/await syntax to handle asynchronous operations?](#)
4. [What is the purpose of modules in JavaScript, and how to export/import them?](#)
5. [How to implement a deep clone of an object in JavaScript?](#)
6. [How to implement a custom iterator in JavaScript?](#)
7. [What is the event loop, and how does it work in JavaScript?](#)
8. [How to use Object.defineProperty() to define a property?](#)
9. [What is the purpose of the Reflect API in JavaScript?](#)
10. [How to create a proxy object in JavaScript?](#)

#### 1. How do you debounce a function in JavaScript?
- A technique to limit how often a function is executed
- It ensures that the function is called only after a specified period of inactivity
- **Syntax**

    ```code
    function debounce(func, delay) {
        let timeout;
        return function (...args) {
            const context = this;
            clearTimeout(timeout);
            timeout = setTimeout(() => func.apply(context, args), delay);
        };
    }
    ```

    - **func** - The function to debounce
    - **delay** - The number of milliseconds to wait after the last invocation
    - **timeout** - A variable to store the reference to the timeout
    - **clearTimeout(timeout)** - Clears any existing timeout to reset the debounce delay
    - **setTimeout** - Schedules the function execution after the specified delay
    - **apply(context, args)** - Ensures the function is executed in the correct context (this) with the provided arguments
- **Example** - debounce can be used in a search function to reduce API calls while a user types in a search box

    ```code
    // default debounce
    const search = debounce((query) => {
        console.log(`Searching for: ${query}`);
    }, 300);

    document.getElementById("searchInput").addEventListener("input", (e) => {
        search(e.target.value);
    });

    // debounce from lodash
    import _ from "lodash";

    const search = _.debounce((query) => {
        console.log(`Searching for: ${query}`);
    }, 300);

    document.getElementById("searchInput").addEventListener("input", (e) => {
        search(e.target.value);
    });
    ```
- **Key Benefits**
    - Reduces unnecessary calls or computations, improving performance
    - Useful in scenarios like API calls, window resizing, or button click handlers

#### 2. What are closures, and how are they used in JavaScript?
- A feature where a function "remembers" and continues to access variables from its lexical scope, even after the function has finished executing and the outer scope is no longer active.
- **Key Characteristics of Closures**
    - **Lexical Scope** - Functions can access variables defined in their outer (parent) scope.
    - **Persistence** - The inner function retains access to the outer scope variables even after the outer function has executed.
    - **Encapsulation** - Closures allows to create private variables, which can't be accessed directly from outside the function.
- **How Closures Work**

    ```code
    function outerFunction(outerVariable) {
        return function innerFunction(innerVariable) {
            console.log(`Outer Variable: ${outerVariable}`);
            console.log(`Inner Variable: ${innerVariable}`);
        };
    }

    const closureFunction = outerFunction("outside"); // Creates a closure
    closureFunction("inside");
    ```

    - When `outerFunction` is called, it creates and returns `innerFunction`
    - `innerFunction` is returned and assigned to `closureFunction`
    - Even though outerFunction has finished executing, `innerFunction` retains access to `outerVariable` due to the closure.
    - **Output**
        ```code
        Outer Variable: outside
        Inner Variable: inside
        ```
- **Use Cases of Closures**
    - **Data Privacy** - Closures are often used to create private variables.

        ```code
        function counter() {
            let count = 0; // Private variable
            return {
                increment: function () {
                count++;
                return count;
                },
                decrement: function () {
                count--;
                return count;
                },
            };
        }

        const myCounter = counter();
        console.log(myCounter.increment()); // 1
        console.log(myCounter.increment()); // 2
        console.log(myCounter.decrement()); // 1
        ```
        - Here, count is not accessible directly but can be modified using the increment and decrement methods.
        
    - **Callbacks** - Closures are commonly used in asynchronous code with callbacks.

        ```code
        function fetchData(url) {
        const cachedUrl = url; // Closure variable
        setTimeout(() => {
            console.log(`Fetching data from ${cachedUrl}`);
        }, 2000);
        }

        fetchData("https://api.example.com");
        ```
    
    - **Function Factories** - Closures can be used to create functions dynamically.

        ```code
        function createMultiplier(multiplier) {
            return function (value) {
                return value * multiplier;
            };
        }

        const double = createMultiplier(2);
        const triple = createMultiplier(3);

        console.log(double(5)); // 10
        console.log(triple(5)); // 15
        ```
    
    - **Event Listeners** - Closures ensure the handler function has access to the scope it was defined in
    
        ```code
        function addEventHandlers() {
            for (let i = 0; i < 3; i++) {
                document.getElementById(`button${i}`).addEventListener("click", () => {
                console.log(`Button ${i} clicked`);
                });
            }
        }
        addEventHandlers();
        ```
    
    - **Key Points to Remember**
        - **Closures can cause memory leaks** - If a closure retains references to unnecessary variables, it can increase memory usage.
        - **Use closures carefully** - While powerful, they can introduce complexity if overused.
    - By mastering closures, you'll gain deeper insights into JavaScript's functional programming paradigms and scope management!

#### 5. How to implement a deep clone of an object in JavaScript?
- A deep clone creates a new object that is a completely independent copy of the original object, including all nested objects and arrays. 
- Here are the various ways to implement a deep clone
- **Using `structuredClone` (Modern and Recommended)**
    - The built-in structuredClone function, introduced in modern browsers and Node.js, can deep clone most objects

        ```code
        const original = { a: 1, b: { c: 2 } };
        const clone = structuredClone(original);

        clone.b.c = 3;
        console.log(original.b.c); // 2 (original remains unchanged)
        ```
    - Handles circular references
    - Works for complex structures like Maps, Sets, and Dates
    - Fast and simple
    - Limited support in older environments (e.g., IE)
- **Best Practices**
    - **For modern environments** - Use `structuredClone` or `_.cloneDeep` from Lodash
    - **For simpler data** - Use `JSON.parse(JSON.stringify(object))`
    - **For custom or complex requirements** - Implement a recursive function with circular reference handling

#### 7. What is the event loop, and how does it work in JavaScript?
- A mechanism that handles asynchronous operations, such as handling user input, HTTP requests, or timers. It ensures that non-blocking code, like callbacks and promises, runs at the appropriate time while keeping the execution of synchronous code in order.
- **Key Concepts of the Event Loop**
    - **Call Stack**
        - The call stack is a LIFO (Last In, First Out) data structure that stores all the currently executing functions.
        - When a function is called, it gets pushed onto the stack, and when the function execution completes, it is popped from the stack.
    - **Event Queue (or Message Queue)** 
        - The event queue holds messages (or tasks) waiting to be processed. 
        - These tasks are typically associated with asynchronous operations like I/O, timers, or events.
    - **Web APIs (or Browser APIs)** 
        - These are provided by the browser environment and enable asynchronous tasks, such as `setTimeout`, `fetch`, or event listeners. 
        - Once an asynchronous operation completes, it puts the callback (or promise handler) in the event queue.
    - **Microtask Queue**
        - The microtask queue is similar to the event queue, but it has a higher priority. 
        - This queue holds tasks like promise's `.then` or `async`/`await` handlers. Microtasks are always processed before the event queue.
    - **The Event Loop** 
        - The event loop constantly checks the call stack and the event queues. 
        - It follows this sequence
            - Check if the call stack is empty.
            - If the stack is empty, the event loop looks at the microtask queue and executes any pending microtasks.
            - After the microtask queue is empty, it checks the event queue and moves the first task from the event queue to the call stack.
- **Event Loop Execution Flow**
    - **Synchronous Code** 
        - All synchronous code is executed first. 
        - Functions are pushed onto the call stack, and once they finish, they are removed from the stack.
    - **Asynchronous Code**
        - Asynchronous functions, like `setTimeout`, `fetch`, or event listeners, get executed later. 
        - These operations go through Web APIs, and their associated callbacks are pushed to the event queue once the asynchronous task is completed.
    - **Microtasks**
        - After each synchronous operation completes, the event loop first processes all tasks in the microtask queue (e.g., promise callbacks).
        - This ensures that promises are resolved as soon as possible after the current synchronous code finishes.
    - **Rendering**
        - Once the call stack and queues are clear, the browser can perform any necessary rendering (e.g., updating the DOM).