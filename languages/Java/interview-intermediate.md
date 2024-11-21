
# Interview - Intermediate

### Questions
1. [What is the difference between HashMap and Hashtable?](#1-what-is-the-difference-between-hashmap-and-hashtable)
2. [What are transient and volatile keywords?](#2-what-are-transient-and-volatile-keywords)
3. [How does Java handle memory management?](#3-how-does-java-handle-memory-management)
4. [What is the difference between Comparable and Comparator?](#4-what-is-the-difference-between-comparable-and-comparator)
5. [Explain the purpose of synchronized in Java.](#5-explain-the-purpose-of-synchronized-in-java)
6. [What are Java annotations, and why are they used?](#6-what-are-java-annotations-and-why-are-they-used)
7. [What is the difference between Exception and Error?](#7-what-is-the-difference-between-exception-and-error)
8. [What is the Java Reflection API?](#8-what-is-the-java-reflection-api)
9. [What is the difference between ExecutorService and Thread?](#9-what-is-the-difference-between-executorservice-and-thread)
10. [What is the difference between String.intern() and a regular String?](#10-what-is-the-difference-between-stringintern-and-a-regular-string)

#### 1. What is the difference between HashMap and Hashtable?
- **HashMap**
    - Not synchronized, faster.
    - Allows one null key and multiple null values.
- **Hashtable**
    - Synchronized, thread-safe.
    - Does not allow null keys or values.

#### 2. What are transient and volatile keywords?
- **transient** - Prevents serialization of a variable.
- **volatile** - Ensures visibility of changes to variables across threads.

#### 3. How does Java handle memory management?
- **Heap** - Stores objects and their instance variables.
- **Stack** - Stores method calls and local variables.
- **Garbage Collector (GC)** - Automatically reclaims unused objects.

#### 4. What is the difference between Comparable and Comparator?
- **Comparable**
    - Defines natural ordering via `compareTo()` method.
    - Implemented within the class.
- **Comparator**
    - Defines custom ordering via `compare()` method.
    - Implemented in a separate class.

#### 5. Explain the purpose of synchronized in Java.
- Ensures that only one thread can access a block of code or method at a time.
- Prevents thread interference and maintains consistency in shared resources.

#### 6. What are Java annotations, and why are they used?
- Metadata that provides additional information to the compiler or runtime.
- **Examples** - `@Override`, `@Deprecated`, `@FunctionalInterface`.

#### 7. What is the difference between Exception and Error?
- **Exception** - Recoverable issue (e.g., IOException)
- **Error** - Irrecoverable issue (e.g., OutOfMemoryError)

#### 8. What is the Java Reflection API?
- Allows inspection and modification of classes, methods, and fields at runtime.
- Used for frameworks, debugging, and dynamic method invocation.

#### 9. What is the difference between ExecutorService and Thread?
- **Thread** - Creates and manages individual threads.
- **ExecutorService** - Manages a pool of threads for optimized task execution.

#### 10. What is the difference between String.intern() and a regular String?
- **Regular String** - Stored in the heap.
- **intern()** - Stores the string in the String Pool, ensuring only one instance per unique value