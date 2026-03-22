<!-- TOC --><a name="advanced-number-data-types-and-var"></a>
# Advanced number data types and var

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Advanced number data types and var](#advanced-number-data-types-and-var)
   * [Long, BigInteger and BigDecimal](#long-biginteger-and-bigdecimal)
      + [1. The Non-Trivial Problem: The "Odometer" Overflow](#1-the-non-trivial-problem-the-odometer-overflow)
         - [ASCII Diagram: The Odometer Rollover](#ascii-diagram-the-odometer-rollover)
      + [2. Java's Escalation Ladder (What & How)](#2-javas-escalation-ladder-what-how)
         - [Step 1: `long` (The Bigger Primitive Box)](#step-1-long-the-bigger-primitive-box)
         - [Step 2: `BigInteger` (The Infinite Train)](#step-2-biginteger-the-infinite-train)
         - [Step 3: `BigDecimal` (The Money Saver)](#step-3-bigdecimal-the-money-saver)
         - [ASCII Diagram: The Memory Boxes](#ascii-diagram-the-memory-boxes)
      + [3. Conversions: When and How](#3-conversions-when-and-how)
         - [ASCII Diagram: The Conversion Bridge](#ascii-diagram-the-conversion-bridge)
         - [The Code: Converting Back and Forth](#the-code-converting-back-and-forth)
      + [4. Comparison: JavaScript & Node.js](#4-comparison-javascript-nodejs)
         - [JavaScript's Solution: `BigInt`](#javascripts-solution-bigint)
         - [The Missing Piece in JS: Decimals](#the-missing-piece-in-js-decimals)
         - [Common methods of BigInteger and BigDecimal](#common-methods-of-biginteger-and-bigdecimal)
   * [Using a BigInteger as a loop counter](#using-a-biginteger-as-a-loop-counter)
      + [ASCII Diagram: Translating the Loop](#ascii-diagram-translating-the-loop)
         - [The 3 Rules of the BigInteger Loop:](#the-3-rules-of-the-biginteger-loop)
         - [The Java Code Example (For Loop)](#the-java-code-example-for-loop)
         - [The Java Code Example (While Loop - Often Cleaner)](#the-java-code-example-while-loop-often-cleaner)
      + [Comparison: JavaScript & Node.js](#comparison-javascript-nodejs)
         - [ASCII Diagram: JS BigInt Loop](#ascii-diagram-js-bigint-loop)
         - [The JavaScript / Node.js Code](#the-javascript-nodejs-code)
      + [Summary Table](#summary-table)
   * [How `compareTo` Works: The 3 Magic Numbers](#how-compareto-works-the-3-magic-numbers)
      + [ASCII Diagram: The Weighing Scale](#ascii-diagram-the-weighing-scale)
      + [Translating the Loop Conditional](#translating-the-loop-conditional)
      + [ASCII Diagram: The Translation](#ascii-diagram-the-translation)
   * [The `var` keyword](#the-var-keyword)
      + [1. The Non-Trivial Concept: `var` is NOT a Type!](#1-the-non-trivial-concept-var-is-not-a-type)
         - [ASCII Diagram: The Compiler at Work](#ascii-diagram-the-compiler-at-work)
      + [2. Why do we need it? (The Boilerplate Problem)](#2-why-do-we-need-it-the-boilerplate-problem)
         - [The Problem vs. The Solution](#the-problem-vs-the-solution)
      + [3. How to use it (and the strict rules)](#3-how-to-use-it-and-the-strict-rules)
         - [ASCII Diagram: The "Guessing" Rule](#ascii-diagram-the-guessing-rule)
      + [4. Primitives, Conversions, and `var`](#4-primitives-conversions-and-var)
         - [Code Example: Primitives and Casting](#code-example-primitives-and-casting)
      + [5. Comparison: Java `var` vs. JavaScript / Node.js `var`](#5-comparison-java-var-vs-javascript-nodejs-var)
         - [ASCII Diagram: The Rigid Box vs. The Flexible Bucket](#ascii-diagram-the-rigid-box-vs-the-flexible-bucket)
         - [Table Comparison](#table-comparison)

<!-- TOC end -->

<!-- TOC --><a name="long-biginteger-and-bigdecimal"></a>
## Long, BigInteger and BigDecimal

Advanced data types in Java exist for one simple reason: **standard memory boxes are too small for extreme math, and standard decimals are famously bad at exact math.**

When you write software for a bank, a scientific lab, or cryptography, being "close enough" or running out of room is catastrophic.

<!-- TOC --><a name="1-the-non-trivial-problem-the-odometer-overflow"></a>
### 1. The Non-Trivial Problem: The "Odometer" Overflow

Before understanding `long` or `BigInteger`, you must understand **Integer Overflow**. 

A standard Java `int` is a box made of exactly 32 bits (1s and 0s). The absolute maximum number you can fit in that box is exactly **2,147,483,647** (about 2 billion). 

If you have 2 billion dollars, and you add 1 more dollar, the computer doesn't crash. Instead, it acts like an old car's mechanical odometer that runs out of numbers. It rolls over completely backward into the negative numbers!

<!-- TOC --><a name="ascii-diagram-the-odometer-rollover"></a>
#### ASCII Diagram: The Odometer Rollover
```text
  [ 2,147,483,647 ]  <-- The absolute maximum 'int' limit
+ [             1 ]
-------------------
  [-2,147,483,648 ]  <-- BOOM! You suddenly have negative 2 billion dollars.
```
*This exact bug has caused rockets to crash and video games to break.*


<!-- TOC --><a name="2-javas-escalation-ladder-what-how"></a>
### 2. Java's Escalation Ladder (What & How)

To solve the Odometer problem, Java provides bigger boxes. 



<!-- TOC --><a name="step-1-long-the-bigger-primitive-box"></a>
#### Step 1: `long` (The Bigger Primitive Box)
If `int` isn't enough, you use `long`. It is a 64-bit box. It holds up to **~9 quintillion**. 
* **How:** You must put an `L` at the end of the number so Java knows to use the bigger box.
```java
long distanceToStar = 9460730472580800L; 
```

<!-- TOC --><a name="step-2-biginteger-the-infinite-train"></a>
#### Step 2: `BigInteger` (The Infinite Train)
What if you are calculating the mass of the universe, and 9 quintillion is too small? You use `BigInteger`. 
* **What:** It is an Object, not a primitive. It doesn't use a fixed box. It links memory blocks together like train cars. It can hold a number literally millions of digits long, limited only by your computer's total RAM.
* **How:** Because it's an Object, you cannot use the `+` or `*` keys. You must use methods.
```java
import java.math.BigInteger;

BigInteger hugeNum = new BigInteger("999999999999999999999999999999");
BigInteger anotherNum = new BigInteger("2");

// You can't do: hugeNum * anotherNum
BigInteger result = hugeNum.multiply(anotherNum); 
```

<!-- TOC --><a name="step-3-bigdecimal-the-money-saver"></a>
#### Step 3: `BigDecimal` (The Money Saver)
Standard decimals in Java (`double` and `float`) are built for speed, not accuracy. If you do `0.1 + 0.2` with a `double`, Java often spits out `0.30000000000000004`. If you are writing software for a bank, you will be fired.
* **What:** `BigDecimal` is an infinite-precision decimal. It does math perfectly exactly, down to the thousandth decimal place if needed.
```java
import java.math.BigDecimal;

BigDecimal price = new BigDecimal("0.1");
BigDecimal tax = new BigDecimal("0.2");

BigDecimal total = price.add(tax); // Exactly 0.3. Perfect.
```

<!-- TOC --><a name="ascii-diagram-the-memory-boxes"></a>
#### ASCII Diagram: The Memory Boxes
```text
[ int  ] -> Fits: 2 Billion
[ long ] -> Fits: 9 Quintillion
[ BigInteger ] -> Fits: [ 9 ]-[ 9 ]-[ 9 ]-[ 9 ]... (Keeps adding train cars forever)
```


<!-- TOC --><a name="3-conversions-when-and-how"></a>
### 3. Conversions: When and How

**Why convert?** Objects like `BigInteger` and `BigDecimal` are incredibly slow to calculate compared to raw primitives like `int` and `long`. You only want to use the heavy machinery when absolutely necessary. If a calculation results in a small number, you convert it back down to save computer processing power.

<!-- TOC --><a name="ascii-diagram-the-conversion-bridge"></a>
#### ASCII Diagram: The Conversion Bridge
```text
  (Fast but limited)                        (Slow but infinite)
  [ PRIMITIVES: int, long ]  <==========>  [ OBJECTS: BigInteger ]
          |                                          |
    int myInt = 5;                                   |
          |----------> ( Going UP ) ---------------->|
                            BigInteger.valueOf(myInt)

          |<--------- ( Going DOWN ) <---------------|
    hugeObject.intValue()                          BigInteger hugeObject
```

<!-- TOC --><a name="the-code-converting-back-and-forth"></a>
#### The Code: Converting Back and Forth
```java
// 1. Primitive to Object (Going Up)
long normalLong = 500L;
BigInteger heavyObject = BigInteger.valueOf(normalLong);

// 2. String to Object (Going Up - very common for user input)
BigDecimal exactMoney = new BigDecimal("49.99");

// 3. Object to Primitive (Going Down)
// DANGER: If the BigInteger is bigger than an 'int' can hold, the data gets corrupted!
int normalInt = heavyObject.intValue(); 
long normalLongAgain = heavyObject.longValue();
```

<!-- TOC --><a name="4-comparison-javascript-nodejs"></a>
### 4. Comparison: JavaScript & Node.js

Historically, JavaScript was terrible at this. It only had one number type: `Number`. It was a double-precision float, meaning JS couldn't safely count integers past about **9 quadrillion** (`9007199254740991`). After that limit, JS literally starts guessing the numbers!

<!-- TOC --><a name="javascripts-solution-bigint"></a>
#### JavaScript's Solution: `BigInt`
Modern JS and Node.js introduced `BigInt` to solve the integer problem.
* **How:** You just add an `n` to the end of the number.

```javascript
// A standard Number
let normalNum = 9007199254740991;

// A JS BigInt (Notice the 'n')
let massiveNum = 9007199254740991999999n; 
let result = massiveNum * 2n; 
```

<!-- TOC --><a name="the-missing-piece-in-js-decimals"></a>
#### The Missing Piece in JS: Decimals
JavaScript **does not have a built-in `BigDecimal`**. If you need exact financial math in Node.js, you absolutely must download a third-party library like `decimal.js` or `big.js`. 

| Feature | Java | JavaScript / Node.js |
| :--- | :--- | :--- |
| **Standard Integer** | `int` (up to ~2 Bil) | `Number` (up to ~9 Quad) |
| **Large Integer** | `long` (up to ~9 Quin) | N/A (Uses `Number`) |
| **Infinite Integer**| `BigInteger` (Object) | `BigInt` (Primitive, append `n`) |
| **Exact Decimals** | `BigDecimal` (Object) | **None!** (Requires 3rd party package) |

<!-- TOC --><a name="common-methods-of-biginteger-and-bigdecimal"></a>
#### Common methods of BigInteger and BigDecimal

|Method        |Description                                                              |Code Example                                       |Result                  |
|--------------|-------------------------------------------------------------------------|---------------------------------------------------|------------------------|
|add(val)      |Adds two BigIntegers together.                                           |new BigInteger("10").add(new BigInteger("5"))      |15                      |
|subtract(val) |Subtracts the value.                                                     |new BigInteger("10").subtract(new BigInteger("5")) |5                       |
|multiply(val) |Multiplies the values.                                                   |new BigInteger("10").multiply(new BigInteger("5")) |50                      |
|divide(val)   |Divides the values. (It chops off remainders, just like normal integers).|new BigInteger("10").divide(new BigInteger("3"))   |3 (No decimals allowed!)|
|remainder(val)|Gives you what is left over after a division (the modulo % operator).    |new BigInteger("10").remainder(new BigInteger("3"))|1                       |
|pow(int)      |Raises the number to a power (exponents). The power must be a normal int.|new BigInteger("2").pow(3)                         |8 (Which is 2 * 2 * 2)  |
|abs()         |Absolute value. Turns negatives into positives.                          |new BigInteger("-50").abs()                        |50                      |


<!-- TOC --><a name="using-a-biginteger-as-a-loop-counter"></a>
## Using a BigInteger as a loop counter

Looping over a `BigInteger` in Java is a classic "gotcha" moment for developers. It looks intimidating at first because you suddenly lose all your favorite programming symbols!

When you write a normal `for` loop with an `int`, you rely heavily on operators like `<` (less than) and `++` (plus one). 

Because `BigInteger` is an **Object** and not a primitive box, Java absolutely refuses to let you use those symbols. You have to translate those symbols into **Method Calls**.

<!-- TOC --><a name="ascii-diagram-translating-the-loop"></a>
### ASCII Diagram: Translating the Loop
```text
NORMAL INT LOOP:   for ( int i = 0;             i < max;                   i++ )
                             |                     |                        |
                          (Start)               (Stop)                   (Step)
                             |                     |                        |
BIGINTEGER LOOP:   for ( BigInteger i = ZERO;   i.compareTo(max) < 0;      i = i.add(ONE) )
```

Let's break down the three parts of the loop (Start, Stop, and Step) to see exactly how Java expects them to be written.

<!-- TOC --><a name="the-3-rules-of-the-biginteger-loop"></a>
#### The 3 Rules of the BigInteger Loop:
1.  **Start:** Use `BigInteger.ZERO` or `BigInteger.ONE` instead of typing `new BigInteger("0")`. Java provides these as built-in shortcuts to save memory.
2.  **Stop:** Use `.compareTo()`. Remember, `A.compareTo(B) < 0` means "A is less than B".
3.  **Step:** Use `i = i.add(BigInteger.ONE)`. **CRITICAL:** `BigInteger` is immutable (unchangeable). Doing `i.add(ONE)` does nothing unless you save the result back into the `i` variable!

<!-- TOC --><a name="the-java-code-example-for-loop"></a>
#### The Java Code Example (For Loop)
```java
import java.math.BigInteger;

public class BigLoop {
    public static void main(String[] args) {
        
        // Let's loop 5 times, but using BigInteger
        BigInteger limit = new BigInteger("5");
        
        // START                 // STOP                   // STEP
        for (BigInteger i = BigInteger.ZERO; i.compareTo(limit) < 0; i = i.add(BigInteger.ONE)) {
            
            System.out.println("Current loop count: " + i);
            
        }
    }
}
```

<!-- TOC --><a name="the-java-code-example-while-loop-often-cleaner"></a>
#### The Java Code Example (While Loop - Often Cleaner)
Because the `for` loop gets very long and hard to read with all those words, many Java developers prefer a `while` loop for `BigInteger`.

```java
BigInteger limit = new BigInteger("5");
BigInteger count = BigInteger.ZERO;

while (count.compareTo(limit) < 0) {
    System.out.println("While loop count: " + count);
    count = count.add(BigInteger.ONE); // The step happens inside the loop
}
```


<!-- TOC --><a name="comparison-javascript-nodejs"></a>
### Comparison: JavaScript & Node.js

This is where JavaScript developers get to laugh at Java developers. 

Because modern JavaScript uses `BigInt` as a **primitive** data type (by adding an `n` to the end of the number), the JS engine perfectly understands standard math symbols! You can just write a normal loop.

<!-- TOC --><a name="ascii-diagram-js-bigint-loop"></a>
#### ASCII Diagram: JS BigInt Loop
```text
[ JS ENGINE ] ---> Sees '0n' ---> "Ah, a BigInt primitive!"
      |
      +---> Allows normal operators: < , <= , ++ , --
```

<!-- TOC --><a name="the-javascript-nodejs-code"></a>
#### The JavaScript / Node.js Code
```javascript
// The limit is a BigInt (notice the 'n')
let limit = 5n;

// You can use standard < and ++ just like a normal number!
for (let i = 0n; i < limit; i++) {
    console.log("Current loop count: " + i);
}
```

<!-- TOC --><a name="summary-table"></a>
### Summary Table

| Action | Java `int` | Java `BigInteger` | Node.js `BigInt` |
| :--- | :--- | :--- | :--- |
| **Start Variable** | `int i = 0;` | `BigInteger i = BigInteger.ZERO;` | `let i = 0n;` |
| **Check Condition**| `i < limit;` | `i.compareTo(limit) < 0;` | `i < limit;` |
| **Increment** | `i++` | `i = i.add(BigInteger.ONE)` | `i++` |

<!-- TOC --><a name="how-compareto-works-the-3-magic-numbers"></a>
## How `compareTo` Works: The 3 Magic Numbers

In Java, `compareTo()` is a built-in method used to figure out which of two Objects is "bigger," "smaller," or if they are "equal." 

When you call `A.compareTo(B)`, you are asking Object A to weigh itself against Object B. 
It will always return one of three simple integer numbers: **-1**, **0**, or **1**.

<!-- TOC --><a name="ascii-diagram-the-weighing-scale"></a>
### ASCII Diagram: The Weighing Scale

Let's say we do: `result = A.compareTo(B)`

**Scenario 1: Returns `-1` (A is smaller)**
```text
    [ B ]
      |
      |          [ A ]
      |            |
------------------------  <-- A is lighter/smaller than B. Result is -1.
```

**Scenario 2: Returns `0` (A and B are equal)**
```text
    [ B ]        [ A ]
      |            |
------------------------  <-- Perfectly balanced! Result is 0.
```

**Scenario 3: Returns `1` (A is bigger)**
```text
                 [ A ]
                   |
    [ B ]          |
      |            |
------------------------  <-- A is heavier/bigger than B. Result is 1.
```
*(Note: Sometimes Java returns any negative or positive number, like -5 or +2, but the logic is exactly the same: negative means smaller, positive means bigger).*


<!-- TOC --><a name="translating-the-loop-conditional"></a>
### Translating the Loop Conditional

Now, let's look at your loop question. In a normal loop, you write:
`i < limit`

Because `i` and `limit` are BigIntegers, we must use `compareTo`. We want the loop to keep running as long as `i` is smaller than `limit`. 

If `i` is smaller than `limit`, what does `i.compareTo(limit)` return? **It returns a negative number (like -1).**

So, to ask Java "Is 'i' smaller than 'limit'?", we literally ask: **"Does comparing 'i' to 'limit' result in a number less than 0?"**

<!-- TOC --><a name="ascii-diagram-the-translation"></a>
### ASCII Diagram: The Translation
```text
THE NORMAL WAY:       Is 'i' less than 'limit'?
                      [ i < limit ]

THE BIGINTEGER WAY:   Does weighing 'i' against 'limit' give us a negative number?
                      [ i.compareTo(limit) < 0 ]
```

**Other translations to memorize:**
* `i == limit`  translates to `i.compareTo(limit) == 0`
* `i > limit`   translates to `i.compareTo(limit) > 0`
* `i <= limit`  translates to `i.compareTo(limit) <= 0`

<!-- TOC --><a name="the-var-keyword"></a>
## The `var` keyword

In older versions of Java, you had to explicitly tell the computer exactly what type of box to build for your data before you could put anything inside it. Starting in Java 10, Java introduced the `var` keyword. It is a feature called **Local Variable Type Inference**. Think of `var` as telling the Java compiler: *"Look at what I'm putting on the right side of the equals sign, and just figure out the box size yourself."*

<!-- TOC --><a name="1-the-non-trivial-concept-var-is-not-a-type"></a>
### 1. The Non-Trivial Concept: `var` is NOT a Type!

Before we write code, we must clear up the biggest misunderstanding about Java's `var`. 

In Java, `var` is **not a data type**. It is a shortcut for the compiler. Java is still perfectly, strictly typed (Static Typing). Once the compiler guesses the type on line 1, that box is locked forever. You cannot put a text string into a box that the compiler decided was an integer.

<!-- TOC --><a name="ascii-diagram-the-compiler-at-work"></a>
#### ASCII Diagram: The Compiler at Work
```text
WHAT YOU WRITE:
var age = 25; 

WHAT THE COMPILER DOES BEHIND THE SCENES:
[ Compiler sees "25" ] --> [ Knows "25" is an 'int' ] --> [ Translates 'var' to 'int' ]

WHAT THE PROGRAM ACTUALLY RUNS:
int age = 25; 
```


<!-- TOC --><a name="2-why-do-we-need-it-the-boilerplate-problem"></a>
### 2. Why do we need it? (The Boilerplate Problem)

Java is famous for being incredibly wordy. Often, you find yourself typing the exact same massive word on both sides of the equals sign. `var` was created to save your fingers and make the code easier to read.

<!-- TOC --><a name="the-problem-vs-the-solution"></a>
#### The Problem vs. The Solution
**The Old Way (Repetitive and hard to read):**
```java
// We have to say 'HashMap' twice!
HashMap<String, ArrayList<Integer>> myMap = new HashMap<String, ArrayList<Integer>>();
```

**The New Way (Clean and simple):**
```java
// The compiler sees the right side and says "Ah, I know what myMap is."
var myMap = new HashMap<String, ArrayList<Integer>>();
```


<!-- TOC --><a name="3-how-to-use-it-and-the-strict-rules"></a>
### 3. How to use it (and the strict rules)

Because Java is strict, you can't just use `var` everywhere. 

**Rule 1: It only works for Local Variables.** (Variables inside a method). You cannot use it for class-level properties.
**Rule 2: You MUST give it a value immediately.** If you don't, the compiler has nothing to look at to guess the type!

<!-- TOC --><a name="ascii-diagram-the-guessing-rule"></a>
#### ASCII Diagram: The "Guessing" Rule
```text
  var name;                 <--- ERROR! Compiler says: "I can't guess nothing!"
  name = "John";            

  var name = "John";        <--- SUCCESS! Compiler says: "Ah, it's a String!"
```


<!-- TOC --><a name="4-primitives-conversions-and-var"></a>
### 4. Primitives, Conversions, and `var`

You asked how we convert `var` to primitives or other types. 
The trick is: **You don't convert `var`. You convert the *value*, and `var` just adapts.**

By default, if you type a whole number, `var` makes an `int`. If you type a decimal, `var` makes a `double`. 

If you want a different primitive (like a `byte` or a `float`), you must explicitly cast the number, or use Java's letter suffixes (`F` for float, `L` for long).

<!-- TOC --><a name="code-example-primitives-and-casting"></a>
#### Code Example: Primitives and Casting
```java
// 1. Standard Primitives
var age = 30;          // Compiler makes an 'int'
var price = 19.99;     // Compiler makes a 'double'

// 2. Forcing a different primitive
var hugeNumber = 5000L;          // The 'L' forces a 'long'
var tinyNumber = (byte) 5;       // The cast '(byte)' forces a 'byte'

// 3. Converting later (Standard Java casting)
var myDouble = 9.99;             // It's a double
var myInt = (int) myDouble;      // We cast it to an int (becomes 9)
```


<!-- TOC --><a name="5-comparison-java-var-vs-javascript-nodejs-var"></a>
### 5. Comparison: Java `var` vs. JavaScript / Node.js `var`

This is where developers coming from JavaScript to Java get completely blindsided. 

* **Java's `var`:** Locks the type permanently based on the first value.
* **JavaScript's `var`:** Is a completely lawless, flexible bucket. It can hold a number on line 1, and text on line 2. (This is called Dynamic Typing).

<!-- TOC --><a name="ascii-diagram-the-rigid-box-vs-the-flexible-bucket"></a>
#### ASCII Diagram: The Rigid Box vs. The Flexible Bucket

**Java (Rigid Box):**
```text
var score = 100;    --> [ INT BOX created ] --> Put 100 inside.
score = "Winner";   --> [ INT BOX ] <---------- ERROR! Cannot fit text into an Int box!
```

**JavaScript / Node.js (Flexible Bucket):**
```text
var score = 100;    --> [ BUCKET ] -----------> Put 100 inside.
score = "Winner";   --> [ BUCKET ] -----------> Dumps out 100, puts "Winner" inside. SUCCESS!
```

<!-- TOC --><a name="table-comparison"></a>
#### Table Comparison

| Feature | Java `var` | JavaScript / Node.js `var` |
| :--- | :--- | :--- |
| **Typing** | **Static** (Type is permanently locked) | **Dynamic** (Type can change anytime) |
| **Scope** | Strictly block-scoped (only lives inside the `{ }` where it was made) | Function-scoped (can cause weird bugs where it leaks outside of loops) |
| **Modern Usage**| Highly recommended for local variables to reduce clutter. | **Avoid in JS!** Modern Node.js developers use `let` and `const` instead. |
