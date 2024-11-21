
# Interview - Easy
### Questions
1. [What are the main features of Java?](#1-what-are-the-main-features-of-java)
2. [What is the difference between JDK, JRE, and JVM?](#2-what-is-the-difference-between-jdk-jre-and-jvm)
3. [What is the difference between == and .equals()?](#3-what-is-the-difference-between--and-equals)
4. [What are Java access modifiers?](#4-what-are-java-access-modifiers)
5. [What is the difference between ArrayList and LinkedList?](#5-what-is-the-difference-between-arraylist-and-linkedlist)
6. [What is the purpose of the final keyword in Java?](#6-what-is-the-purpose-of-the-final-keyword-in-java)
7. [What is a static keyword?](#7-what-is-a-static-keyword)
8. [What is the difference between String, StringBuilder, and StringBuffer?](#8-what-is-the-difference-between-string-stringbuilder-and-stringbuffer)
9. [What are checked and unchecked exceptions?](#9-what-are-checked-and-unchecked-exceptions)
10. [What is the difference between abstract class and interface?](#10-what-is-the-difference-between-abstract-class-and-interface)

#### 1. What are the main features of Java?
- Object-oriented
- Platform-independent (via JVM and bytecode)
- Robust (exception handling, garbage collection)
- Secure (no explicit pointers, runtime checks)
- Multithreaded
- High performance (JIT compiler)

#### 2. What is the difference between JDK, JRE, and JVM?
- JVM (Java Virtual Machine): Runs Java bytecode.
- JRE (Java Runtime Environment): Provides libraries and JVM for running Java applications.
- JDK (Java Development Kit): Includes JRE + tools (compiler, debugger) for development.

#### 3. What is the difference between == and .equals()?
- `==` - Compares memory references (object identity).
- `.equals()` - Compares content of objects (logical equality, overridden in classes like String).

#### 4. What are Java access modifiers?
- `public` - Accessible from anywhere.
- `private` - Accessible within the same class.
- `protected` - Accessible within the same package and subclasses.
- `Default (no modifier)` - Accessible within the same package.

#### 5. What is the difference between ArrayList and LinkedList?
- **ArrayList**
    - Faster for accessing elements.
    - Uses dynamic arrays.
- **LinkedList**
    - Faster for insertion/deletion.
    - Uses doubly linked lists.

#### 6. What is the purpose of the final keyword in Java?
- **final class** - Cannot be subclassed.
- **final method** - Cannot be overridden.
- **final variable** - Value cannot be changed (constant).

#### 7. What is a static keyword?
- **static variable** - Shared across all instances.
- **static method** - Can be called without creating an instance.
- **static block** - Executes once during class loading.

#### 8. What is the difference between String, StringBuilder, and StringBuffer?
**String** - Immutable, stored in the String pool.
**StringBuilder** - Mutable, not thread-safe, faster.
**StringBuffer** - Mutable, thread-safe, slower than StringBuilder.

#### 9. What are checked and unchecked exceptions?
**Checked exceptions** - Compile-time exceptions (e.g., IOException, SQLException).
**Unchecked exceptions** - Runtime exceptions (e.g., NullPointerException, ArithmeticException).

#### 10. What is the difference between abstract class and interface?
- **Abstract class**
    - Can have abstract and concrete methods.
    - Supports constructors and instance variables.
    - Single inheritance.
- **Interface**
    - Only abstract methods (before Java 8; Java 8+ can have default and static methods).
    - No constructors or instance variables.
    - Supports multiple inheritance