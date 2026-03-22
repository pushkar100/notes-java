<!-- TOC --><a name="nested-classes-and-their-scope"></a>
# Nested classes and their scope

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Nested classes and their scope](#nested-classes-and-their-scope)
   * [1. The Non-Trivial Concept: The "Invisible Umbilical Cord"](#1-the-non-trivial-concept-the-invisible-umbilical-cord)
      + [ASCII Diagram: The Umbilical Cord](#ascii-diagram-the-umbilical-cord)
   * [2. Why do we need them? (Practical Use Cases)](#2-why-do-we-need-them-practical-use-cases)
      + [When NOT to use them:](#when-not-to-use-them)
   * [3. How it works: Java Code Examples & Scope](#3-how-it-works-java-code-examples-scope)
      + [Type 1: The Inner Class (Non-Static)](#type-1-the-inner-class-non-static)
      + [Type 2: The Static Nested Class](#type-2-the-static-nested-class)
   * [4. Comparison: Java vs. JavaScript & Node.js](#4-comparison-java-vs-javascript-nodejs)
      + [ASCII Diagram: Java Nesting vs JS Closures](#ascii-diagram-java-nesting-vs-js-closures)
      + [Node.js Equivalent (Module Exporting)](#nodejs-equivalent-module-exporting)
   * [Nested classes interacting with siblings](#nested-classes-interacting-with-siblings)
      + [1. The Non-Trivial Concept: The "Family Trust" Rule](#1-the-non-trivial-concept-the-family-trust-rule)
         - [ASCII Diagram: The Family House](#ascii-diagram-the-family-house)
      + [2. Java: How Siblings Interact](#2-java-how-siblings-interact)
         - [The Java Code Example](#the-java-code-example)
      + [3. Comparison: Java vs. JavaScript & Node.js](#3-comparison-java-vs-javascript-nodejs)
         - [ASCII Diagram: JavaScript's "Locked Safes"](#ascii-diagram-javascripts-locked-safes)
         - [The JavaScript / Node.js Code Example](#the-javascript-nodejs-code-example)
      + [4. Summary Table](#4-summary-table)

<!-- TOC end -->

Nested classes in Java are exactly what they sound like: a class written completely inside the curly braces of another class. 

Think of it like a **Russian Matryoshka doll**, or a **Car and its Engine**. An Engine is a complex object on its own (so it deserves its own class), but it really only makes sense in the context of a Car.

<!-- TOC --><a name="1-the-non-trivial-concept-the-invisible-umbilical-cord"></a>
## 1. The Non-Trivial Concept: The "Invisible Umbilical Cord"

Before looking at code, we must understand the biggest hurdle in Java nested classes: **Static vs. Non-Static**. 

When you put a class inside another class, Java gives you two ways to do it.

1.  **Inner Class (Non-Static):** The inner class is born physically attached to a specific instance of the outer class. It has an invisible "umbilical cord" connecting it to the outer object, allowing it to see all of the outer object's private secrets.
2.  **Static Nested Class:** The inner class is just "parked" inside the outer class for organizational purposes. There is no umbilical cord. It doesn't belong to any specific outer object.

<!-- TOC --><a name="ascii-diagram-the-umbilical-cord"></a>
### ASCII Diagram: The Umbilical Cord

**1. Inner Class (Non-Static):**
```text
[ OUTER CLASS OBJECT (e.g., MyCar) ]
      |
      |-- private String VIN = "12345";
      |
      +========= (Invisible Umbilical Cord) =========+
                                                     |
                                        [ INNER CLASS OBJECT (e.g., MyEngine) ]
                                          - Can read MyCar's VIN easily!
```

**2. Static Nested Class:**
```text
[ OUTER CLASS BLUEPRINT (e.g., MathUtils) ]
      |
      |-- static double PI = 3.14;
      |
      x   <-- NO CORD!
      |
[ STATIC NESTED CLASS (e.g., Calculator) ]
  - Can only see static stuff like PI. 
  - Cannot see instance variables because it's not attached to an object!
```


<!-- TOC --><a name="2-why-do-we-need-them-practical-use-cases"></a>
## 2. Why do we need them? (Practical Use Cases)

1.  **Logical Grouping:** If Class B is *only* ever useful to Class A, keep them together. (e.g., A `Node` inside a `LinkedList`).
2.  **Encapsulation (Hiding):** You can make a nested class `private`. This means the outside world doesn't even know it exists. 
3.  **Readability:** It keeps related code right next to each other instead of scattered across dozens of files.

<!-- TOC --><a name="when-not-to-use-them"></a>
### When NOT to use them:
* If the nested class could be useful to *other* classes (e.g., if you build a `Tire` class inside `Car`, but later realize your `Bicycle` class also needs Tires).
* If your outer class is getting massive (thousands of lines long). It becomes too hard to read.


<!-- TOC --><a name="3-how-it-works-java-code-examples-scope"></a>
## 3. How it works: Java Code Examples & Scope

Let's look at the two main types with clear examples of how their "Scope" (what they can see and access) works.

<!-- TOC --><a name="type-1-the-inner-class-non-static"></a>
### Type 1: The Inner Class (Non-Static)
Notice how the `Engine` can access the `carModel` variable, even though `carModel` is strictly `private` to the `Car`.

```java
public class Car {
    private String carModel = "Mustang"; // Outer property

    // 1. Define the Inner Class
    public class Engine {
        private int horsepower = 400; // Inner property
        
        public void start() {
            // It can access its own properties AND the parent's properties!
            System.out.println("Starting the " + horsepower + "HP engine of the " + carModel);
        }
    }

    public void testDrive() {
        // 2. The Outer class can create the Inner class easily
        Engine myEngine = new Engine();
        myEngine.start();
    }
}
```

<!-- TOC --><a name="type-2-the-static-nested-class"></a>
### Type 2: The Static Nested Class
Usually used for "Helpers" or the famous **Builder Pattern**.

```java
public class User {
    private String name;

    // A static nested class
    public static class Builder {
        private String bName;
        
        public Builder setName(String n) {
            this.bName = n;
            return this;
        }
        
        public User build() {
            User u = new User();
            u.name = this.bName; // Can access private members of outer class!
            return u;
        }
    }
}

// Usage in another file:
// We don't need a User object to create a Builder object!
User.Builder myVault = new User.Builder(); 
```


<!-- TOC --><a name="4-comparison-java-vs-javascript-nodejs"></a>
## 4. Comparison: Java vs. JavaScript & Node.js

JavaScript approaches this completely differently. Because JavaScript functions are "First-Class Citizens," JS developers usually nest *functions* (creating Closures) or just use standard JavaScript Objects, rather than strictly nesting formal classes.

While ES6 (Modern JS) *does* technically allow you to write a `class` inside another `class`'s method, it is highly unidiomatic (nobody does it).

<!-- TOC --><a name="ascii-diagram-java-nesting-vs-js-closures"></a>
### ASCII Diagram: Java Nesting vs JS Closures
**Java (Class inside Class):**
```text
[ Class: BankAccount ]
      |
      +-- [ Class: TransactionHistory ]
```

**JavaScript / Node.js (Function Closure):**
```text
[ Function: createBankAccount() ]
      |
      |-- let balance = 100; (Private state)
      |
      +-- [ Function: addTransaction() ]
            - Forms a "Closure", remembering the 'balance' variable.
```

<!-- TOC --><a name="nodejs-equivalent-module-exporting"></a>
### Node.js Equivalent (Module Exporting)
Instead of nesting classes to hide them, Node.js developers usually put multiple classes in one file, but only `export` the main one. The other class becomes effectively "private" to that file.

```javascript
// This acts like a private inner class because we DO NOT export it.
class Engine {
    constructor() { this.hp = 400; }
    start() { console.log(`Vroom! ${this.hp} HP`); }
}

// This acts like the Outer class
class Car {
    constructor(model) {
        this.model = model;
        this.engine = new Engine(); // Can use Engine here
    }
}

// We only expose Car to the rest of the app. Engine remains hidden!
module.exports = Car; 
```

| Feature | Java | JavaScript / Node.js |
| :--- | :--- | :--- |
| **Concept** | Nested Classes (Inner, Static) | Closures / Module Scoping |
| **Accessing Parent Data** | Automatic (via invisible cord) | Lexical Scoping (Inner functions see outer variables) |
| **Privacy** | Strict (`private class Engine`) | File-level (Don't `module.exports` it) |


<!-- TOC --><a name="nested-classes-interacting-with-siblings"></a>
## Nested classes interacting with siblings

When you have multiple nested classes sitting at the same level inside an Outer class, they act like siblings living in the same house. 

<!-- TOC --><a name="1-the-non-trivial-concept-the-family-trust-rule"></a>
### 1. The Non-Trivial Concept: The "Family Trust" Rule

The most surprising thing about sibling nested classes in Java is how they handle **privacy**. 

Normally, if a variable is marked `private`, nobody outside that specific class can see it. However, Java’s rule for privacy is actually based on the **top-level outer class** (the file level). 

Because Sibling A and Sibling B are born inside the exact same Outer class, they completely trust each other. **Sibling A can directly read and change Sibling B's `private` variables!**

<!-- TOC --><a name="ascii-diagram-the-family-house"></a>
#### ASCII Diagram: The Family House
```text
  [ THE OUTER CLASS: Computer ]  <-- The "House" boundary
               |
               |======( The Family Trust Zone )======|
               |                                     |
    [ Sibling 1: CPU ]                  [ Sibling 2: RAM ]
    - private int speed = 5;            - private int memory = 16;
               |                                     |
               +<------- Can read 'memory' --------->+
               +<------- Can read 'speed'  --------->+
```


<!-- TOC --><a name="2-java-how-siblings-interact"></a>
### 2. Java: How Siblings Interact

For one sibling to talk to another, it just needs to create an instance (an object) of its sibling.

<!-- TOC --><a name="the-java-code-example"></a>
#### The Java Code Example
Let's build a `Computer` that has a `CPU` and `RAM`. Notice how the CPU reaches right into the RAM's private stuff.

```java
public class Computer {

    // SIBLING 1
    public class CPU {
        private String cpuSecret = "Calculations";

        public void askRam() {
            // 1. CPU creates an instance of its sibling
            RAM myRam = new RAM();
            
            // 2. CPU accesses RAM's STRICTLY PRIVATE variable!
            System.out.println("CPU grabbed from RAM: " + myRam.ramSecret);
        }
    }

    // SIBLING 2
    public class RAM {
        private String ramSecret = "Stored User Data";
    }

    // Outer class testing it out
    public void runTest() {
        CPU myCpu = new CPU();
        myCpu.askRam(); 
    }
}
```
**Output:** `CPU grabbed from RAM: Stored User Data`


<!-- TOC --><a name="3-comparison-java-vs-javascript-nodejs"></a>
### 3. Comparison: Java vs. JavaScript & Node.js

This is where Java and modern JavaScript (ES6/Node.js) are completely opposite. 

In JavaScript, if you put two classes in the same file (the equivalent of being siblings in a module), they **do not** share a "Family Trust" zone when it comes to true private fields (variables starting with `#`).

In JS, `#private` means *strictly* private to that exact class block. Siblings cannot see each other's private data, even if they live in the same file.

<!-- TOC --><a name="ascii-diagram-javascripts-locked-safes"></a>
#### ASCII Diagram: JavaScript's "Locked Safes"
```text
  [ THE MODULE / FILE: computer.js ]  <-- The Neighborhood
               |
    [ Class 1: CPU ]                    [ Class 2: RAM ]
    - #speed = 5;                       - #memory = 16;
    (Locked Safe)                       (Locked Safe)
               |                                     |
               x <----- BLOCKED! Access Denied -----> x
```

<!-- TOC --><a name="the-javascript-nodejs-code-example"></a>
#### The JavaScript / Node.js Code Example
If you try to replicate the Java behavior in JS, your program will crash.

```javascript
class RAM {
    // Modern JS true private field
    #ramSecret = "Stored User Data"; 
}

class CPU {
    askRam() {
        const myRam = new RAM();
        
        // CRASH! SyntaxError: Private field '#ramSecret' must be declared in an enclosing class
        console.log("CPU grabbed from RAM: " + myRam.#ramSecret); 
    }
}
```
*Fix for JS:* You would have to build a public "getter" method inside `RAM` (like `getSecret()`) so the CPU can ask for it politely.


<!-- TOC --><a name="4-summary-table"></a>
### 4. Summary Table

| Feature | Java (Nested Siblings) | JavaScript / Node.js (Same File Classes) |
| :--- | :--- | :--- |
| **Can they instantiate each other?**| Yes | Yes |
| **Can they access each other's `public` data?**| Yes | Yes |
| **Can they access each other's `private` data?**| **Yes** (They share Outer Class scope) | **No** (Strict class-level encapsulation) |
| **Why?** | Java treats the Outer Class as the ultimate security boundary. | JS treats the individual Class as the ultimate security boundary. |
