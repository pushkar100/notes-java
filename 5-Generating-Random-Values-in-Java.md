<!-- TOC --><a name="generating-random-values-in-java"></a>
# Generating Random Values in Java

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Generating Random Values in Java](#generating-random-values-in-java)
   * [The `Random` class](#the-random-class)
      + [1. The Non-Trivial Part: "Pseudo" Randomness and The Seed](#1-the-non-trivial-part-pseudo-randomness-and-the-seed)
         - [ASCII Diagram: The Random Machine](#ascii-diagram-the-random-machine)
      + [2. Java: How to Use the `Random` Class](#2-java-how-to-use-the-random-class)
         - [Step 1: Import and Create](#step-1-import-and-create)
         - [The "Bounds" Trap (Crucial Concept)](#the-bounds-trap-crucial-concept)
         - [ASCII Diagram: The Bounds of nextInt(6)](#ascii-diagram-the-bounds-of-nextint6)
      + [3. Comparison: Java vs. JavaScript](#3-comparison-java-vs-javascript)
         - [ASCII Diagram: The Toolboxes](#ascii-diagram-the-toolboxes)
      + [4. Code Comparison for Common Use Cases](#4-code-comparison-for-common-use-cases)
         - [Use Case 1: Flipping a Coin (True / False)](#use-case-1-flipping-a-coin-true-false)
         - [Use Case 2: Picking a Random Number from 0 to 99](#use-case-2-picking-a-random-number-from-0-to-99)
      + [5. What about Node.js?](#5-what-about-nodejs)
      + [6. Picking a random item from an array or list](#6-picking-a-random-item-from-an-array-or-list)
      + [Java: Arrays vs. Lists](#java-arrays-vs-lists)
         - [Example A: Using a standard Array](#example-a-using-a-standard-array)
         - [Example B: Using an ArrayList](#example-b-using-an-arraylist)
      + [3. Comparison: JavaScript & Node.js](#3-comparison-javascript-nodejs)
         - [ASCII Diagram: The JavaScript Math](#ascii-diagram-the-javascript-math)
         - [JavaScript / Node.js Code](#javascript-nodejs-code)
      + [4. Summary Table](#4-summary-table)

<!-- TOC end -->

<!-- TOC --><a name="the-random-class"></a>
## The `Random` class

The `Random` class in Java is like a virtual dice-roller, coin-flipper, or card-shuffler. Whenever your program needs an element of surprise or unpredictability, you use this tool.

<!-- TOC --><a name="1-the-non-trivial-part-pseudo-randomness-and-the-seed"></a>
### 1. The Non-Trivial Part: "Pseudo" Randomness and The Seed

Before we write code, we must understand a massive quirk about computers: **Computers cannot be truly random.** They are perfectly logical machines; they only do exactly what they are told.

To fake randomness, they use a massive, complex mathematical formula. 
But every formula needs a starting number to begin calculating. This starting number is called the **Seed**. By default, Java uses the current time on your computer's clock (down to the nanosecond) as the seed.

<!-- TOC --><a name="ascii-diagram-the-random-machine"></a>
#### ASCII Diagram: The Random Machine
```text
[ CURRENT TIME ] ---> (The Seed: 1711048... )
                             |
                             v
                 [ THE MATH FORMULA MACHINE ] 
                             |
                             +---> [ Number 1: 42 ] ---> (Becomes new seed)
                             |
                 [ THE MATH FORMULA MACHINE ]
                             |
                             +---> [ Number 2: 7 ]  ---> (Becomes new seed)
```
*Note: If you give the machine the exact same Seed twice, it will spit out the exact same sequence of numbers forever!*


<!-- TOC --><a name="2-java-how-to-use-the-random-class"></a>
### 2. Java: How to Use the `Random` Class

In Java, `Random` is an object. You have to build the "machine" before you can ask it for numbers.

<!-- TOC --><a name="step-1-import-and-create"></a>
#### Step 1: Import and Create
```java
import java.util.Random; // 1. Bring in the blueprint

public class Game {
    public static void main(String[] args) {
        Random diceMachine = new Random(); // 2. Build the machine
        
        // 3. Ask for a number
        int roll = diceMachine.nextInt(6); 
        System.out.println("You rolled: " + roll);
    }
}
```

<!-- TOC --><a name="the-bounds-trap-crucial-concept"></a>
#### The "Bounds" Trap (Crucial Concept)
When you ask Java for `nextInt(6)`, it does **not** give you a number from 1 to 6. Computers start counting at 0. It gives you a number from 0 to 5. The number you provide (6) is the **ceiling**, and it is exclusively blocked.

<!-- TOC --><a name="ascii-diagram-the-bounds-of-nextint6"></a>
#### ASCII Diagram: The Bounds of nextInt(6)
```text
  [0]   [1]   [2]   [3]   [4]   [5] |  [6]
   ^     ^     ^     ^     ^     ^  |   ^
   |----- CAN BE CHOSEN ----------- | BLOCKED!
```
**To get a real dice roll (1 to 6), you must do simple math:**
`int realRoll = diceMachine.nextInt(6) + 1;`


<!-- TOC --><a name="3-comparison-java-vs-javascript"></a>
### 3. Comparison: Java vs. JavaScript

This is where the languages take very different approaches. 

* **Java** gives you a dedicated object with many convenient buttons: "Give me an integer," "Give me a boolean (true/false)," "Give me a decimal."
* **JavaScript** gives you exactly *one* tool: `Math.random()`. It only ever gives you a long decimal number between 0.0 and 0.999... It is up to you to do the math to turn that decimal into whatever you actually need.

<!-- TOC --><a name="ascii-diagram-the-toolboxes"></a>
#### ASCII Diagram: The Toolboxes
**Java's Toolbox (`new Random()`):**
```text
[ BUTTON: nextInt(10) ]   -----> Outputs: 7
[ BUTTON: nextBoolean() ] -----> Outputs: true
[ BUTTON: nextDouble() ]  -----> Outputs: 0.4582...
```

**JavaScript's Toolbox (`Math`):**
```text
[ BUTTON: Math.random() ] -----> Outputs: 0.7491...
   (Wait, I wanted a whole number from 1 to 10?)
   -> You must build it: Math.floor(Math.random() * 10) + 1
```


<!-- TOC --><a name="4-code-comparison-for-common-use-cases"></a>
### 4. Code Comparison for Common Use Cases

<!-- TOC --><a name="use-case-1-flipping-a-coin-true-false"></a>
#### Use Case 1: Flipping a Coin (True / False)
**Java:** Clean and built-in.
```java
Random rand = new Random();
boolean heads = rand.nextBoolean();
```
**JavaScript:** You have to invent it using math.
```javascript
// If the decimal is bigger than 0.5, call it true.
let heads = Math.random() > 0.5; 
```

<!-- TOC --><a name="use-case-2-picking-a-random-number-from-0-to-99"></a>
#### Use Case 2: Picking a Random Number from 0 to 99
**Java:**
```java
Random rand = new Random();
int enemyHealth = rand.nextInt(100); 
```
**JavaScript:**
```javascript
// 1. Get decimal (e.g., 0.428)
// 2. Multiply by 100 (e.g., 42.8)
// 3. Chop off the decimal using Math.floor (e.g., 42)
let enemyHealth = Math.floor(Math.random() * 100);
```

<!-- TOC --><a name="5-what-about-nodejs"></a>
### 5. What about Node.js?

Node.js uses the exact same `Math.random()` as standard browser JavaScript. 

However, because Node.js is often used for backend servers and security (like generating passwords or secure login tokens), it includes a special module called `crypto`. Standard pseudo-randomness is easy for hackers to predict. `crypto` pulls randomness from the actual physical hardware of the server to be completely unpredictable.

**Node.js Secure Random:**
```javascript
const crypto = require('crypto');

// Gives a cryptographically secure random number from 0 to 99
const secureNum = crypto.randomInt(0, 100); 
```

*(Note: Java also has a secure version for this exact same reason, called `SecureRandom`, which works exactly like the `Random` class but is unhackable).*

<!-- TOC --><a name="6-picking-a-random-item-from-an-array-or-list"></a>
### 6. Picking a random item from an array or list

Picking a random item from a collection (like a deck of cards) is one of the most common things you will do with the `Random` class. 

To understand how to do this, we have to realize that the computer doesn't actually pick a random *item*. It picks a random **slot number** (an index), and then you look inside that slot.

<!-- TOC --><a name="java-arrays-vs-lists"></a>
### Java: Arrays vs. Lists

In Java, you store multiple items in either an **Array** (fixed size) or an **ArrayList** (flexible size). The logic is exactly the same for both, but the words you use to get the size and fetch the item are slightly different.

<!-- TOC --><a name="example-a-using-a-standard-array"></a>
#### Example A: Using a standard Array
Arrays use `.length` to find out how many items exist, and square brackets `[]` to open the slot.

```java
import java.util.Random;

public class CardGame {
    public static void main(String[] args) {
        // 1. Create the deck
        String[] deck = {"Ace", "King", "Queen", "Jack"};
        
        // 2. Build the random machine
        Random rand = new Random();
        
        // 3. Pick a random slot from 0 to 3. 
        // We use deck.length (which is 4) as the ceiling limit.
        int randomIndex = rand.nextInt(deck.length); 
        
        // 4. Open that slot
        String drawnCard = deck[randomIndex];
        
        System.out.println("You drew the: " + drawnCard);
    }
}
```

<!-- TOC --><a name="example-b-using-an-arraylist"></a>
#### Example B: Using an ArrayList
Lists use `.size()` to find out how many items exist, and `.get()` to open the slot.

```java
import java.util.ArrayList;
import java.util.Random;

public class ListGame {
    public static void main(String[] args) {
        ArrayList<String> deck = new ArrayList<>();
        deck.add("Ace");
        deck.add("King");
        deck.add("Queen");
        
        Random rand = new Random();
        
        // Use .size() for ArrayLists
        int randomIndex = rand.nextInt(deck.size()); 
        
        // Use .get() to pull the item out
        String drawnCard = deck.get(randomIndex); 
    }
}
```


<!-- TOC --><a name="3-comparison-javascript-nodejs"></a>
### 3. Comparison: JavaScript & Node.js

Because JavaScript uses `Math.random()` (which only gives decimals like `0.345...`), getting a random item from an array requires combining three different Math tools.

1. `Math.random()` to get the decimal.
2. Multiply it by the `array.length` to scale it up.
3. `Math.floor()` to chop off the decimal points and turn it into a clean slot number.

<!-- TOC --><a name="ascii-diagram-the-javascript-math"></a>
#### ASCII Diagram: The JavaScript Math
```text
Goal: Pick from an array of 4 items.

Step 1: Math.random()            ====> 0.621
Step 2: 0.621 * deck.length (4)  ====> 2.484
Step 3: Math.floor(2.484)        ====> 2  (This is our random slot!)
```

<!-- TOC --><a name="javascript-nodejs-code"></a>
#### JavaScript / Node.js Code
JavaScript only has Arrays (they act like Java's flexible ArrayLists by default).

```javascript
let deck = ["Ace", "King", "Queen", "Jack"];

// The standard formula for picking a random JS array item
let randomIndex = Math.floor(Math.random() * deck.length);

let drawnCard = deck[randomIndex];
console.log("You drew the: " + drawnCard);
```

<!-- TOC --><a name="4-summary-table"></a>
### 4. Summary Table

| Step | Java (Array) | Java (ArrayList) | JavaScript / Node.js |
| :--- | :--- | :--- | :--- |
| **Find Size** | `deck.length` | `deck.size()` | `deck.length` |
| **Get Random Slot** | `rand.nextInt(size)` | `rand.nextInt(size)` | `Math.floor(Math.random() * size)` |
| **Fetch Item** | `deck[index]` | `deck.get(index)` | `deck[index]` |

