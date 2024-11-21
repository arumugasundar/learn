#### 1. What is OOP? List its main principles.
- OOP (Object-Oriented Programming) is a programming paradigm based on objects containing data (fields) and methods (functions).
- Main principles:
    - Encapsulation: Hiding implementation details.
    - Inheritance: Reusing code through parent-child relationships.
    - Polymorphism: Performing a single action in different ways.
    - Abstraction: Showing essential features, hiding complexity.

#### 2. What is a class? How is it different from an object?
- Class: A blueprint for creating objects. Defines properties and behaviors.
- Object: An instance of a class with its own values for properties.

```code
class Car {
    String color;
    void drive() { System.out.println("Driving"); }
}
Car myCar = new Car(); // Object
```

#### 3. What is encapsulation? Why is it important?
- Encapsulation is the process of restricting direct access to certain details of an object and controlling access through getters and setters.

```code
class Account {
    private double balance; // Hidden field
    public double getBalance() { return balance; }
    public void deposit(double amount) { balance += amount; }
}
```

#### 4. What is inheritance in OOP?
- Inheritance allows a class (child) to inherit fields and methods from another class (parent)

```code
class Vehicle {
    void move() { System.out.println("Vehicle is moving"); }
}
class Car extends Vehicle {
    void honk() { System.out.println("Car honks"); }
}
```

#### 5. What is polymorphism? Explain with an example.
- Polymorphism means "many forms" and allows methods to perform differently based on the object.
    - Example of Method Overloading (Compile-time Polymorphism):

        ```code
        class Calculator {
            int add(int a, int b) { return a + b; }
            double add(double a, double b) { return a + b; }
        }
        ```

    - Example of Method Overriding (Runtime Polymorphism)

        ```code
        class Animal { void sound() { System.out.println("Animal sound"); } }
        class Dog extends Animal { void sound() { System.out.println("Bark"); } }
        ```

#### 6. What is abstraction in OOP?
- Abstraction is the concept of hiding implementation details and showing only functionality to the user
- Achieved using abstract classes or interfaces

    ```code
    abstract class Animal {
        abstract void makeSound();
    }
    class Dog extends Animal {
        void makeSound() { System.out.println("Bark"); }
    }
    ```

#### 7. What are constructors?
- A constructor is a special method used to initialize objects
- It has the same name as the class and no return type

```code
class Person {
    String name;
    Person(String name) { this.name = name; }
}
Person p = new Person("John"); // Constructor call
```

#### 8. What is the difference between method overloading and method overriding?
- Overloading: Same method name, different parameters. Happens in the same class.
- Overriding: Child class redefines a parent class method with the same signature.

#### 9. What is the difference between an abstract class and an interface?
- Abstract Class:
    - Can have concrete and abstract methods.
    - Supports fields with default values.
    - Inherits using extends.
- Interface:
    - Only abstract methods (prior to Java 8).
    - Supports multiple inheritance.
    - Implements using implements.

#### 10. What is a static method?
- A static method belongs to the class, not instances, and can be called without creating an object.

```code
class MathUtils {
    static int square(int x) { return x * x; }
}
MathUtils.square(5); // Calls static method
```

#### 11. What is a `this` keyword in Java?
- The `this` keyword refers to the current instance of the class

```code
class Employee {
    String name;
    Employee(String name) { this.name = name; } // Refers to instance variable
}
```

#### 12. What is the `super` keyword?
- The `super` keyword refers to the parent class and can access its methods or constructor.

```code
class Parent { void greet() { System.out.println("Hello from Parent"); } }
class Child extends Parent {
    void greet() { super.greet(); System.out.println("Hello from Child"); }
}
```

#### 13. What is the difference between composition and inheritance?
- Inheritance: "Is-a" relationship
```code
class Dog extends Animal {} // Dog is an Animal
```
- Composition: "Has-a" relationship
```code
class Car {
    Engine engine; // Car has an Engine
}
```

#### 14. What is object cloning?
- Creating an exact copy of an object. Achieved by implementing the `Cloneable` interface and overriding the `clone()` method

```code
class Employee implements Cloneable {
    String name;
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
```





