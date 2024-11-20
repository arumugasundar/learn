
# JavaScript - Exception Handling

- Exceptions (errors) can be handled using the `try...catch` statement
- Allows to execute code that might throw an error and deal with that error gracefully
- Preventing the script from crashing
- **Syntax**

    ```code
    try {
        // Code that might throw an exception
    } catch (error) {
        // Code to handle the error
    } finally {
        // (Optional) Code that always executes, regardless of an error
    }
    ```
    
- **Key Components**
    - **`try` Block**
        - Contains code that might throw an exception
        - If no error occurs, the `catch` block is skipped
    - **`catch` Block**
        - Handles any error thrown in the `try` block
        - The error object provides details about what went wrong
    - **`finally` Block**
        - Executes after the `try` and `catch` blocks, regardless of whether an exception occurred
        - Useful for cleanup tasks like closing a file or releasing resources


## Types of Errors
1. [ReferenceError](#)
2. [SyntaxError](#)
3. [TypeError](#)
4. [RangeError](#)
5. [URIError](#)
6. [AggregateError](#)

## Examples
1. [Basic Example](#)
2. [Custom Error Messages](#)
3. [Using `finally`](#)
4. [Catching Specific Errors](#)
5. [Re-Throwing Errors](#)
6. [Asynchronous Errors](#)

### 1. ReferenceError
- Occurs when referencing a variable or function that is not defined

    ```code
    try {
        console.log(undefinedVariable);
    } catch (error) {
        console.log('Caught a ReferenceError:', error.message);
    }
    ```

### 2. SyntaxError
- Occurs during code parsing due to invalid syntax

    ```code
    try {
        eval('var a = ;'); // Invalid syntax
    } catch (error) {
        console.log('Caught a SyntaxError:', error.message);
    }
    ```
    
### 3. TypeError
- Occurs when a value is not of the expected type

    ```code
    try {
        null.toString(); // Cannot call a method on null
    } catch (error) {
        console.log('Caught a TypeError:', error.message);
    }
    ```

### 4. RangeError
- Occurs when a number is outside the allowable range

    ```code
    try {
        const arr = new Array(-5); // Invalid array length
    } catch (error) {
        console.log('Caught a RangeError:', error.message);
    }
    ```

### 5. URIError
- Occurs when dealing with malformed URIs

    ```code
    try {
        decodeURIComponent('%'); // Malformed URI
    } catch (error) {
        console.log('Caught a URIError:', error.message);
    }
    ```

### 6. AggregateError
- Occurs when handling multiple errors in Promises

    ```code
     try {
        const promises = [
            Promise.reject('Error 1'),
            Promise.reject('Error 2'),
        ];
        Promise.any(promises).catch(error => {
            console.log('Caught an AggregateError:', error.errors);
        });
    } catch (error) {
        console.log(error.message);
    }
    ```


--------------------------------------------------------------

### 1. Basic Example

    ```code
    try {
        const num = 10 / 0; // No exception, but result is Infinity
        console.log(num);

        JSON.parse('invalidJSON'); // Throws a SyntaxError
    } catch (error) {
        console.log('An error occurred:', error.message); // Logs: An error occurred: Unexpected token i in JSON
    } finally {
        console.log('Execution complete'); // Always runs
    }
    ```

### 2. Custom Error Messages
- throw user defined errors using `throw`

    ```code
    try {
        const age = -1;
        if (age < 0) {
            throw new Error('Age cannot be negative');
        }
    } catch (error) {
        console.log('Caught an error:', error.message); // Caught an error: Age cannot be negative
    }
    ```

### 3. Using `finally`

    ```code
    function readFile() {
        try {
            console.log('Opening file...');
            // Simulate an error
            throw new Error('File not found');
        } catch (error) {
            console.log('Error:', error.message); // Error: File not found
        } finally {
            console.log('Closing file...'); // Always runs
        }
    }

    readFile();
    ```

### 4. Catching Specific Errors
-  To identify the type of error and handle it accordingly

    ```code
    try {
        undefinedFunction(); // ReferenceError
    } catch (error) {
        if (error instanceof ReferenceError) {
            console.log('ReferenceError occurred:', error.message);
        } else {
            console.log('An unexpected error occurred:', error.message);
        }
    }
    ```

### 5. Re-Throwing Errors
- catch an error, perform some action, and re-throw it to be handled by a higher-level `catch`

    ```code
    function process() {
            try {
                try {
                throw new Error('Something went wrong');
                } catch (error) {
                console.log('Handling error locally:', error.message);
                throw error; // Re-throw the error
                }
            } catch (error) {
                console.log('Handling error globally:', error.message);
            }
        }

        process();
    ```

### 6. Asynchronous Errors
- Errors in asynchronous code (like Promises) are not caught by `try...catch`. need to use `.catch()` or `async/await`

    ```code
     // Using Promises
    fetch('invalid-url')
    .then(response => response.json())
    .catch(error => {
        console.log('Caught an async error:', error.message);
    });

    // Using async/await with try...catch
    async function fetchData() {
    try {
        const response = await fetch('invalid-url');
        const data = await response.json();
    } catch (error) {
        console.log('Caught an async error:', error.message);
    }
    }

    fetchData();
    ```