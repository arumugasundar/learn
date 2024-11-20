
# Callback Function
- a function that is passed as an argument to another function and is executed after the completion of that function
- It enables asynchronous programming and allows functions to run in a sequence or when a particular event occurs

## Characteristics
- **Passed as an Argument** - It is provided as an input to another function.
- **Executed Later** - It is invoked (called back) after the parent function completes its execution or meets a condition.

## Syntax
```code
function mainFunction(callback) {
  // Perform some operations
  callback(); // Call the callback function
}
```

## Why Are Callbacks Important?
- `Asynchronous Programming` - Essential for tasks like API calls, file I/O, or timers
- `Reusability` - You can define generic functions and use different callback implementations for custom behavior
- `Event Handling` - Callbacks are the core of event-driven programming in JavaScript

## Potential Issues with Callbacks
- `Callback Hell` - When multiple nested callbacks create complex, hard-to-read code

    ```code
    asyncTask1(function (result1) {
        asyncTask2(result1, function (result2) {
            asyncTask3(result2, function (result3) {
            console.log(result3);
            });
        });
    });
    ```

- `Solution` - Use Promises or async/await for better readability

    ```code
    async function runTasks() {
        const result1 = await asyncTask1();
        const result2 = await asyncTask2(result1);
        const result3 = await asyncTask3(result2);
        console.log(result3);
    }
    runTasks();
    ```

### Examples

1. [Basic Example](#1-basic-example)
2. [Asynchronous Example](#2-asynchronous-example)
3. [Event Handling](#3-event-handling)
4. [Array Methods](#4-array-methods)
5. [Custom Callback Function](#5-custom-callback-function)

#### 1. Basic Example

```code
function greet(name) {
  console.log(`Hello, ${name}!`);
}

function processUserInput(callback) {
  const userName = 'Alice';
  callback(userName); // Call the callback with a parameter
}

processUserInput(greet);
// Output: Hello, Alice!
```

#### 2. Asynchronous Example
- When working with asynchronous tasks like fetching data or reading files, callbacks are used to handle the result after completion

    ```code
    function fetchData(callback) {
    console.log('Fetching data...');
    setTimeout(() => {
        const data = { name: 'Alice', age: 25 };
        callback(data); // Call the callback with the fetched data
    }, 2000);
    }

    function displayData(data) {
    console.log('Data received:', data);
    }

    fetchData(displayData);
    // Output:
    // Fetching data...
    // (after 2 seconds) Data received: { name: 'Alice', age: 25 }
    ```

#### 3. Event Handling
- Callbacks are commonly used in event listeners

    ```code
    document.getElementById('button').addEventListener('click', function () {
    console.log('Button clicked!');
    });
    ```

#### 4. Array Methods
- Several JavaScript array methods use callback functions, such as `map`, `filter`, and `reduce`
    - **`map` Example**

        ```code
        const numbers = [1, 2, 3, 4];
        const doubled = numbers.map(num => num * 2);
        console.log(doubled); // Output: [2, 4, 6, 8]
        ```

    - **`filter` Example**

        ```code
        const numbers = [1, 2, 3, 4];
        const evenNumbers = numbers.filter(num => num % 2 === 0);
        console.log(evenNumbers); // Output: [2, 4]
        ```

#### 5. Custom Callback Function

    ```code
    function calculate(num1, num2, callback) {
        const result = num1 + num2;
        callback(result); // Call the callback with the result
    }

    calculate(5, 10, function (result) {
        console.log('The sum is:', result); // Output: The sum is: 15
    });
    ```

