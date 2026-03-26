# IntelliJ Java Shortcuts

These are officially called **Live Templates** in IntelliJ. Instead of just suggesting words, they generate entire blocks of code and automatically place your cursor exactly where you need to type next.

Here is how the flow works:

```text
[ THE LIVE TEMPLATE MAGIC ]

1. You type a tiny abbreviation:    sout
                                      |
2. You press the action key:      [ Tab ] or [ Enter ]
                                      |
                                      v
3. IntelliJ builds the code:        System.out.println("|");
                                                        ^
                                          (Your cursor lands right here!)
```

Here is a master list of the most useful default templates for Java, grouped by what they do.

### 1. Printing to the Console (The `sout` Family)
You already know `sout`, but IntelliJ has a few smarter variations that save you from manually typing variable names.

* `sout` → Standard print.
    ```java
    System.out.println("");
    ```
* `soutv` → Prints the value of the last variable you used. 
    ```java
    System.out.println("myUser = " + myUser);
    ```
* `soutm` → Prints the current class and method name (perfect for quick "Did I reach this code?" debugging).
    ```java
    System.out.println("App.calculateTotal");
    ```
* `serr` → Standard error print (shows up as red text in your console).
    ```java
    System.err.println("");
    ```

### 2. The Entry Point
* `psvm` (or simply `main`) → Creates the standard Java main method.
    ```java
    public static void main(String[] args) {
        
    }
    ```

### 3. Loops (The Biggest Time Savers)
Writing loops manually takes a lot of keystrokes. These templates guess what list or array you want to loop through based on the code above it.

* `fori` → A standard counting `for` loop.
    ```java
    for (int i = 0; i < ; i++) {
        
    }
    ```
* `iter` → An enhanced "for-each" loop. It automatically finds the nearest List or Collection and sets it up.
    ```java
    for (String item : itemList) {
        
    }
    ```
* `itar` → A standard `for` loop specifically designed to iterate over an Array instead of a List.

### 4. Null Checks
Preventing `NullPointerException` crashes is a huge part of Java.

* `ifn` → If Null.
    ```java
    if (myObject == null) {
        
    }
    ```
* `inn` → If Not Null.
    ```java
    if (myObject != null) {
        
    }
    ```

### 5. Constants and Variables
Typing out long access modifiers for constants gets repetitive.

* `psf` → `public static final`
* `prsf` → `private static final`
* `psfi` → `public static final int`
* `psfs` → `public static final String`

---

### Pro-Tip: "Postfix Completion"

IntelliJ has an even faster version of Live Templates called **Postfix Completion**. Instead of typing the abbreviation first, you type your variable *first*, then add a dot, then the abbreviation.

```text
[ POSTFIX COMPLETION FLOW ]

1. Type your variable:       myList
2. Add dot and template:     myList.fori
                                  |
                              [ Tab ]
                                  |
                                  v
3. Instantly expands to:     for (int i = 0; i < myList.size(); i++) {
                                 
                             }
```

**Great Postfix examples:**
* `myList.null` → expands to `if (myList == null) {}`
* `myList.notnull` → expands to `if (myList != null) {}`
* `"Hello".sout` → expands to `System.out.println("Hello");`
* `myBoolean.if` → expands to `if (myBoolean) {}`

Would you like to learn how to create your own custom Live Template? For example, we could make one where typing `logger` instantly writes the SLF4J logger setup code (`private static final Logger logger = LoggerFactory.getLogger(...)`) so you never have to memorize it!
