# Java Concurrency & Multithreading Course

[Udemy: Become an expert in Multithreading, Concurrency & Parallel programming in Java, with strong emphasis on high performance](https://pplearn.udemy.com/course/java-multithreading-concurrency-performance-optimization/learn/lecture/10187964#overview)

## Motivation

A single thread has two issues:
1. **Responsiveness** (Delays, Waiting period, especially for end users). Becomes even more important for applications that have a User Interface (UI)
    - Solution: **Multitasking** (**Concurrency**): Multi-tasking between "threads" can achieve better responsiveness. We don't need multiple CPU cores for this, with just one CPU and multiple "threads", we can do it!
2. **Performance** (Create the *illusion* of running multiple tasks in parallel using just a *single core*)
    - Solution: Again, multiple "threads". True parallelism is only achieved via multiple CPU cores!
    - Impact: 
        - Fewer machines required at high scale -> Less money on hardware
        - Completes a complex task much faster!

## OS fundamentals - Programs and Processes

A **program** is the *recipe* (instructions stored on disk). 
- Program: A stored set of instructions, saved as a file (like `.exe`, `.sh`, `.py`) that tells the computer what to do, but is not running yet.

A **process** is the *cooking* (those instructions actually running in memory and using CPU).
- Process: A program that is currently running, with its own memory, CPU state, and resources managed by the operating system
- Examples: (1) `chrome.exe` on disk → program (2) When you open Chrome and it appears on screen → process (actually often many processes)

### Location and format

#### Program

- Lives: Mostly in *secondary storage* (disk/SSD), as a file.
- Basic format: Instructions + static data in a file (executable or script).

Location:
```
Disk / SSD
+----------------------------------------+
|  my_app.exe   (Program: code + data)   |
+----------------------------------------+
|  editor.py    (Program: source code)   |
+----------------------------------------+
```

This file just sits there until the OS loads it.

Structure: Logically a program file has:
- Code: Instructions to execute.
- Data: Constants and initial data.

```
Program file (on disk)
+---------------------------+
|  Code section             |
|  (instructions)           |
+---------------------------+
|  Data section             |
|  (constants, globals)     |
+---------------------------+
```

#### Process

- Lives: In main memory (*RAM*) while running; tracked by the OS.
- Basic format: Program code + its own data + stack + heap + CPU registers + OS bookkeeping (PCB).

Location:
```
RAM (while running)
+------------------------------------------+
|  Code   | Data   | Stack | Heap | PCB   |
| (from   | (vars) |       |      | (OS   |
| program)|        |       |      | info) |
+------------------------------------------+
         ^ process = this whole package
```

The OS creates this package when you run the program and deletes it when it finishes.

Structure:
```
One process in memory
+---------------------------+
|  Code (from program)      |
+---------------------------+
|  Data (globals)           |
+---------------------------+
|  Heap (dynamic objects)   |
+---------------------------+
|  Stack (function calls)   |
+---------------------------+
|  CPU registers, PC        |
+---------------------------+
|  PCB (ID, state, files)   |
+---------------------------+
```

A process includes the program plus runtime state:
- Code: Copy of program instructions in RAM.
- Data: Global and static variables.
- Heap: Dynamically allocated memory (malloc, new, etc.).
- Stack: Function calls, local variables, return addresses.
- CPU state: Registers, program counter.
- PCB (Process Control Block): OS metadata (PID, state, priority, open files, etc.)

#### Process: key characteristics

- Active: Represents real execution of a program.
- Dynamic: Created when started, changes state (ready, running, waiting), and eventually terminates.
- Short-lived: Exists only while running; disappears after completion or kill.
- Uses resources: Needs CPU time, RAM, open files, I/O devices, etc.
- Has PCB: OS tracks it via a Process Control Block (ID, state, priority, etc.).
- Many per program: One program file can spawn multiple processes at once.

## Threads

A thread is a **lightweight path of execution** ***inside*** a process. 

In simple terms: program → process → threads (threads are the smallest running parts).

- Thread: The smallest sequence of instructions that the CPU can schedule and run, inside a process, ***sharing the process’s memory and resources***.
- A process can have one thread (single-threaded) or many threads (multi-threaded), all running parts of the same program at the same time (logically).

```
Program (on disk)
   |
   v
Process (in memory)
   |
   +-- Thread 1
   +-- Thread 2
   +-- Thread 3
```

Location: Where threads live:
- Threads live **inside a process, in RAM**, and are **managed by the OS scheduler**.
- Threads in the same process share:
    1. Code
    2. Global data
    3. Heap
    4. Open files / other resources

**Each thread has its own**:
1. **Stack** (function calls, local variables)
2. Registers (CPU state like program counter, etc.)
3. Thread control info (like a mini PCB, often called TCB)

```
Process address space (in RAM)
+-------------------------------------------+
|  Code (shared by all threads)             |
+-------------------------------------------+
|  Data / Globals (shared)                  |
+-------------------------------------------+
|  Heap (shared)                            |
+-------------------------------------------+
|  Stack - Thread 1 (private)               |
+-------------------------------------------+
|  Stack - Thread 2 (private)               |
+-------------------------------------------+
|  Stack - Thread 3 (private)               |
+-------------------------------------------+
           ^ all of this = one process
             with 3 threads
```

### Characrteristics of a thread

1. It is a Subset of a process (Threads cannot exist standalone)
2. Share memory, fast communication: Reading/writing globals and heap variables are used to share info
3. Lightweight and fast to switch: Creating a thread is cheaper/faster than creating a process (*Reason*: no separate whole address space).
4. Own stack, shared rest: 
    - local variables of one thread are not directly seen by others.
    - Code, globals, heap, and resources like file descriptors are shared.
5. Concurrency inside one process: Threads allow one process to do multiple things “at once”

Example of a multi-threaded browser process:
```
Browser process
+-------------------------------------------+
| Code: browser logic (shared)              |
+-------------------------------------------+
| Data/Heap: tabs, cache, settings (shared) |
+-------------------------------------------+
| Stack: UI thread                          |
+-------------------------------------------+
| Stack: Network thread                     |
+-------------------------------------------+
| Stack: Rendering thread                   |
+-------------------------------------------+
```

| Aspect         | Process                                 | Thread                                |
| -------------- | --------------------------------------- | ------------------------------------- |
| Lives where    | OS + RAM, its own address space         | Inside a process’s address space      |
| Relation       | Independent unit                        | Part of a process                     |
| Memory sharing | Does not share address space by default | Shares code, data, heap with siblings |
| Owns what      | Code, data, heap, stack, registers      | Own stack and registers; shares rest  |
| Cost           | Heavyweight, expensive to create/switch | Lightweight, cheaper to create/switch |
| Communication  | Slower, needs IPC                       | Fast, via shared memory               |

## Context switching

A **context switch** is when the CPU *stops* running one process or thread, *saves* its state, and then *loads and continues* another process or thread.

- Every thread or process: Consumes CPU and memory
- One context switch, the CPU will have to:
    1. Store the data for the current thread / process
    2. Restore data for another thread / process

**Too many context switches are bad!**
- Between too many threads, context switching leads to **thrashing**
- However, context switching between *threads* (consumes less resources) is *cheaper* than between processes (**Benefit of threads**)

**Thrashing** (w.r.t. context switching) is when the system spends so much time rapidly switching between processes/threads that it barely does any real work.

```
Time ----->

CPU:
   [Save A][Load B][Save B][Load C][Save C][Load A][Save A][Load B] ...
      ^       ^       ^       ^       ^
     CS      CS      CS      CS      CS
   (CS = context switch)

Work done:
   [  tiny ][ tiny ][ tiny ][ tiny ][ tiny ] ...
```
Here the CPU is mostly doing context switch overhead (Save/Load) for processes/threads A, B, C, instead of actually executing their useful instructions.

## Thread scheduling

Thread scheduling is the *decision-making process* that chooses which thread runs on the CPU next and for how long.

```
            +--------------------+
            |   Ready Threads    |
            |  (waiting to run)  |
            +--------------------+
              |    |       |
              v    v       v
            [T1] [T2]    [T3]
              \    |      /
               \   |     /
                \  |    /
                 \ |   /
                  \|  /
             +----------------+
             |   Scheduler    |
             +----------------+
                      |
          picks one   |   to run
                      v
               +-------------+
               |     CPU     |
               |  running    |
               |   T2 now    |
               +-------------+
```

### 1. First Come First Serve (FCFS)

First Come First Serve (FCFS) is a (non‑preemptive) scheduling algorithm where the process that arrives earliest gets the CPU first and runs until it finishes.

In pure FCFS itself, **starvation** usually appears in the form of **very long waiting times for short jobs** when a very long job arrives first, so the later short jobs are stuck until it completes; some authors describe this as “starvation of small processes” compared to more balanced scheduling algorithm

What is starvation?
- Starvation or "indefinite blocking" is when a process keeps waiting for a needed resource (like CPU) for a very long time or effectively forever because other processes are continually chosen instead

Why is starvation bad?
- It is bad because some processes may never make progress or complete, which breaks fairness and can cause parts of a system to “freeze” or become unusable while others keep running

### 2. Shortest Job First (SJF)

A scheduling algorithm that always *picks the ready process with the smallest CPU burst time* to run next

- *UI threads* usually perform very short, quick actions, so under SJF they get chosen early and often, keeping the interface responsive.

SJF also leads to starvation (of "long processes"):
- If new short jobs keep arriving, SJF keeps selecting them, so long-running processes can wait indefinitely and suffer starvation.

### 3. Epochs (The Modern OS Standard)

In **epoch scheduling**, time is divided into *fixed rounds called epochs* (moderately sliced), and tasks are given *CPU time* and *priorities* for each epoch, then reconsidered at the start of the next epoch.

Therefore, a slice of time within an epoch is assigned to each thread! (Note: Not all threads can complete within an epoch since they might require a larger time slice / more slices to do so)

```
Time ------------------------------------------->

Epoch 1          Epoch 2          Epoch 3
+-----------+    +-----------+    +-----------+
| T1 T2 T3  |    | T1 T4 T5  |    | T2 T3 T6  |
| scheduled |    | scheduled |    | scheduled |
+-----------+    +-----------+    +-----------+
      ^               ^                ^
   decide set &    re-evaluate &    re-evaluate &
   priorities      reshuffle tasks  reshuffle tasks
```

**Priority**: Selecting a time slice for each thread:

**`Dynamic priority = Static priority + bonus`** (bonus can be negative)

- Static priority: Set by the developer programmatically.
- Bonus: Adjusted by the OS in every epoch, for each thread.

Advantages:
1. Better fairness: Bonus raises priority for threads that waited more or used less CPU, so they get a chance next epoch.
2. Responsive UI: Interactive / I‑O bound threads get positive bonus, so their dynamic priority becomes higher and they are scheduled quickly.
3. Prevents hogging: CPU‑bound threads get negative bonus, lowering their dynamic priority so they cannot hog the CPU every epoch.
4. Adapts over time: Because priority = static priority + bonus is recomputed each epoch, the system automatically adjusts to changing workloads.

## When to use a multi-threaded architecture?

Reasons:
1. If the tasks **share a lot of the data**. Why? 
    - Threads are cheaper to create and destroy than Processes
    - Switching between threads (Context Switching) is much faster

## When to use a multi-process architecture?

Reasons:
1. **Security** and **stability** are of higher importance. Why?
    - Processes are completely isolated from one another
    - Threads share memory and communicate. Hence, a single bad thread can bring down the entire process
2. When **tasks are completely unrelated to each other**. Why?
    - You do not need to share data between the tasks and threads are mostly used for that i.e makes sense for performing related tasks together as threads
    - Processes are also interleaved and scheduled by the OS so they fit well for this use-case

## Threading fundamentals

### Creating a thread

All the thread related properties and methods are encapsulated in the **`Thread`** class by the **JDK** (Available by default).

1. Use `new Thread()` to instantiate an object of the class
2. We need to pass in an object of a class that implements the `Runnable` interface (We can instantiate it *inline* - a common pattern)
    - This interface needs to have one public and `void` returning method called **`run()`**
3. Invoke the `start()` method on the newly created Thread object

The **Runnable** interface is a Java interface that represents a task whose `run()` method can be executed by a thread.

Note: 
- In Java 8+, we can collpase the Runnable object creation into a Lambda function *(Not shown below)*
- Static `Thread` method, `currentThread()`, provides us an object with information on the current running thread. Use the `getName()` or `getId()` methods to fetch its name or ID.
- There is also a static method of a Thread called `sleep()` which puts the current thread to sleep for a given number number of milliseconds
    - How does it work? Instructs CPU to not schedule the thread until the time elapses

```java
public class App {
    public static void main(String[] args) throws Exception {
        Thread thread = new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("Hello from the " + Thread.currentThread().getName() + " thread!");
            }
        });

        System.out.println("We are in the " + Thread.currentThread().getName() + " thread before starting the new thread.");
        thread.start();
        System.out.println("We are in the " + Thread.currentThread().getName() + " thread after starting the new thread.");
    }
}
```

Output:
```
We are in the main thread before starting the new thread.
We are in the main thread after starting the new thread.
Hello from the Thread-0 thread!
```

Key points for `thread.start()`:
1. Creates a new thread (Thread‑0) and marks it as runnable.
2. It **returns immediately**; it **does not block main**, and it does not mean Thread‑0 runs right now.
3. The **OS scheduler decides when Thread‑0 actually gets CPU**.
4. Usually, the main thread keeps the CPU for a tiny bit longer, so it prints both lines before the scheduler gives a turn to Thread‑0. But, in the above example, it was very much possible for the print from the thread to appear between the two main thread prints had the CPU decided to schedule it sooner! Example:
```
We are in the main main thread before starting the new thread.
Hello from the Thread-0 thread!
We are in the main main thread after starting the new thread.
```

```java
public class App {
    public static void main(String[] args) throws Exception {
        Thread thread = new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("Hello from the " + Thread.currentThread().getName() + " thread!");
            }
        });

        System.out.println("We are in the " + Thread.currentThread().getName() + " thread before starting the new thread.");
        thread.start();

        Thread.sleep(5000); // Current (main) thread sleeps for 5 seconds and then gets re-scheduled (resumed)
        System.out.println("We are in the " + Thread.currentThread().getName() + " thread after starting the new thread.");
    }
}
```

Possible outputs (Depending on when CPU schedules the new thread):
```
Case A: Schedules thread immediately
We are in the main main thread before starting the new thread.
Hello from the Thread-0 thread!
// ... waits 5 seconds ...
We are in the main main thread after starting the new thread.


Case B: Schedules thread later than 5 secs (unlikely though!)
We are in the main main thread before starting the new thread.
// ... waits 5 seconds ...
We are in the main main thread after starting the new thread.
Hello from the Thread-0 thread!
```

### Setting the name and priority of a thread

In the above example, the auto-generated value for a thread's name (`Thread-0`) is not very friendly. Imagine we have 1000s of threads then knowing which thread number is asssociated with which thread is not easy!

"Static priority" of a thread can be set by the developer. The value ranges from 1 to 10.

1. Name:
    - `thread.setName()`: Sets the name of the thread
    - `thread.getName()`: Gets the name of the thread
2. Priority (static part):
    - `thread.setPriority()`: Sets the priority of the thread (1 to 10. We can also use constants for it: `Thread.MAX_PRIORITY` and `Thread.MIN_PRIORITY`)
    - `thread.getPriority()`: Gets the priority of the thread

Note: The current executing thread is referened by `Thread.currentThread()`.

```java
public class App {
    public static void main(String[] args) throws Exception {
        Thread thread = new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("Hello from the " + Thread.currentThread().getName() + " thread!");
                System.out.println("The priority of the thread is " + Thread.currentThread().getPriority());
            }
        });

        thread.setName("MyThread");
        thread.setPriority(Thread.MAX_PRIORITY);

        System.out.println("We are in the " + Thread.currentThread().getName() + " main thread before starting the new thread.");
        thread.start();
        System.out.println("We are in the " + Thread.currentThread().getName() + " main thread after starting the new thread.");
    }
}
```

Output:
```
We are in the main main thread before starting the new thread.
We are in the main main thread after starting the new thread.
Hello from the MyThread thread!
The priority of the thread is 10
```

**Note: Debugging threads in a multi-threaded app**
- Add debuggers in your IDE
- When the breakpoint is caught, the JVM window will display all the current threads as "Threads [<name>]" in the call-stack (If no threads other than main have started, only the main thread is displayed)
- JVM might always show some internal threads that it has created 
- All threads stop whenever a breakpoint is caught!
- We might see multiple breakpoints highlighted in the IDE (Why?: Multiple threads executions were paused!)

### Handling uncaught exceptions inside a thread

If any exceptions arise within a thread and they are uncaught, the whole program can get affected and crash.

In order to handle any thread exceptions outside the thread i.e not already handled within the thread code, we can provide a *static* `Thread.UncaughtExceptionHandler` to a *static* method called `setDefaultUncaughtExceptionHandler()` on the `Thread` class. It handles any exceptions occurring from the point of initialization of that thread.

Without an uncaught exception handler:
```java
public class App {
    public static void main(String[] args) throws Exception {
        Thread misbehavingThread = new Thread(new Runnable() {
            @Override
            public void run() {
                throw new RuntimeException("This is an uncaught exception from the misbehaving thread!");
            }
        });

        misbehavingThread.start();
    }
}
```
Output
```
Exception in thread "Thread-0" java.lang.RuntimeException: This is an uncaught exception from the misbehaving thread!
        at App$1.run(App.java:6)
        at java.base/java.lang.Thread.run(Thread.java:833)
```

With an uncaught exception handler:
```java
public class App {
    public static void main(String[] args) throws Exception {
        Thread misbehavingThread = new Thread(new Runnable() {
            @Override
            public void run() {
                throw new RuntimeException("This is an uncaught exception from the misbehaving thread!");
            }
        });

        Thread.setDefaultUncaughtExceptionHandler(new Thread.UncaughtExceptionHandler() {
            @Override
            public void uncaughtException(Thread t, Throwable e) {
                System.out.println("Uncaught exception in thread: " + t.getName());
                System.out.println("Exception message: " + e.getMessage()); // Log the exception message
                // Recovery / logging of the error can be done here
            }
        });

        misbehavingThread.start();
    }
}
```
Output
```
Uncaught exception in thread: Thread-0
Exception message: This is an uncaught exception from the misbehaving thread!
```

### Alternate way to define threads using the `Thread` class alone

Current way to define a thread is to:
1. Instantiate a `Thread` object
2. Inside the constructor, instantiate and pass another object of type `Runnable` 

Instead of the above two objects method, we can do the same with just the `Thread` class instantiation!

How?
- `Thread` class already implements the `Runnable` interface (`public class Thread implements Runnable { ... }`)
- Hence, create a class that extends the `Thread` class
- Instead of creating a new Runnable object with an overrided `run()` method, create the method within the class created above

**Note**: We can call `Thread` object methods like `getName` or `getId` directly inside the created class using **this** since it extends the `Thread` class!

```java
public class App {
    public static void main(String[] args) throws Exception {
        Thread myThread = new NewThread();
        myThread.setName("MyThread");
        myThread.start();
    }

    private static class NewThread extends Thread {
        @Override
        public void run() {
            System.out.println("Hello from " + this.getName());
            // this.getName() <=== equivalent to ===> Thread.currentThread().getName()
        }
    }
}
```
Output:
```
Hello from MyThread
```

#### Pros and Cons of the approach of extending a `Thread` class

Advantage:
1. **Greater control due to Inheritance**
    - Since you extend the base class, you can also override its methods and add new ones! (**Polymorphism**)

Disadvantage:
1. **Can only extend one class**
    - Since `Thread` is a class, if you extend it, your class cannot extend anything else (`1 class = 1 extends` rule)
    - `Runnable` is an interface. Hence, you can implement multiple interfaces in your class

**Note**: Some developers prefer to decouple the code and the threading functionality (by extending `Thread`) while others prefer to imeplement a `Runnable` (implementing an interface). There is no right or wrong answer.

Example of great control over multi-threading when using extending the `Thread` class:
- Multiple threads try to unlock a vault (One checks number-by-number ascending and another, descending)
- A "police" thread waits 10 seconds before busting the attempts and re-securing the vault
- Notice how much of the behaviour we can inherit from the base class and tweak it!

```java
import java.util.Random;
import java.util.ArrayList;
import java.util.List;

public class App {
    public static final int MAX_PASSWORD = 9999;

    public static void main(String[] args) {
        Random random = new Random();
        Vault vault = new Vault(random.nextInt(MAX_PASSWORD + 1)); // Generate a random password for the vault

        List<Thread> threads = new ArrayList<>();

        threads.add(new AscendingHackerThread(vault));
        threads.add(new DescendingHackerThread(vault));
        threads.add(new PoliceThread());

        for (Thread thread : threads) {
            thread.start(); // Start all threads
        }
    }

    /**
     * This class represents a vault that has a password. 
     * It has a method to check if a given guess is correct, 
     * which simulates a time-consuming operation by sleeping for 1 second 
     * before returning the result.
     */
    private static class Vault {
        private int password;

        public Vault(int password) {
            this.password = password;
        }

        public boolean isCorrectPassword(int guess) {
            try { // Sleep needs to be in a try-catch block because it can throw an InterruptedException
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            return this.password == guess;
        }
    }

    private static abstract class HackerThread extends Thread {
        protected Vault vault;

        public HackerThread(Vault vault) {
            this.vault = vault;
            this.setName(this.getClass().getSimpleName()); // Set the thread name to the class name for easier identification
            this.setPriority(Thread.MAX_PRIORITY);
        }

        // Override the start method to print a message when the thread starts
        @Override
        public void start() {
            System.out.println("Starting thread " + this.getName());
            super.start();
        }
    }

    // Hacker thread that will attempt to guess the password in ascending order
    private static class AscendingHackerThread extends HackerThread {
        public AscendingHackerThread(Vault vault) {
            super(vault);
        }

        @Override
        public void run() {
            for (int guess = 0; guess <= MAX_PASSWORD; guess++) {
                if (vault.isCorrectPassword(guess)) {
                    System.out.println(this.getName() + " guessed the password " + guess);
                    System.exit(0); // Exit the program when the password is guessed
                }
            }
        }
    }

    // Hacker thread that will attempt to guess the password in descending order
    private static class DescendingHackerThread extends HackerThread {
        public DescendingHackerThread(Vault vault) {
            super(vault);
        }

        @Override
        public void run() {
            for (int guess = MAX_PASSWORD; guess >= 0; guess--) {
                if (vault.isCorrectPassword(guess)) {
                    System.out.println(this.getName() + " guessed the password " + guess);
                    System.exit(0); // Exit the program when the password is guessed
                }
            }
        }
    }
    
    // Thread that will simulate the police arriving after a certain time, which will end the program
    // Note: Directly extends Thread instead of HackerThread because it does not need to interact with the vault
    private static class PoliceThread extends Thread {
        @Override
        public void run() {
            for (int i = 10; i > 0; i--) {
                try {
                    System.out.println("The police will arrive in " + i + " seconds...");
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    // Ignore for now - should not get interrupted
                }
            }

            System.out.println("Game over for you hackers - the police have arrived!");
            System.exit(0); // Exit the program when the police arrive
        }
    }
}
```

Example output:
```
Starting thread AscendingHackerThread
Starting thread DescendingHackerThread
The police will arrive in 10 seconds...
The police will arrive in 9 seconds...
The police will arrive in 8 seconds...
The police will arrive in 7 seconds...
The police will arrive in 6 seconds...
AscendingHackerThread guessed the password 3
```

## Thread termination

### Why do we want to stop threads?

Threads **consume resources**
- Memory and Kernel resources
- CPU and Cache memory

*Scenario 1*:
- If a thread has finished its work but the application is still running, we want to clean up the thread's resources

*Scenario 2*:
- If a thread is misbehaving, we want to stop it

*Scenario 3*:
- By default, the application will NOT stop as long as at least one thread is running (Even if the main thread has completed!)

### Using `Thread.interrupt()`

We can use the *static* method, **`Thread.interrupt`**, to interrupt a thread from another one.

```
Thread A (caller)           Thread B (target)
      |                            |
      |   interrupt()              |
      |--------------------------->|
      |                            |
      |                        [B is blocked
      |                         or running]
      |                            |
      |                        B notices
      |                        interrupt flag
      |                            |
      |                        → throws
      |                          InterruptedException
      |                          (if blocking)
      |                            |
```

- Thread A calls threadB.interrupt() → the JVM sets Thread B’s interrupt flag.
- When Thread B checks that flag or is in an interruptible wait/sleep/join, it wakes/throws `InterruptedException`.

#### When can we interrupt a thread?

1. If the thread is executing a mrthod that throws an `InterruptedException`
2. If the thread's code is handlingthe interrupt signal

Example when the thread has a `catch (InterruptedException e)` or equivalent in the method it currently runs:

```java
public class App {
    public static void main(String[] args) {
        Thread thread = new Thread(new BlockingTask());
        thread.start();
        thread.interrupt(); // Interrupt the thread to stop the blocking task
        // The thread handles it only if it is designed to check for interrupts, 
        // otherwise it will continue sleeping until it finishes or is interrupted again.
    }

    private static class BlockingTask implements Runnable {
        @Override
        public void run() {
            try {
                Thread.sleep(500000); // Long time to complete (500 seconds)
            } catch (InterruptedException e) {
               // Never leave the catch block empty!
               // Do something / return as otherwise it will not catch it properly.
               System.out.println("Existing blocking task...");
            }
        }
    }
}
```
Output
```
Existing blocking task...
```

Example when InterruptException is not caught: The thread needs to manually check the status of the thread i.e whether it has been implemented and take apprpriate action (Uses `Thread.currentThread().isInterrupted()`)

```java
import java.math.BigInteger;

public class App {
    public static void main(String[] args) {
        Thread thread = new Thread(new LongComputationTask(BigInteger.valueOf(20000), BigInteger.valueOf(300000)));
        thread.start();
        thread.interrupt(); // Since InterruptException is not caught inside the run method, 
        // the thread needs to manually check for interruption and handle it accordingly.
    }
    
    private static class LongComputationTask implements Runnable {
        private BigInteger base;
        private BigInteger exponent;

        public LongComputationTask(BigInteger base, BigInteger exponent) {
            this.base = base;
            this.exponent = exponent;
        }

        @Override
        public void run() {
            System.out.println(base + "^" + exponent + " = " + power(base, exponent));
        }

        private BigInteger power(BigInteger base, BigInteger exponent) {
            BigInteger result = BigInteger.ONE;
            for (BigInteger i = BigInteger.ZERO; i.compareTo(exponent) < 0; i = i.add(BigInteger.ONE)) {
                if (Thread.currentThread().isInterrupted()) {
                    System.out.println("Computation was interrupted");
                    return BigInteger.ZERO; // Return a default value or handle as needed
                }
                result = result.multiply(base);
            }
            return result;
        }
    }
}
```
Output:
```
Computation was interrupted
20000^300000 = 0
```

### Daemon threads

Deamon threads are **background threads** that *do not prevent* the applicaiton from exiting if the main thread terminates.

*Scenario 1*:
- Backgorund tasks that should not prevent our application from exiting
- Example: File saving thread in a text editor - It is okay if the main application (editor) can be closed even if a thread checking every minute if the file needs to be saved has not terminated

*Scenario 2*:
- Code in a worker thread is not under our control and we do not want it to block our application from terminating
- Example: Worker thread that uses an external library that might not handle the thread interrupt signal!
- Another example: The command `System.in.read()` to read a character from the I/O does not respond to `Thread.interrupt()`

If we do not have a daemon thread running for the above cases, we will have to forcefully kill the application at the OS level (Ex: CLI commands).

*How do we mark a thread as a Daemon?*
- Set the daemon property of the thread to `true`: **`setDaemon(true)`**

```java
import java.math.BigInteger;

public class App {
    public static void main(String[] args) {
        Thread thread = new Thread(new LongComputationTask(BigInteger.valueOf(20000), BigInteger.valueOf(300000)));
        thread.setDaemon(true); // Set the thread as a daemon thread
        thread.start();
        // Application will exit immediately after starting the thread (reaches end of execution), 
        // and the daemon thread will finish execution without blocking the application from exiting.
    }

    private static class LongComputationTask implements Runnable {
        private BigInteger base;
        private BigInteger exponent;

        public LongComputationTask(BigInteger base, BigInteger exponent) {
            this.base = base;
            this.exponent = exponent;
        }

        @Override
        public void run() {
            System.out.println(base + "^" + exponent + " = " + power(base, exponent));
        }

        private BigInteger power(BigInteger base, BigInteger exponent) {
            BigInteger result = BigInteger.ONE;
            for (BigInteger i = BigInteger.ZERO; i.compareTo(exponent) < 0; i = i.add(BigInteger.ONE)) {
                if (Thread.currentThread().isInterrupted()) {
                    System.out.println("Computation was interrupted");
                    return BigInteger.ZERO; // Return a default value or handle as needed
                }
                result = result.multiply(base);
            }
            return result;
        }
    }
}
```
Output: None. Since the main application exited without printing anything and the daemon continued executing in the background

## Joining threads & coordination

Points about threads:
1. Different threads ***run independently*** of each other
2. Order of execution outside our control (Depends on the OS scheduler)

Imagine two threads: A and B.

A might complete before B or B before A. Also, A's execution might be interleaved with B or not. We can never know as it is not in our control.

**Problem**
- What if A depends on B? How does B know A has finished? How can we control the flow appropriately?


### Naive solution of Busy Waiting

We simply add an `if` condition in one thread to check if another has finished (using the `isFinished()` method of that other thread)

Example:
```java
void waitForThreadA() {
    while(!threadA.isFinished()) {
        // BURNS CPU CYCLES! Not desirable...wasteful!
    }
}
```

Whenever B is scheduled, it takes away time away from A and on top of it, all it does during the scheduled time is wait for A to finish (***blocking and wasteful***).

### Desired solution using `join()`

Sample flow:
- Thread B checks A and goes to "sleep" completely
- Thread A does the work (finishes)
- Thread B wakes up when `join()` is invoked and gets the result from A


Without `join`:
```java
import java.util.List;
import java.math.BigInteger;
import java.util.ArrayList;
import java.util.Arrays;

public class App {
    public static void main(String[] args) {
        List<Long> inputNumbers = Arrays.asList(0L, 3435L, 35435L, 2324L, 4656L, 23L, 2435L, 5566L);

        List<FactorialThread> threads = new ArrayList<>();

        for (Long inputNumber : inputNumbers) {
            FactorialThread thread = new FactorialThread(inputNumber);
            threads.add(thread);
            thread.start();
        }

        for (int i = 0; i < inputNumbers.size(); i++) {
            FactorialThread factorialThread = threads.get(i);

            if (factorialThread.isCompleted()) {
                System.out.println("Factorial of " + inputNumbers.get(i) + " is: " + factorialThread.getResult());
            } else {
                System.out.println("Factorial of " + inputNumbers.get(i) + " is still being calculated.");
            }
        }
    }

    private static class FactorialThread extends Thread {
        private long number;
        private BigInteger result = BigInteger.ZERO;
        private boolean isCompleted = false;

        public FactorialThread(long number) {
            this.number = number;
        }

        @Override
        public void run() {
            result = factorial(number);
            isCompleted = true;
        }

        private BigInteger factorial(long n) {
            BigInteger tempResult = BigInteger.ONE;

            for (long i = n; i > 0; i--) {
                tempResult = tempResult.multiply(new BigInteger(Long.toString(i)));
            }

            return tempResult;
        }

        public boolean isCompleted() {
            return isCompleted;
        }

        public BigInteger getResult() {
            return result;
        }
    }
}
```
Output:
```
Factorial of 0 is still being calculated.
Factorial of 3435 is still being calculated.
Factorial of 23L is still being calculated.
...
...
```

Notice how the main thread has a **race condition** between thread completion (`isFinished()`) and the execution of the loop. How can we wait for ALL the results to come back in from the factorial threads before printing the result.

**With`join`:**

- Use **`join()`** method on a thread
- This waits for the thread to complete / finish i.e checking `isFinished()` will return true

(Note: `join()` invocation must be wrapped in a try-catch that is looking for a `InterruptedException` since the thread can be interrupted, else your compiler will complain.)

```java
import java.util.List;
import java.math.BigInteger;
import java.util.ArrayList;
import java.util.Arrays;

public class App {
    public static void main(String[] args) {
        List<Long> inputNumbers = Arrays.asList(0L, 3435L, 35435L, 2324L, 4656L, 23L, 2435L, 5566L);

        List<FactorialThread> threads = new ArrayList<>();

        for (Long inputNumber : inputNumbers) {
            FactorialThread thread = new FactorialThread(inputNumber);
            threads.add(thread);
            thread.start();
        }

        for (FactorialThread thread : threads) {
            try {
                thread.join(); // Once this line is reached, the main thread waits on the factorial thread
                // Until this and other threads are not complete, main thread will not execute the remainder of the program!
            } catch (InterruptedException e) { // Need to handle any interrupts!
                e.printStackTrace();
            }
        }

        for (int i = 0; i < inputNumbers.size(); i++) {
            FactorialThread factorialThread = threads.get(i);

            if (factorialThread.isCompleted()) {
                System.out.println("Factorial of " + inputNumbers.get(i) + " is: " + factorialThread.getResult());
            } else {
                System.out.println("Factorial of " + inputNumbers.get(i) + " is still being calculated.");
            }
        }
    }

    private static class FactorialThread extends Thread { /* ... */ }
}
```
Output:
```
Factorial of 0 is 1
Factorial of 23 is 2.5852017e+22
...
...
Factorial of 5566 is: 48110966871420306777610245835196137...
```

### Best practice while joining threads

What if a single thread takes a disproprtionately long time to finish?

Even if other threads send back results after finishing, the main thread in our example will have to wait indefinitely for this one particular thread to complete. What do we do?

**Solution**: Pass a timeout argument to the `join(<milliseconds>)` method. The current thread will only wait up to the timeout on that given thread before resuming execution of the remainder part of the program!

```java
import java.util.List;
import java.math.BigInteger;
import java.util.ArrayList;
import java.util.Arrays;

public class App {
    public static void main(String[] args) {
        List<Long> inputNumbers = Arrays.asList(10000000L, 3435L, 35435L, 2324L, 4656L, 23L, 2435L, 5566L);
        // Note: The first number is too big and will take a lot of time to complete
        // This will choke the main thread
        // Solution: Add a timeout using thread.join(<milliseconds>) for each factorial thread

        List<FactorialThread> threads = new ArrayList<>();

        for (Long inputNumber : inputNumbers) {
            FactorialThread thread = new FactorialThread(inputNumber);
            thread.setDaemon(true); // Set the thread as a daemon thread to allow the program to exit even if threads are still running
            threads.add(thread);
            thread.start();
        }

        for (FactorialThread thread : threads) {
            try {
                thread.join(2000); // Wait for a maximum of 2 seconds for each thread to complete
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }

        for (int i = 0; i < inputNumbers.size(); i++) {
            FactorialThread factorialThread = threads.get(i);

            if (factorialThread.isCompleted()) {
                System.out.println("Factorial of " + inputNumbers.get(i) + " is: " + factorialThread.getResult());
            } else {
                System.out.println("Factorial of " + inputNumbers.get(i) + " is still being calculated.");
            }
        }
    }

    private static class FactorialThread extends Thread {
        /* ... */
    }
}
```

In the above example, even though the first number takes a long time, if the main thread does not get blocked. It waits only for two seconds and moves on. 

However, the application will not exit unless all threads are complete. For this, you can use many approaches such as:
- Setting the thread as a daemon (background process) as in the code example above
- Sending an interrupt and handling it in the thread class / method

**Note**: Always use thread coodination, always prepare for the worst scenario and use ***defensive programming***.

## Performance in Multithreading

There are two ways to calculate performance:
1. **Latency**: The time to completions of a task. Measured in time units
2. **Throughput**: The amount of tasks completed in a given period. Measured in tasks/time unit

### Ideal latency

What is the "ideal" latency time? How can we calculate and optimize for it?

- If a single task takes `T` time, the latency is `T`.
- With multithreading, we add `N` threads to complete the entire task in `T/N` time. Hence, the ideal latency is `T/N` (i.e latency improved by a factor of `N`)

```
Time →
0                                      T

[ Thread 1 ]
+----------------------------------------+
|              Whole task                |
+----------------------------------------+
Latency = T
```

```
Time →
0             T/N                    T

[ Thread 1 ]
+-----------+
|  Part 1   |
+-----------+

[ Thread 2 ]
+-----------+
|  Part 2   |
+-----------+

[ Thread 3 ]
+-----------+
|  Part 3   |
+-----------+

        ...
[ Thread N ]
+-----------+
|  Part N   |
+-----------+

All finish around time T/N  → ideal latency = T/N
```

### Practical latency 

There are questions we need to answer before trying to achieve `T/N` latency.

Questions:
1. **What is the ideal value of `N`?**
    - How many subtasks/threads are required to break the original task?
2. **Does breaking the original task and aggregating results come for free?**
    - What is the penalty or overhead?
3. **Can we break any task into subtasks?**


Answer 1: 
- To achieve "true parallelism" or "a fully parallelized task", **we can only have as many sub-tasks as the CPU cores available to us**
    - Even adding a single additional sub-task (Ex: cores + 1 number of sub-tasks) is counter productive! 
    - The single extra thread *reduces latency* by adding context switch overhead, bad cache performance and extra memory consumption
- `#threads = #cores` is optimal **only if** all threads are runnable i.e run without interruptions such as no I/O blocking calls, sleep, etc. This is not practically possible to always limit!
    - The assumption is nothing else is running that consumes a lot of the CPU
- Partial solution to increasing the number of cores:
    - Modern computers provide **"Hyperthreading"** where one physical core can provide two or more "Virtual cores" enabling us to have more than one thread running on it (`= Number of virtual threads`). This is made possible by duplicating some of the hardware inside a CPU core. However, the core itself cannot be duplicated as a whole so while this helps, virtual threads is still not going to be fully parallel!

Answer 2:
- Creating threads has a **cost** or **overhead** to it:
    1. Operation 1: Breaking a task into subtasks
    2. Operation 2: Thread creation and passing tasks to them
    3. Operation 3: Time between thread.start() to it actually being scheduled by the OS
    4. Operation 4: Time until the last thread finishes and signals
    5. Operation 5: Time taken to aggregate all thread runs and their results
- If you plot the latency of the original task v/s the threadified one against time taken, you will find that the cost of parallelization & aggregation makes threading of simple, trivial tasks more time consuming (higher latency)!
    - There is a **threshold point** in this graph where the benefit of threading outweighs the overhead costs and the threading performs better than the original task
    - Identify this threshold and determine if your task is complex enough to cross it and give returns w.r.t latency!

```
Latency
  ^
  |                             single-thread
  |                            /
  |                          /
  |                        /
  |                      /
  |                    /
  |                  /             ___--- multithread
  |                /         ___---
  |              /     ___---
  |            / ___---
  |    ___---/--      <-- intersection (threshold: from here multithread is better)
  |__--     /  
  |      /  
  |    /  
  |  /  
  |/    
  +--------------------------------------------> Task size / complexity
 (0,0)
```

Answer 3:
- We **cannot** break every task into smaller tasks
- There are 3 types of tasks: Fully breakable into smaller tasks, non-breakable, and partially breakable
- We need to check the characteristics of a specific tasks and answer this question and take the appropriate action

### Ideal throughput

Definition: The number of tasks completed in a given period. (tasks/time unit)

**When would throughput matter?**
- When you have a program with a ***concurrent flow*** of tasks (Ex: incoming HTTP requests) and we want to ***perform as many tasks as possible, as fast as possible***

Note: Latency is related to "duration per task i.e single task", throughput is for "handling of multiple concurrent tasks"

Ideal throughput:
- If one task takes `T` time, latency is `T/1`. Throughput will be `1/T` or one task in `T` time (Inverse. Makes sense because you want to "reduce" latency and "increase" throughput)
- If we perform multithreading with `N` threads, then latency is `T/N`. Throughput will be `N/T` or N tasks within T time

```
Theoretical Throughput = N / T
```

**NOTE**: We are trying ***maximize*** throughput. Hence, the bigger the `N/T` value, the better!

### Practical throughput

In practice, throughput will be **less than** `N/T` because (less performant)

**Why?**
- The same constraints of threading overhead (creating subtasks, creating threads, waiting for them to get scheduled, etc.) apply to throughput as well
- This creates unnecessary wastage in CPU time usage

```
Practical Throughput < N / T
```

**Practical throughput is closer to ideal throughput** than practical latency is to ideal latency. How?
- Even though threading overhead costs exist, for throughput, the tasks' interdependence does not matter
- We only care about tasks in isolation for this metric (how many tasks ran in a given time - we do not care about aggregating results and producing one output etc for this metric)
- Hence, does not matter if all the sub-tasks results were not aggregated. It is not a per-task metric

#### Approaches to improve throughput 

**Thread pooling**

Creating the threads once and reusing them for future tasks instead of recreating them each and every time from scratch!
    - Once threads are created, they sit in the pool
    - Tasks are distributed among these threads through a **queue**
    - Each thread takes a task from the queue whenever that thread is available
    - If all the threads are busy, the task is just going to wait in the queue until a thread becomes available

If the threads are busy and well-utilized, and we keep feeding them tasks, we ***maximize throughput***!

Option 1: **Fixed thread pool executor**
- Use an `Executor` class
    - Comes with a built-in queue
- Invoke the method `newFixedThreadPool(numberOfThreads)` on it to initialize the pool
- Executing a thread: Create a runnable task and pass it to the executor object's `execute()` method
- Gives a significant performance boost!

```java
int numberOfThreads = 4;
Executor executor = Executor.newFixedThreadPool(numberOfThreads);

// ...

Runnable task = /* ... */;
executor.execute(task);
```

**Note**: Creating and maintaing a thread pool is **NOT** a trivial task! (Lot of complexities involved)

Example: `HttpServer` class has a provision for addign a thread pool executor
```java
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;
// ...
import java.util.concurrent.Executor;
import java.util.concurrent.Executors;

public class ThroughputHttpServer {
    private static final String INPUT_FILE = "./resources/war_and_peace.txt";
    private static final int NUMBER_OF_THREADS = 8;

    public static void main(String[] args) throws IOException {
        String text = new String(Files.readAllBytes(Paths.get(INPUT_FILE)));
        startServer(text);
    }

    public static void startServer(String text) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(8000), 0);
        server.createContext("/search", new WordCountHandler(text));

        // Create a thread pool with a fixed number of threads
        Executor executor = Executors.newFixedThreadPool(NUMBER_OF_THREADS);
        // Set the executor for the server to use the thread pool
        server.setExecutor(executor);
        // Start the server
        server.start();
    }

    private static class WordCountHandler implements HttpHandler {
        private String text;

        public WordCountHandler(String text) {
            this.text = text;
        }

        @Override
        public void handle(HttpExchange httpExchange) throws IOException {
            // ...
        }

        private long countWord(String word) {
            // ...
        }
    }
}
```

**How throughput changes with number of threads over time**:
1. From 0 to ≈ number of CPU cores: Adding threads keeps more cores busy, so throughput increases quickly (steep slope).
2. Beyond CPU cores, up to virtual-thread limit: More threads mostly add scheduling/coordination overhead; throughput still rises but slowly, because the same cores are just time-slicing more threads.
3. Near the virtual-thread limit: Extra threads add almost only overhead, so throughput plateaus (no real gain).

```
Throughput
   ^
   |            
   |           
   |          
   |         
   |        
   |                _ - - -  ← plateau
   |            __/
   |        __/
   |    __/
   |   /
   |  /
   | /  ← steep (up to CPU cores)
   |/
   +-----------------------> Threads
        ^           ^
        |           |
     cores      vthreads
```

## Data sharing between threads

**What is a stack?**
- It (call stack) is a memory region where methods are called, arguments are passed and local variables are stored
- `Stack + instruction pointer = state of each thread's execution`

You may run an application with methods that invoke other methods in debug mode and check the changing call stack in your IDE at different points of execution.

Stack properties:
1. All variables belong to the thread executing on the stack
2. Statically allocated when the thread is created
3. Stack's size is fixed and relatively small
4. If our calling hierarchy is too deep, we may get a `StackOverflow` exception (Risky with recursive calls)

**What is a heap?**
- It is a memory region where any object created with `new` is located (String, Object, Collection, ...)
- Also stores members of classes
- "Static variables" are also stored on the heap
- **Important!**: The heap is governed and managed by the **Garbage Collector**
    1. "Objects" stay as long as we have a reference to them
    2. "Members of classes" exist as long as their parent objects exist (same lifecyle as their parents)
    3. "Static variables" stay forever

**References to objects**
- They are allocated on the call stack for their method
- However, they can be allocated on the heap too if they are members of a class (see above section)
- ***Objects*** themselves are ***always*** located on the heap!

Examples:

1. Local variable (on stack)
```java
void doSomething() {
    int x = 10;  // local variable
}
```
x value (10) is stored in the stack frame of doSomething (**stack**).

2. Class member / instance variable (on heap)
```java
class Person {
    int age;      // instance (class member) variable
}
```
For `Person p = new Person();`, the age field is stored inside the Person object on the **heap**.

3. Static variable (method area / heap region)
```java
class Config {
    static int maxUsers = 100;  // static variable
}
```
`maxUsers` belongs to the class, stored in the JVM’s method area (often treated as part of **heap** space)

4. Object reference (reference on stack, object on heap)
```java
void create() {
    Person p = new Person();  // p is a reference
}
```
- `p` (the reference variable) is in the **stack** frame of create.
- The actual Person object that `p` points to is on the **heap**.

### Why would threads want to share data?

Threads can share objects, class members, and static variables but not local primitives and local references.

There are many use cases to share data:
1. UI thread and thread to save a document editor sharing the data structure that holds the file being edited
2. A work dispatcher thread placing a task in a queue for multiple worker threads to pick up for procssing - the queue is the shared resource
3. Multiple request threads handle writing data to a database. The DB is the shared resource

### Problem with a simple resource sharing approach

An example of problems caused by respource sharing 
- Inconsistent edits
- No synchronization

Example: Using two threads to add and remove item counts from an inventory class
```java
public class App {
    // This code demonstrates a race condition where multiple threads are incrementing the same counter without proper synchronization.
    public static void main(String[] args) throws InterruptedException {
        InventoryCounter inventoryCounter = new InventoryCounter(); 
        Thread incrementThread = new IncrementThread(inventoryCounter);
        Thread decrementThread = new DecrementThread(inventoryCounter);

        // Start both threads to increment the counter concurrently
        incrementThread.start();
        decrementThread.start();

        // Wait for both threads to finish before printing the final count
        incrementThread.join();
        decrementThread.join();

        // Print the final count, which may not be 20000 due to the race condition!
        // This is happening because both threads are modifying the same counter variable without any synchronization mechanism, leading to a race condition.
        System.out.println("Final count: " + inventoryCounter.getCount());
    }

    private static class InventoryCounter {
        private int count = 0;

        public void increment() {
            count++;
        }

        public void decrement() {
            count--;
        }

        public int getCount() {
            return count;
        }
    }

    private static class DecrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public DecrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.decrement();
            }
        }
    }

    private static class IncrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public IncrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.increment();
            }
        }
    }
}
```
Potential outputs: (See! It is inconsistent)
```
Run 1: 
Final count: -501

Run 2:
Final count: -88

Run 3:
Final count: 0
```

This is happening because both threads are modifying the same counter variable without any synchronization mechanism, leading to a race condition.

**Hmmmm...**
- **BUT**, if both update it i.e increment from 0 to 10000 and the other decrement from 10000 to 0 then irrespective of the race condition, the value must end up being 0 still, right?

**The gotcha!...**
- The reason we get different results is the **ATOMIC** operation for an OS is an "instruction" (think assembly/machine language instruction). For the OS, `count++` or `count--` are NOT atomic operations
- The way `count++` might be split into atomic operations for the OS is:
```
1. Read current value as the count value
2. Create a new value (temp) to count + 1
3. Update count to temp
```
- The way `count--` might be split into atomic operations for the OS is:
```
1. Read current value as the count value
2. Create a new value (temp) to count - 1
3. Update count to temp
```

An **atomic operation** (at the OS level) is an operation that runs as one indivisible step, so no other process or thread can see or modify its intermediate state.

So, here is what *might* happen when two threads try to `count++` and `count--` concurrently:
```
count = 0
IncrementThread scheduled:
    reads current count as 0
    temp = current count + 1 = 1

*Interrupt* OS schedules DecrementThread instead
    read current count as 0
    temp = current count - 1 = -1
    count = temp = -1

DecrementThread finished, IncrementThread rescheduled:
    count = temp = 1

Done.

---   

In the end, count is 1 in this sample run instead of 0 (expected)
```

**Non-atomic operations** like the one above form the challenges of **multi-threaded programming**!

## Concurrency challenges

When does a concurrency problem occur? It occurs when:
1. Two threads perform operations on the same resource 
2. Both threads are reading and modifying the resource at the same time
3. The operations are **not** atomic

Therefore, even though at the OS level, these are not atomic operations, we need to make it atomic

Example: Assume this is our set of operations for a task
```java
void aggregateFunction() {
    op1();
    op2();
    op3();
}
```

How do we make it atomic? We need a **lock** on this set of operations.
- To make this happen, we have a special instruction to indicate a block of code as a **critical section**
```java
void aggregateFunction() {
    /* ENTER CRITICAL SECTION */
    op1();
    op2();
    op3();
    /* EXIT CRITICAL SECTION */
}
```

Points to note:
1. When one thread enters a critical section, another thread cannot enter it at the same time
2. If one thread leaves a critical section, another thread can enter it

This mechanism is known as a **synchronized monitor** / **lock**. Different languages implement the same concept in different ways (syntax/constructs)

### Synchronization in Java 

There are two ways to make this happen:

1. Add **`synchronized`** to the method signatures
    - Whenever we tag a method as synchronized, the lock is, in fact on the whole object of the class!
    - **Important**: If there are multiple methods tagged as synchronized, if one thread has entered even one of them, no other thread can enter any of the synchronized methods too! (Why: Because the lock is on the object itself!)
    - If a method is not marked as synchronized though, any thread can enter it any time

Examples:
```java
public class ClassWithCriticalSections {
    public synchronized void method1() {
        /* ... */
    }

    public synchronized void method2() {
        /* ... */
    }
} 
```
If `Thread A` has entered `method1()` then another thread, `Thread B`, can neither enter `method1()` nor `method2()` until `Thread A` leaves!

Example:
```java
public class ClassWithCriticalSections {
    public synchronized void method1() {
        /* ... */
    }

    public synchronized void method2() {
        /* ... */
    }

    public void method3() {
        /* ... */
    }
} 
```
If `Thread A` has entered `method1()` then another thread, `Thread B`, cannot enter `method1()` or `method2()`, but it can enter `method3()` since there is no lock on it

Practical example:
```java
public class App {
    // This code demonstrates a race condition where multiple threads are incrementing the same counter without proper synchronization.
    public static void main(String[] args) throws InterruptedException {
        InventoryCounter inventoryCounter = new InventoryCounter(); 
        Thread incrementThread = new IncrementThread(inventoryCounter);
        Thread decrementThread = new DecrementThread(inventoryCounter);

        // Start both threads to increment the counter concurrently
        incrementThread.start();
        decrementThread.start();

        // Wait for both threads to finish before printing the final count
        incrementThread.join();
        decrementThread.join();

        // Print the final count, which may not be 0 due to the race condition!
        // This is happening because both threads are modifying the same counter variable without any synchronization mechanism, leading to a race condition.
        System.out.println("Final count: " + inventoryCounter.getCount());
    }

    private static class InventoryCounter {
        private int count = 0;

        public synchronized void increment() {
            count++;
        }

        public synchronized void decrement() {
            count--;
        }

        public int getCount() {
            return count;
        }
    }

    private static class DecrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public DecrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.decrement();
            }
        }
    }

    private static class IncrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public IncrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.increment();
            }
        }
    }
}
```
Output:
```
Final count: 0
```

1. Add a custom **`synchronized`** lock block within a method
    - Create a new object (or use an existing one)
    - Within your method, create a **`syncrhonized (<object>) { ... }`** block
    - Place all the critical operations within this block
    - **Note**: The object we place the lock on need not be the object we are operating on inside the block

Example:
```java
public class ClassWithCriticalSections {
    Object lockingObject1 = new Object(); // Can be any object (not just of Object type)
    Object lockingObject2 = new Object(); // Can be any object (not just of Object type)
    
    public void method1() {
        synchronized(lockingObject1) {
            // ...
        }
    }

    public synchronized method2() {
        synchronized(lockingObject2) {
            // ...
        }
    }
}
```
If `Thread A` has entered the synchronized section in `method1()` then another thread, `Thread B`, cannot enter the same section in `method1()`, but it can enter a synchronized section in `method2()` since it depends on another lock object, `lockingObject2` (Assuming it is not held by another thread).

This way of locking is **better**! Why?
1. You can choose to lock a smaller section of code than a whole method! (***Smaller the critical section, the better for resource sharing and performance***)
2. Even the "synchronized method" way of locking is nothing but a specialized form of locking based on objects
    - It is as good as locking on the **`this`** object: `synchronized (this) { ... }`
        - That is why synchronized methods are all locked together (as they are all locked due to the `this` object)

Practical example:
```java
public class App {
    // This code demonstrates a race condition where multiple threads are incrementing the same counter without proper synchronization.
    public static void main(String[] args) throws InterruptedException {
        InventoryCounter inventoryCounter = new InventoryCounter(); 
        Thread incrementThread = new IncrementThread(inventoryCounter);
        Thread decrementThread = new DecrementThread(inventoryCounter);

        // Start both threads to increment the counter concurrently
        incrementThread.start();
        decrementThread.start();

        // Wait for both threads to finish before printing the final count
        incrementThread.join();
        decrementThread.join();

        // Final count will always be 0 due to the 'synchronize' used correctly
        System.out.println("Final count: " + inventoryCounter.getCount());
    }

    private static class InventoryCounter {
        private int count = 0;
        private Object lock = new Object();
        
        public synchronized void increment() {
            synchronized (lock) {
                count++;
            }
        }

        public synchronized void decrement() {
            synchronized (lock) {
                count--;
            }
        }

        public int getCount() {
            return count;
        }
    }

    private static class DecrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public DecrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.decrement();
            }
        }
    }

    private static class IncrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public IncrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.increment();
            }
        }
    }
}
```
Output:
```
Final count: 0
```

#### What happens to a thread unable to acquire a lock?

All the threads waiting to acquire a lock not freed up by a particular thread:
1. Get suspended (execution paused)
2. Wake up only when the lock is released!

(**Note**: Calling the interrupt method on a thread (`blockingThread.interrupt()`) from another thread to free up a lock held by it ***does not work*** in the case of a `synchronized` lock)

#### Reentrant locking

The **`synchronized`** tool is known as a "reentrant lock". 

A reentrant lock is a lock that the same thread can acquire multiple times without blocking on itself, as long as it eventually releases it the same number of times.

Essentially, it means that the same thread can enter a critical section once again while it is inside the first critical in that section. *Corollary*: A thread cannot prevent itself from entering a critical section

How it works:
- If Thread A enters a synchronized method on object obj, it acquires obj’s monitor lock.
- If, inside that method, Thread A calls another synchronized method on the same object obj, it is allowed to enter again without getting stuck; the JVM increases an internal hold count.
- Only when Thread A exits all those synchronized sections (matching number of exits) is the lock fully released and another thread can enter.

Example:
```java
class Demo {
    synchronized void a() {
        // Thread A gets the lock on "this"
        b();  // also synchronized on "this"
    }

    synchronized void b() {
        // Thread A can enter here too, reusing the same lock
    }
}
```
Here, a() calls b(), both are synchronized on the same object (`this`), and the same thread can enter both — that’s exactly what “reentrant” means.

### When to synchronize?

- Using a lot of Synchronized method or blocks will be worse than running a single thread
    - Most threads will simply wait on resources (sequential thread)
    - Whenever they get the entry, scheduler overhead to context switch actually makes it worse than single threaded
- **Lock only the most critical resources**
    - Smaller concurrent section, the better

## The `volatile` keyword

**What are the atomic operations in Java (and the OS)?**

1. Methods marked as synchronized (`synchronized`)
2. References to objects: We can "get" and "set" object references atomically
    - Ex: `Object a = new Object(); // atomic`
    - Ex: `Object b = a; // atomic`
    - Ex: `public void setName(String name) { this.name = name }; // atomic`
    - Ex: `public int[] getAges() { return this.ages; } // int[] is an array i.e an object. Hence, atomic`
        - Same with Strings (getting and setting them is atomic as they are objects)
3. Assignment to the following primitives: `int`, `short`, `byte`, `float`, `boolean`, `char`

**What are NOT atomic operations in Java (and the OS)?**

1. Reading and writing 64-bit+ primitives: **`long`** and **`double`**
    - Why? Every atomic operation works on 32-bits. Long and double set/get take 2 instructions to get done
2. Any other operations that are not listed in the set of atomic operations above (Ex: Different arithmetic operations / computations / multi-step Java statements, incrementing a counter (like `count++`), and so on)

How to make `long` and `double` getters/setters atomic?
- Use the **`volatile`** keyword

Example:
```java
volatile double x = 1.0;
volatile double y = 2.0;

x = y; // Atomic now!
```

Note: Java has a whole set of other classes based on the principles above to make lock-free concurrency possible. `java.util.concurrency.atomic`. More advanced (Discussed later)

Practical example:
```java
import java.util.Random;

public class App {
    public static void main(String[] args) {
        Metrics metrics = new Metrics();
        MetricsPrinter printer = new MetricsPrinter(metrics);
        BusinessLogic logic1 = new BusinessLogic(metrics);
        BusinessLogic logic2 = new BusinessLogic(metrics);

        logic1.start();
        logic2.start();
        printer.start();
    }

    public static class MetricsPrinter extends Thread {
        private Metrics metrics;

        public MetricsPrinter(Metrics metrics) {
            this.metrics = metrics;
        }

        @Override
        public void run() {
            while (true) {
                try {
                    Thread.sleep(100); // Print metrics every second
                } catch (InterruptedException e) {}

                System.out.println("Current average is: " + metrics.getAverage() + " ms");
            }
        }
    }

    public static class BusinessLogic extends Thread {
        private Metrics metrics;
        private Random random = new Random();

        public BusinessLogic(Metrics metrics) {
            this.metrics = metrics;
        }

        @Override
        public void run() {
            while (true) {
                long start = System.currentTimeMillis();
                
                try {
                    Thread.sleep(random.nextInt(10)); // Simulate time-consuming task
                } catch (InterruptedException e) {}

                long end = System.currentTimeMillis();
                metrics.addSample(end - start);
            }
        }
    }

    // Our whole Metrics class operations are about maintaining a count and an average.
    // The count is only modified within the addSample method, which is synchronized, so it is thread-safe.
    // The average is updated in the addSample method, which is also synchronized, ensuring that updates to the average are thread-safe.
    // The getAverage method simply returns the current average, which is declared as volatile, 
    // ensuring that it can be safely read by multiple threads without synchronization.
    public static class Metrics {
        private long count = 0;

        // Double in the getter is now volatile, so it can be safely read without synchronization
        private volatile double average = 0.0; 

        // Method does a lot of non-atomic things. Hence, needs to be synchronized to prevent race conditions
        public synchronized void addSample(double value) {
            double currentSum = average * count;
            count++;
            average = (currentSum + value) / count;
        }

        public double getAverage() {
            return average; 
        }
    }
}
```

## Data race 

There are two types of issues with managing shared resources
1. **Race condition**
2. **Data race**

Race condition: This is what we have seen so far. 
- `count++` and `count--` are "non-atomic" operations on the ***same item/resource*** (assume the operations are not synchronized)
- If multiple threads perform such an operation simultaneously *without synchronization*, it leads to inconsistent/inaccurate results

**Data race**: This is another type of concurrency where:
- Multiple threads are acting "non-atomically" on ***two different resources*** at the ***same time*** 
- However, it still leads to inconsistencies in fetching results.

Explanation: Consider this class with two member variables, x & y:
```java
public class SharedClass {
    int x = 0;
    int y = 0;

    public void increment() {
        x++;
        y++;
    }

    public void print() {
        if (y > x) {
            System.out.println("x: " + x + ", y: " + y);
        }
    }
}
```

We assume that: Since x is always incremented before y in `increment()`, `y` can never be greater than `x` while printing. 

Let us say multiple threads invoke `increment()` and `print()` concurrently and they are even scheduled and interleaved. 
But logically, x will always be either the same as y or greater.

**CPU optimization**
- The logic above **FAILS**! 
- Why? Compiler and CPU "instructions re-arrangement" is a whole other level of optimization that happens internally in the OS
- ***Unrelated / independent operations can happen in any order!!***
- This CPU optimization makes the execution faster, so it is a good thing, and not to be changed!
    - Reasons: Vectorization (SIMD), Prefetching instructions, better cache performance, etc.

Example: Independent operations (order not maintained)
```java
int x = 0;
int y = 0;

x++;
y++; 

// CPU might perform y++ before x++ since they are independent operations
```
That is, there is no guarantee that `x++` will run before `y++`.

Example: Dependent operations (order maintained)
```java
int a = 0;

int x = a + 1; // CPU can never execute this before `int a = 0;`
int y = x + 2; // CPU can never execute this before `int x = a + 1;`
```

### Avoiding a data race

- Option 1: `synchronized` method or block that modifies a shared variable
- Option 2: Declaring a shared variable as `volatile` 

These are the *same* two options used for "Race-conditions" but they work for a "Data race" too!

Visualizing volatile for "Data race":
```sh
volatile int sharedVar;

public void method() {
    // ... All instructions will be executed before
    read/write(sharedVar);
    // ... All instructions will be executed after
}
```

Practical example:
```java
import java.util.Random;

public class App {
    public static void main(String[] args) {
        SharedClass sharedClass = new SharedClass();

        Thread thread1 = new Thread(() -> {
            for (int i = 0; i < Integer.MAX_VALUE; i++) {
                sharedClass.increment();
            }
        });
        Thread thread2 = new Thread(() -> {
            for (int i = 0; i < Integer.MAX_VALUE; i++) {
                sharedClass.checkForDataRace();
            }
        });

        thread1.start();
        thread2.start();
    }

    public static class SharedClass {
        private volatile int x = 0;
        private volatile int y = 0;

        public void increment() {
            x++;
            y++;
        }

        public void checkForDataRace() {
            if (y > x) {
                // This can never execute because x and y are declared as volatile
                // Volatile on x:
                // Makes sure all operatins before x++ execute before x++ and all operations after x++ execute after x++ even on the CPU
                // Volatile on y:
                // Makes sure all operatins before y++ execute before y++ and all operations after y++ execute after y++ even on the CPU
                System.out.println("x: " + x + ", y: " + y);
            }
        }
    }
}
```
Output: None.

Notice that even though the data type is an `int` which can be assigned (set/update) and read atomically in Java, the "Data race" problem makes us still mark it as "volatile".
 
## Locking strategies and deadlock

When you have multiple shared resources , you can choose a strategy for locking them:
1. **Coarse-grained locking**: One big lock on all the resources (Ex: adding `synchronized` on ALL or most class methods)
    - Less control, more high-level / blanket locking in some cases
    - Bad for performance as threads cannot do much while waiting for critical sections to become available
2. **Fine-grained locking**: Use smaller locks only in places where it is needed (Ex: synchronized blocks, volatile, etc)
    - More control and flexible
    - Beware of using it everywhere on all variables, sections and objects
    - Good for performance when done well

There is no one good / one bad approach. It depends on the specifics. You need to make a choice for your app / code.

### Deadlock

Deadlock is a situation where two or more threads/processes are stuck forever because each is waiting for a resource or lock held by another, so none of them can continue!

Example: Thread 1 getting locks on two lists, A & B
```
lock(A)
lock(B)
delete(A, item)
add(B, item)
unlock(B)
unlock(A)
```

Example: Thread 2 getting locks on two lists, A & B
```
lock(B)
lock(A)
delete(B, item)
add(A, item)
unlock(A)
unlock(B)
```

Now, consider this execution order:
```
thread 1:           Thread 2:
1. lock(A)
                    2. lock(B)
                    3. lock(A)
3. lock(B) !! Deadlock !! A cannot acquire a lock on B as thread 2 holds it
                          B cannot acquire a lock on A as thread 1 holds it
```

Code example:
```java
import java.util.Random;

public class App {
    public static void main(String[] args) {
        Intersection intersection = new Intersection();
        Thread trainAThread = new Thread(new TrainA(intersection));
        Thread trainBThread = new Thread(new TrainB(intersection));

        trainAThread.setName("trainAThread");
        trainBThread.setName("trainBThread");

        trainAThread.start();
        trainBThread.start();
    }

    public static class TrainA extends Thread {
        private Intersection intersection;

        public TrainA(Intersection intersection) {
            this.intersection = intersection;
        }

        @Override
        public void run() {
            while (true) {
                long sleepTime = new Random().nextInt(1000);
                try {
                    Thread.sleep(sleepTime); // Simulate time taken to approach the intersection
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }

                intersection.takeRoadA(); // Attempt to take road A
            }
        }
    }

    public static class TrainB extends Thread {
        private Intersection intersection;

        public TrainB(Intersection intersection) {
            this.intersection = intersection;
        }

        @Override
        public void run() {
            while (true) {
                long sleepTime = new Random().nextInt(1000);
                try {
                    Thread.sleep(sleepTime); // Simulate time taken to approach the intersection
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }

                intersection.takeRoadB(); // Attempt to take road B
            }
        }
    }

    // An intersection with two roads, A and B. 
    // Trains can only cross the intersection if they have locked both roads.
    public static class Intersection {
        private Object roadA = new Object();
        private Object roadB = new Object();

        public void takeRoadA() {
            synchronized (roadA) {
                System.out.println("Road A is locked by " + Thread.currentThread().getName());
                
                synchronized (roadB) {
                    System.out.println("Train is passing through road A");
                    try {
                        Thread.sleep(new Random().nextInt(5000)); // Simulate time taken to pass through
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                }
            }
        }

        public void takeRoadB() {
            synchronized (roadB) {
                System.out.println("Road A is locked by " + Thread.currentThread().getName());

                synchronized (roadA) {
                    System.out.println("Train is passing through road B");
                    try {
                        Thread.sleep(new Random().nextInt(5000)); // Simulate time taken to pass through
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                }
            }
        }
    }
}
```
Output: At some point both the threads must be locked on each other!

#### Conditions for a deadlock:
1. *Mutual exclusion*: Only one thread can have exclusive access to a resource
2. *Hold and wait*: At least one thread is holding a resource and is waiting for another resource
3. *Non-preemptive allocation*: A resource is released only after the thread is done using it
4. *Circular wait*: A chain of at least two threads with each one holding one resource and waiting for another resource

#### Solutions for removing a deadlock
1. **Avoid circular wait**: Enforce a strict order in lock acquisition (All the locks must be acquired in the same order by every thread)

Example:
```java
// ...
public void takeRoadA() {
    synchronized (roadA) {
        // ...
        synchronized (roadB) {
            // ...
        }
    }
}

// ...

public void takeRoadB() {
    synchronized (roadA) { // Changed from earlier lock on B to A to maintain the same order
        // ...
        synchronized (roadB) { // Changed from earlier lock on B to A to maintain the same order
            // ...
        }
    }
}
```

2. Watchdog - deadlock detection (Advanced concept)
3. Thread interruption - Not possible with `synchronized` in Java
4. "tryLock" operations - Not possible with `synchronized` in Java

## Advanced locking

Let us refresh our memory on what happens to a thread unable to acquire a lock because of another thread holding it:
- All the threads waiting to acquire a lock not freed up by a particular thread:
    1. Get suspended (execution paused)
    2. Wake up only when the lock is released!

(**Note**: Calling the interrupt method on a thread (`blockingThread.interrupt()`) from another thread to free up a lock held by it ***does not work*** in the case of a `synchronized` lock)

### ReentrantLock

**ReentrantLock**: A reentrant lock from `java.util.concurrent.locks` that you manage manually with lock()/unlock() and that offers extra features like tryLock, fairness, and interruptible/timed locking.

- It works just like the `synchronized` keyword applied on an "object" (not applied on methods). However, it requires **explicit** *locking* and *unlocking*
- Also, we cannot lock on any object, we need to use an object of the class `ReentrantLock` only!
- It provides *at least* a `lock()` and an `unlock()` method to explicity choose when to lock/unlock

```java
import java.util.concurrent.locks.ReentrantLock; // Needs to be imported, unlike synchronized

class MyClass {
    private final ReentrantLock lock = new ReentrantLock();
}
```

**TL;DR**
- More control, advanced features

Example:
```java
Lock lockObject = new ReentrantLock();
Resource resource = new Resource();

// ...

public void method() {
    lockObject.lock();
    // ...
    // use(resource);
    // ...
    lockObject.unlock();
}
```

**Problems with the lock mechanism of Reentrant locks**:
1. If the method returns before unlocking, the lock is maintained forever
```java
public void method() {
    lockObject.lock();
    // ...
    return; 
    // Below code never runs; lock is never freed! (x)
    lockObject.unlock();
}
```

2. Even if we unlock before returning, a runtime exception (Ex: `throw`) might occur and lock is never freed!
```java
public void method() {
    lockObject.lock();
    // ...
    throwExceptionMethod(); 
    // Below code never runs; lock is never freed! (x)
    lockObject.unlock();
}
```

**Solution**: `lock()` *before* a `try`, wrap critical operation in a `try` block, and the `unlock()` in a `finally`.
- In this way, the lock is always freed, irrespective of whether we return early or throw an exception inside the method!
- Why `lock()` *before* the try block? Because if the lock cannot be acquired, thread simply pauses, there is no error. But, the critical block of code may error out.

```java
public void method() {
    lockObject.lock();
    try {
        someOperations();
        return value;
    } finally {
        // Below code always runs; lock is always freed!
        lockObject.unlock();
    }
}
```

### Query methods for testing ReentrantLock

1.`getQueuedThreads()`: Returns a list of threads waiting to acquire a lock
2. `getOwner()`: Returns the thread that currently owns the lock
3. `isHeldByCurrentThread()`: Queries if the lock is held by the current thread
4. `isLocked()`: Queries if the lock is held by any thread

### Lock fairness

A ReentrantLock takes in an optional argument which, if `true`, ensures fairness in providing locks to threads. Typically the OS schedules threads and some threads may unfairly suffer i.e too much delay. This lock option tries to change the priorities to ensure fairness.

```java
ReentrantLock lock = new ReentrantLock(true);
```

It tries to avoid deadlocks and starvations but could, in fact, lead to longer wait times i.e backfire! (Reduced "throughput" of app)

Use it sparingly! Only if absolutely necessary.

### Locking interruptibly

Synchronized locks (the default) go into a suspended state if the lock it is trying to acquire is not free. We cannot even interrupt the thread with the lock to free it

- Reentrant locks provide a `lockInterruptibly()` method to be able to interrupt a thread in order to acquire it
- The code is forced to have a try-catch on the lock invocation in order to listen for `InterruptedException`s

```java
@Override
public void run() {
    while (true) {
        try {
            lockObject.lockInterruptibly();
            // ...
        } catch (InterruptedException e) { // Ends up here after `someThread.interrupt()`
            cleanUpAndExit(); 
        }
    }
}
```

### The try lock

A synchronized lock always makes the thread wait (suspended) on fetching the lock - either immediately or wake up when freed 

A Reentrant lock can help us acquire a `tryLock()` in case we want to conditionally perform actions without waiting on always acquiring a lock. **This is one of the most important use cases of a ReentrantLock**

How it works:
1. Returns `true` if lock was successfully acquired
2. Returns `false` if lock could not be acquired

**Note**: The `tryLock()` method is **never blocking** unlike the other lock methods

Why does this matter? **Real-time applications** where suspending a thread on a `lock()` method is **unacceptable**
- Video/Image playback or processing applications cannot suspend threads and must move on to other tasks to keep the playback or processing running
- High speed / low latency trading systems
- User Interface applications

Example:
```java
// ...
if (lockObject.tryLock()) {
    try {
        useResource(); // critical operation
    }
    finally {
        lockObject.unlock();
    }
} else {
    /* ... Do something else ... */
}
// ...
```

### Reentrant Read Write lock

Until now, we have seen only one type of lock: A lock of "total mutual exclusion"

What does this mean?
- Mutliple threads share a resource with at least one thread modifying it
- If any thread acquires a lock, it is a complete lock i.e no other thread can gain entry until lock is released
- It does not matter if our use case for each thread is a read or a write (operation agnostic)

This is fine for most use cases (`synchronized` and `ReentrantLock`) but is sub-optimal for a few (explained below).

Imagine a DB / Cache with:
1. One writer thread writing to it
2. Multiple reader threads reading from it

Whenever we write, we don't want to read inconsistent data. But whenever we only read, should all other readers be blocked? When readers are more, this could lead to slow performance and unnecessary locking and data is remaining the same and not corrupted by the threads!

Hence, in such a case we use a **`ReentrantReadWritelock`**.

It is best used when:
1. Read operations are ***predominant*** (OR)
2. Read operations are ***not as fast*** (OR)
3. Mutual exclusion of reading threads ***negatively impacts the performance***

**`ReentrantReadWritelock`** can be used as follows:
- It is not a lock by itself (unlike other lock types). It provides an object when instantiated
- The object has two methods, `readLock()` and `writeLock()`

Use the `writeLock()` for lock on shared resource modification, and `readLock` for lock on shared resource reads.

**Rules**:
1. `writeLock`: Only a single thread is allowed to lock a write lock
2. `readLock`: Multiple threads can acquire the read lock

**Benefits**:
1. If a `writeLock` is acquired, no thread can acquire a `readLock`
    - So that data is not read while being updated, preventing inconsistent/corrupt reads
2. If at least one thread holds a `readLock`, no thread can acquire a `writeLock`
    - So that as long as someone is reading the data, no one can modify it, preventing inconsistent/corrupt reads

```java
ReentrantReadWriteLock rwLock = new ReentrantReadWriteLock();
Lock readLock = rwLock.readLock();
Lock writeLock = rwLock.writeLock()
```

Write locking example:
```java
writeLock.lock();
try {
    modifySharedResource();
} finally {
    writeLock.unlock();
}
```

Read locking example:
```java
readLock.lock();
try {
    readFromSharedResources();
} finally {
    readLock.unlock();
}
```

**Note**: `ReentrantReadWriteLock` is not always better than a conventional lock. Use the right tool for the job.

## Semaphore

Semaphore is a **thread synchronization tool**.

It can be used for:
- Restrict the number of "users" to a particular resource or a group of resources
    - This is unlike the *locks* that allows "one user" per resource

The semaphore can restrict any given number of users to a resource!

### Analogy to understand semaphore

Think of a semaphore as the gate system for a ***parking lot with limited spots***.

Simple analogy
The semaphore value = number of free parking spots.

Each car = a thread.

The parking lot = the shared resource.

```java
          +----------------------+
          |   Parking Lot (3)    |
          |  [ ]  [ ]  [ ]       |  ← 3 free spots = semaphore = 3
          +----------^-----------+
                     |
        acquire()    |    release()
      (try to park)  |   (leave spot)
                     v

Cars (threads):

   Car A -----> tries to enter
   Car B -----> tries to enter
   Car C -----> tries to enter
   Car D -----> tries to enter
                 |
                 v

State as they arrive:

Semaphore = 3  → Car A enters, spots = 2
Semaphore = 2  → Car B enters, spots = 1
Semaphore = 1  → Car C enters, spots = 0
Semaphore = 0  → Car D must WAIT outside
                  (blocked until a spot frees)

When any car leaves:
  spots++  → semaphore++  → one waiting car can enter
```

In words:
- Each arriving car takes 1 permit (decrements the semaphore) if a spot is free; otherwise it waits.
- Each leaving car returns 1 permit (increments the semaphore), letting a waiting car proceed.

### Semaphore basic usage

Example:
```java
Semaphore semaphore = new Semaphore(NUMBER_OF_PERMITS);
semaphore.acquire(5); // NUMBER_OF_PERMITS - 5 now available
// ...
useResource();
// ...
semaphore.acquire(5); // NUMBER_OF_PERMITS now available
```

Example 2:
```java
Semaphore semaphore = new Semaphore(NUMBER_OF_PERMITS);
semaphore.acquire(NUMBER_OF_PERMITS); // 0 now available
// ...
// ...
semaphore.acquire(); // 0 permits available -> THREAD BLOCKED! -> GOES TO SLEEP!
```

### Binary semaphore

It is a semaphore initialized with `1` (which is the default if an argument is not passed).

- A binary semaphore is like a flag that can be either 0 or 1, used to control access to something shared.
- It is usually initialized to 1, meaning “resource is free; one thread can enter.”

This type of sempahore is **not** a **Re-entrant** i.e the thread cannot acquire a semaphore it already has!
- If a thread already holds the semaphore (it successfully did `acquire()`), and it tries to `acquire()` again without `release()` in between, it will block on itself.
- The semaphore does not “remember” which thread owns it; it only knows “free (1)” or “taken (0)”.

When a thread calls `acquire()`:
1. If the value is `1`, it becomes `0` and the thread continues (it “takes” the resource).
2. If the value is `0`, the thread blocks and goes to sleep until someone else releases it.
3. When a thread calls `release()`, the value goes from `0` back to `1` and wakes one waiting thread, if any.

```java
void function1() {
    semaphore.acquire(); // A binary semaphore 
    semaphore.acquire(); // THREAD BLOCKED! -> GOES TO SLEEP! (cannot acquire acquire a lock it already has)
}
```

### Semaphores make horrible locks!

Reasons:
1. Semaphore does not have a concept of an owner thread
2. **Important**: Many threads can acquire a permit!
3. **Important**:The same thread can acquire the semaphore multiple times!

Main difference: **A semaphore can be released by *any* thread**

```
thread 1:               thread 2:
---------               ---------
sem.acquire()
                        sem.release() // Any thread can release a semaphore!
useShareResource()
                        sem.acquire() // Works! (Allowed) POSSIBLE since we were able to release the sem
                        useShareResource() // As you can see, a sem is not a good lock!
                        sem.release()
sem.release()
```

Then what is a semaphore used for?
1. Inter-thread communication
2. Maintaining a healthy Producer-Consumer flow 

### Semaphores are used for the producer-consumer pattern

```java
Semaphore full = new Semaphore(0);  // how many items are available
Semaphore empty = new Semaphore(1); // how many empty slots are available
Item item = null;

// Producer
while (true) {
    empty.acquire();            // wait if there is NO empty slot
    item = produceNewItem();    // put item into the (single) slot
    full.release();             // signal: one item is now available
}

// Consumer
while (true) {
    full.acquire();             // wait if there is NO item
    consume(item);              // take/use the item from the slot
    empty.release();            // signal: slot is now empty again
}
```

Producer workflow:
1. The producer waits for an empty slot, puts a new item, then signals that an item is available.
    - `empty.acquire()` → “Is there space?” If not, wait.
2. `item = produceNewItem()` → actually create and place the item.
3. `full.release()` → “Hey consumer, there is now one item for you.”

Consumer workflow:
1. The consumer waits for an available item, takes/uses it, then signals that the slot is free again.
    - `full.acquire()` → “Is there an item?” If not, wait. (i.e suspended / blocked)
2. `consume(item)` → actually use the item produced.
3. `empty.release()` → “Hey producer, the space is empty again, you can put another item.”

Semaphores are good for producer/consumer because they give you exactly the two things this pattern needs:
- Automatic waiting at the right time
- Producers are forced to wait when the buffer is full (no empty slots).
- Consumers are forced to wait when the buffer is empty (no items to take).

Bottom-line: **Producers cannot produce faster than a consumer can consume** (Slow consumer? Producer waits. Fast consumer? Producer produces faster)

### Multiple Producers & consumers

We can also use semaphores for multiple Producers & consumers. Place a "queue" instead of a single item. We also add a **lock** on the queue access so that only a single thread can produce to or consume from it at a time

```java
Semaphore full = new Semaphore(0);  // how many items are available
Semaphore empty = new Semaphore(CAPACITY); // how many empty slots are available
Queue queue = new ArrayDeque();
Lock lock = new ReentrantLock();

// Producer
while (true) {
    Item item = producer();

    empty.acquire();            // wait if there is NO empty slot

    lock.lock();
    queue.offer(item);    // put item into the (single) slot
    lock.unlock();

    full.release();             // signal: one item is now available
}

// Consumer
while (true) {
    full.acquire();             // wait if there is NO item

    lock.lock();
    Item item = queue.poll();              // take/use the item from the slot
    lock.unlock();

    consume(item);

    empty.release();            // signal: slot is now empty again
}
```

## Inter-Thread communication and conditional variables

The following are the ways of Inter-thread communication:
1. Lock interrupts & joins
2. Semaphores

...and then, there is "Conditional variables" for a lock.

A **condition variable** is a mechanism that lets ***one thread go to sleep until some condition becomes true***, and ***another thread wake it up when that condition changes***.

Core idea in simple terms
- Threads often share some state, like “queue is empty” or “data is ready”.
- One thread wants to wait: “I’ll stop running until queue is not empty.”
- Another thread later signals: “I just put data in the queue; whoever was waiting for that can wake up now.”
A condition variable is the thing they both use to do this cleanly.

How it works with a lock:
1. You always use a condition variable together with a lock:
    - The **lock** protects shared data (so only one thread can change/check it at a time).
    - The **condition** variable lets threads:
        -  `wait` (sleep) until the data reaches a desired state.
        - `signal` or `broadcast` to wake waiting threads when the state changes.

Pseudocode example:
```
shared: some_state, lock, cond

Thread A (waiter):
  lock.lock()
  while (!condition_on_state) {
      cond.wait(lock)   // atomically: release lock, sleep, then re-lock on wakeup
  }
  // condition is true, do work with state
  lock.unlock()

Thread B (signaler):
  lock.lock()
  change some_state
  cond.signal()         // or cond.broadcast() to wake one/all waiting threads
  lock.unlock()
```

Key points:
1. `wait` releases the lock while sleeping, so other threads can change the state.
2. When `wait` wakes up, it **reacquires the lock before continuing**.
3. The `while` loop **re-checks the condition** (in case of spurious wake-ups or multiple waiters).

Why they’re useful for inter-thread communication
- They avoid busy-waiting: threads are not looping and checking the condition again and again; they sleep efficiently.
- They make producer–consumer and similar patterns clear:
    - Consumer waits on “queue not empty” condition variable.
    - Producer pushes an item and signals the condition variable.

Consumer applies **backpressure** on the producer to wait until it has consumed.

They let you express logic like: “Don’t run until X has happened,” in a clean, explicit way between threads.

Java example:
- In Java’s Lock/Condition API, **`await()`** is like wait() and **`signal()`** is like notify()—but used with an explicit Lock.
- We can define a condition using `lock.newCondition();`

Below is a very simplified producer–consumer style example using `Condition.await()` and `Condition.signal()`.
```java
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;
import java.util.concurrent.locks.Condition;

class SimpleQueue {
    private Integer item = null;          // single-slot buffer
    private final Lock lock = new ReentrantLock();
    private final Condition notEmpty = lock.newCondition();
    private final Condition notFull  = lock.newCondition();

    // Producer
    public void put(int value) throws InterruptedException {
        lock.lock();
        try {
            while (item != null) {        // buffer is full, wait
                notFull.await();         // release lock, go to sleep
            }
            item = value;                // produce
            notEmpty.signal();           // wake a waiting consumer
        } finally {
            lock.unlock();
        }
    }

    // Consumer
    public int take() throws InterruptedException {
        lock.lock();
        try {
            while (item == null) {       // buffer is empty, wait
                notEmpty.await();        // release lock, go to sleep
            }
            int value = item;            // consume
            item = null;
            notFull.signal();            // wake a waiting producer
            return value;
        } finally {
            lock.unlock();
        }
    }
}
```

**Note**: `condition.signalAll()`
- `condition.signalAll()` wakes up **all threads** that are currently waiting on that condition, which is good when the state change you just made can now allow multiple waiting threads to make progress (or when you don’t know which specific one should be woken). `condition.signal()` only wakes up one waiting thread (if any) and if there are more waiting threads, all but one continue to wait. 

### Objects as conditional variables

All objects in Java extend from the base **`Object` class** which has the following methods by default:
1. `public final void wait() throws InterruptedException`
2. `public final void notify()`
3. `public final void notifyAll()`

Every Java class inherits from the Object class.

We can use any object as a condition variable and a lock (using the `synchronized` variable)

`wait()`
- Causes current thread to wait until another thread wakes it up
- In the wait state, a thread is not consuming any CPU

Two ways to wake up a thread:
1.  `notify()`: Wakes up a *single thread* waiting on that object
2.  `notifyAll()`: Wakes up *all* the threads waiting on that object

To call any of these methods, we need t oacquire the monitor of that object (i.e use synchronized on that object)

```java
public class MySharedClass {
    private boolean isComplete = false;

    // Assume thread A is executing this
    public void waitUntilComplete() {
        synchronized (this) {
            while (isComplete === false) {
                this.wait(); // Thread A goes to sleep 
            }
        }
    }

    // ... 

    // Assume thread B is executing this
    public void complete() {
        synchronized (this) {
            isComplete = true;
            this.notify(); // Wakes up the single thread A waiting on this object
        }
    }
}
```

Note:
- `object.wait === condition.await`
- `object.notify === condition.signal`
- `object.notifyAll === condition.signalAll`


Note: If the object is **`this`** then we can just use "synchronized methods" (all work on the same object) instead of adding `this` to each block or prefix object method calls with it
```java
public class MySharedClass {
    private boolean isComplete = false;

    // Assume thread A is executing this
    public synchronized void waitUntilComplete() {
        while (isComplete === false) {
            wait(); // Thread A goes to sleep 
        }
    }

    // ... 

    // Assume thread B is executing this
    public synchronized void complete() {
        isComplete = true;
        notify(); // Wakes up the single thread A waiting on this object
    }
}
```

## Lock-free and non-blocking operations

Why do we need it? **For the most part, we probably don't!**

Locks are generally great!:
1. Most of the concurrency problems (race conditions and data race) are solved easily and safely by data locks
2. Locks have great hardware and software support

Why do we need "lock-free" solutions then?
1. **Deadlocks are usually unrecoverable** and can bring the application to a complete halt
    - More locks in a system, the higher the chances for a deadlock
2. **Slow critical section**
    - If one threads locks for a long time, the other threads are slowed down (all threads are effectively as slow as the slowest thread)
3. **Priority inversion**
    - Two threads shared a lock and one has a higher priority than the other (combo of static & bonus priorities by the developer and OS, respectively)
    - If a low priority thread acquires the lock but is preempted by the OS (scheduled out), the high priority thread cannot progress until the low priority thread is rescheduled to release the lock!
    - Priority inversion can happen if a thread dies, gets interrupted or forgets to release a lock
    - Hence, **complex code must be written** to ensure timeouts, finally blocks etc take care of releasing the lock in all adverse cases

For some applications, these drawbacks and performance issues (such as overhead with acquiring and releasing locks) become a bottleneck (ex: Trading platforms)

### Atomic operations revisit

Most of the concurrency problems, at least race conditions, are because our operations are non-atomic.
What if we could provide an atomic operation for every kind of data structure?

That is what lock-free operations do! They take advantage of the **hardware layer** to perform computations on a variable in an atomic manner (guaranteed to be atomic!)

Note: All primitives except for `long` and `double` are atomic. Read/assignment to all references are atomic. We use `volatile` on `long` and `double` read/assignment to make them also atomic.

We do not need to use `volatile` or `synchronized` on any of these data types though if we use the atomic versions of them at the platform level!

New package: **`java.util.concurrent.atomic`**

Note, if you are working on more than one atomic data type at a time or operating more than once on it within a critical section, you still need locking and synchronization!

#### Atomic integer

```java
// Assignment:
int initialValue = 0;
AtomicInteger atomicInteger = new AtomicInteger(initialValue);

// Atomically increment the integer by one
atomicInteger.incrementAndGet(); // return the new value
atomicInteger.getAndIncrement(); // return the old value

// Atomically decrement the integer by one
atomicInteger.decrementAndGet(); // return the new value
atomicInteger.getAndDecrement(); // return the old value

// Atomically add any integer
int delta = 5; // Use a negative value to decrement
atomicInteger.addAndGet(); // return the new value
atomicInteger.getAndAdd(); // return the old value
```

Pros:
- Simple
- No need for locks / sync
- No race condition or data races

Cons:
- Only the operation itself is atomic
- There is **still a race condition** between **two separate atomic operations**

Practical example:
```java
import java.util.concurrent.atomic.AtomicBoolean;
import java.util.concurrent.atomic.AtomicInteger;

public class App {
    // This code demonstrates a race condition where multiple threads are incrementing the same counter without proper synchronization.
    public static void main(String[] args) throws InterruptedException {
        InventoryCounter inventoryCounter = new InventoryCounter(); 
        Thread incrementThread = new IncrementThread(inventoryCounter);
        Thread decrementThread = new DecrementThread(inventoryCounter);

        // Start both threads to increment the counter concurrently
        incrementThread.start();
        decrementThread.start();

        // Wait for both threads to finish before printing the final count
        incrementThread.join();
        decrementThread.join();

        // Final count will be 0 due to the usage of an AtomicInteger
        System.out.println("Final count: " + inventoryCounter.getCount());
    }

    private static class InventoryCounter {
        private AtomicInteger count = new AtomicInteger(0);

        public void increment() {
            count.incrementAndGet();
        }

        public void decrement() {
            count.decrementAndGet();
        }

        public int getCount() {
            return count.get();
        }
    }

    private static class DecrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public DecrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.decrement();
            }
        }
    }

    private static class IncrementThread extends Thread {
        private InventoryCounter inventoryCounter;

        public IncrementThread(InventoryCounter inventoryCounter) {
            this.inventoryCounter = inventoryCounter;
        }

        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                inventoryCounter.increment();
            }
        }
    }
}
```
Output:
```
Final count: 0
```

Note: `AtomicLong`, `AtomicDouble`, and `AtomicBoolean` behave in a similar way and with similar methods.

#### Atomic references

This data type is for setting and getting objects atomically.

- `AtomicReference(V initialValue)`
- `V get()` - returns the current value
- `void set(V newValue)` - Sets the value to the new value

**An important comparison method**: **`boolean compareAndSet(V expectedValue, V newValue)`**
- Assigns new value ***only*** if `currentValue === expectedValue`
- Ignores the new value if the `currentValue !== expectedValue`

Note: Even `AtomicInteger`, `AtomicLong`, `AtomicDouble`, and `AtomicBoolean` have this method i.e available in all atomic classes!

Example:
```java
import java.util.concurrent.atomic.AtomicReference;

public class Main {
    public static void main(String[] args) {
        String oldName = "John";
        String newName = "Doe";

        AtomicReference<String> atomicName = new AtomicReference<>(oldName);

        // Attempt to update the name atomically
        if (atomicName.compareAndSet(oldName, newName)) {
            // If the current value is oldName, it will be updated to newName
            System.out.println("Name updated successfully: " + atomicName.get());
        } else {
            // If the current value is not oldName, the update will fail
            System.out.println("Failed to update name. Current name: " + atomicName.get());
        }
    }
}
```

Why is this `AtomicReference` and its `compareAndSet` method used in this code?
- They are used in this code to ensure thread-safe updates to the name variable. The compareAndSet method allows for an atomic check-and-set operation

If multiple threads were trying to update the name variable simultaneously, using `AtomicReference` ensures that only one thread can successfully update the name at a time, preventing race conditions and ensuring data integrity. 

If the current value of `atomicName` is equal to oldName, it will be updated to newName atomically, otherwise, the update will fail, and the current name will be printed without any risk of inconsistent state due to concurrent modifications.

## Threading models for high performance I/O

### Negative impact of blocking on locks

What happens to other threads when one thread has a lock on a critical section?
- All the other threads are "blocked"
- Only when the lock is freed, can they access it (again, usually one by one)

```
method {
    critical section
        use resource
    end critical section
}
```

In order to get around the negative / blocking impacts of locking, **"lock-free"** algorithms/data structures/atomic operations were introduced.

### Another type of blocking - Blocking I/O

There are two types of operations in general:
1. CPU intensive: Spends most of its time doing computational tasks on the CPU
2. I/O bound: Spends most of its time waiting for an I/O operation to complete (Ex: File system access)

In the discussions so far on **"throughput"** performance and its optimization, we have assumed that the threads are CPU intensive! However, this is far from ideal. Many threads will be I/O bound too!

**What is I/O?**

Your program + CPU are fast; I/O devices are slow.

```text
Program ----read/write----> File / Network / Console
           (I/O operation)
```

Examples of I/O:
1. Read from a file (Storage disk access)
2. Write to a file (Storage disk access)
3. Send/receive data over network (Ex: calling other services/APIs - made possible via the network card)
4. Print to terminal (Monitor)
5. Act on a mouse event (Mouse), ... so on

The CPU has *no direct access* to these I/O devices. They usually have **"Controllers"** (Driver software installed on the system) that communicate with the CPU.

The CPU only has direct access to **memory** (RAM). CPU cache and registers are part of the CPU itself. Apart from these, no other direct access mechanisms exist.

**Blocking I/O: basic idea**

With blocking I/O, when you ask the OS to do I/O, your thread waits there until it finishes. It cannot do other work meanwhile.

```text
Thread:
   do stuff
   read(data)  --> WAIT here until data arrives / is read
   do more stuff
```

Timeline:
```text
Time →
Thread:
  [ compute ] [  BLOCKED on I/O  ] [ compute ]
```
- CPU work only happens in the "compute" parts.
- During "BLOCKED on I/O", this thread is just waiting.

Imagine reading from a file:
```
Your thread           OS / Device
   |                      |
   |  read() ------------>|
   |      (request)       |
   |   (go to sleep)      |
   |  ........waiting.....|
   |                      |-- disk/network work --> data ready
   |<---------------------|
   |     wake + data      |
   |  continues running   |
```

Blocking I/O is when a thread makes an I/O call and then stops and waits right there until the OS finishes that input/output operation, before doing anything else.

**I/O blocking is wasteful and reduces throughput!**

- The Thread is put to sleep 
- Does nothing until the data comes back from the I/O device controller
- It can potentially do other things!
- What makes it **worse** is that even to transfer large bytes of data from the I/O device to the memory, the I/O device controller uses the **Direct Memory Access (DMA)** as a bridge, to bypass the CPU. So, the CPU literally mostly just waits for the events from the controller to know when it is done, etc!

Even with a fixed thread pool (See `Executor` class), reusing the threads (since context switch is cheaper) does not solve the blocking I/O problem. That is, it assumes all processes are CPU bound in order to improve performance (throughput)

```java
public void handleRequest (HttpExchange exchange) {
    Request request = parseUserRequest(exchange); // Fast CPU operation
    Data data = readFromDatabase(request); // SLOW (BLOCKING) I/O OPERATION ❌
    sendPageToUser(data, exchange); // Fast CPU operation
}
```

### I/O bound use-cases

1. Online web store application (News website) (The thread mostly waits for DB/API responses, so this is I/O-bound.)
```
User → [ Web Server Thread ]
           |
           v
      +----------+       +------------+
      |  render  |-----> | DB / API   |
      |  HTML    |  I/O  | (slow)     |
      +----------+       +------------+
            ^                 ^
            |                 |
          CPU           Network / Disk
        (fast)             (slow)
```

2. Big-data / ML transform application
```
+-------------+      +--------------+      +------------+
|  Storage    | ---> |  App Thread  | ---> |  Storage   |
|  (files)    | I/O  |  (transform) | I/O  | (results)  |
+-------------+      +--------------+      +------------+
     ^                     ^
     |                     |
   Disk I/O            CPU work (faster)
    (slow)            between long reads/writes
```

**Important**: Throughput is often limited by how fast you can read/write data, not how fast you can compute.

### Even a few blocking I/O threads can signicantly impact throughput

**Note**: All it takes is even just one or a few long blocking I/O bound tasks to affect the throughput!
- Ex of an HTTP server: 4 HTTP request threads come into a 4 CPU core system (multithreaded, concurrent, `1 thread = 1 core` optimization)
    - One request takes a long time, so when 4 more requests come, only 3 threads in the pool are available
        - Again one request takes a long time, so when even more requests come, only 2 threads are available and so on...
            - Eventually all CPU cores are busy (the threads on them are blocked on I/O). Other, new threads are waiting unnecessarily for the CPU access! 

4 requests arrive:
```
Cores/Threads:

Core1: [Req1 handling...]
Core2: [Req2 handling...]
Core3: [Req3 handling...]
Core4: [Req4 handling...]

Some requests hit slow DB / API: threads BLOCK on I/O
```

One request is very slow I/O
```
Core1: [Req1 BLOCKED on I/O]   ← thread alive but waiting
Core2: [Req2 doing work]
Core3: [Req3 doing work]
Core4: [Req4 doing work]
```

Now 4 more requests arrive, but only 3 threads are effectively doing useful work (one is stuck on I/O).

Later another long I/O request appears
```
Core1: [Req1 BLOCKED on I/O]
Core2: [Req5 BLOCKED on I/O]
Core3: [Req3 doing work]
Core4: [Req4 doing work]
```

More new requests come in; now only 2 threads are actively progressing.

Eventually, all threads end up blocked
```
Core1: [BLOCKED on I/O]
Core2: [BLOCKED on I/O]
Core3: [BLOCKED on I/O]
Core4: [BLOCKED on I/O]

New incoming requests:
   wait in queue, even though CPU
   could be free if we didn't tie up
   threads with blocking I/O.
```

Takeaways:
1. A **few long blocking I/O calls grab threads and hold them** while they wait on disk/network -> **Impacts the entire application**
2. As more such requests appear, more threads are stuck, and fewer are left to handle new incoming work.
3. This reduces overall throughput, because threads (and indirectly cores) are “busy” doing nothing but waiting on I/O.

**Therefore: `1 thread = 1 core` oiptimization does NOT give us the best throughput when dealing with blocking I/O calls**

### Thread per task/request model

What we have seen so far: 1 thread per CPU core
- It is sub-optimal
- If more blocking threads run, all the CPU cores eventually end up busy (Since eventually all the blocking threads grab a CPU core each)

```
4 CPU cores, 4 threads total

Cores:     [Core1] [Core2] [Core3] [Core4]
Threads:   [ T1  ] [ T2  ] [ T3  ] [ T4  ]

If T2, T3 block on I/O:

Core1: [ T1 running ]
Core2: [ T2 BLOCKED on I/O ]
Core3: [ T3 BLOCKED on I/O ]
Core4: [ T4 running ]

=> 2 cores are effectively wasted waiting on I/O.
```

What we can do: **Assign/create 1 thread per task**
- Since threads are interleaved and scheduled on the CPU cores by the OS, every thread is run conccurently
- This will improve the throughput & hardware utilization
- Hence, faster than a thread-per-core model

```
Tasks:  Req1 Req2 Req3 Req4 Req5 Req6
Threads: T1   T2   T3   T4   T5   T6

Cores: [Core1] [Core2] [Core3] [Core4]

Scheduler time-slices:

Time slice 1:  Core1:T1  Core2:T2  Core3:T3  Core4:T4
Time slice 2:  Core1:T5  Core2:T6  Core3:T1  Core4:T2
Time slice 3:  Core1:T3  Core2:T4  Core3:T5  Core4:T6
...
=> All tasks make progress “concurrently”.
```

How many threads is enough?
1. Unchecked: Too many threads? The JVM runs of out memory -> Application crashes
2. Too few threads? Low CPU utilization i.e bad throughput
3. **Solution**: Have a **fixed pool of threads more than the number of CPU cores**. No right formula, depends, needs testing. (Ex: `Executor executor = Executor.newFixedThreadPool(numberOfThreads);`)

```
Too few threads (e.g., 2 threads on 8 cores):

Cores: [C1] [C2]    [C3]      [C4]      [C5]      [C6]      [C7]      [C8]
Use :  [T1] [T2] [  idle  ][  idle  ][  idle  ][  idle  ][  idle  ][  idle  ]

=> Low CPU utilization, bad throughput.


Too many threads (e.g., 1000 threads):

Threads: T1 T2 T3 ... T1000
Memory: stack + metadata for each thread

=> High memory use, lots of context switching, possible OOM.
```

```
Fixed thread pool (> cores):

int cores = 4;
int poolSize = 8;

ExecutorService ex = Executors.newFixedThreadPool(8);

=> More threads than cores, but bounded.
```

#### Ideal numebr of blocking calls per thread in the thread-per-task model

Thread per task where task only does 1 blocking I/O:
- Fewer context switches, less time for the total CPU run duration 

Thread per task where task only does 1 blocking I/O:
- Multiple context switches, CPU spends a lot of time just scheduling a thread!
- **Counter productive!** in the thread-per-task model!
- Known as **"Threadshing"**: A situation where most of the CPU is spent on the OS managing the system

“Threadshing” (as written above) is really “thread thrashing”; it is related in spirit to classic OS thrashing, but they are different things
- Thrashing: the system spends most time swapping memory pages between RAM and disk instead of running your code
- Cause: Too many processes for the physical memory; each has too few frames, causing constant page faults and swapping

**Final note**: Thread per task/request has been industry standard for many years. However, due to the above issues, we know that it:
- It will **not** give us optimal performance or CPU utilization

## Non-blocking I/O

Threads per task work fine for standard applications even though it is sub-optimal. It has been in use for a while.

Imagine another scenario:
- A task is chosen based on some condition
- This chosen task is one type of I/O bound operation
- Say, one is for reading from the DB and another, a service call

If 50% of the requests go to the DB and 50% to the service, if the service crashes / delays a response disproportionately to the DB response:
- Then even if we use 1 thread per request/task, **eventually** all the threads become blocking
- Ex: 
    - 100 threads (i.e 100 requests) -> 50 land in DB (fast), 50 get blocked by service
    - Next 100 threads arrive -> They only have 50 threads to choose from -> 25 sent to DB, 25 get blocked on service again
    - Remaining 50 new task have to wait for the 25 DB threads to free up. **The number of threads are diminishing with time!**

Hence, even threads per request/task have issues due to **Inversion of Control**
- It essentially means that the thing you want to control (service in this case, we just ask it to give us back some data) ends up controlling you (blocking your threads)

```
You (app code):

   callService()  --->  [Service]
       |                    |
       |---- "Please send data" --->  (service does its work)
       |
       |  (thread waits here...)
       v

If service is slow or stuck:
   - Your thread remains BLOCKED
   - New requests can't get threads
   - Service delay ends up controlling your throughput
```
```
You want:   You control service latency impact
Reality:    Service latency controls your thread availability
```

Solution: **Non-blocking I/O**

In non-blocking I/O, we create a method that **immediately returns**
- Thread is not blocked
- Whenever the data is ready from the I/O, we can receive it in the thread
- Since the thread is not blocked, it can scheduled in and out -> aids concurrency as other, esp. new threads can get CPU time!

How can we fetch the data in non-blocking I/O? 
- We need to use "callbacks" (Similar to JS callbacks)

Pseudocode:
```
public void someMethod() {
    nonBlockingIO((data) -> {
        process(data) // CPU operation
    })
}
```

```
someMethod():
   |
   +-- nonBlockingIO(callback) ---> OS / library starts I/O
   |
   +-- returns immediately
       (thread can handle other requests)

Later, when I/O done:
   OS/lib calls -> callback(data)
                    |
                    +-- process(data)
```

So, in our example, if the server response never comes back or comes back very late, the subsequent requests are not waiting in queue and even the thread that made the call to the server is not blocked!

***Biggest benefit***: We can perform non-blocking I/O on a **SINGLE THREAD**!

Since the "call" returns immediately, multiple requests can be serviced conccurently:
- Get request -> make non-blocking I/O call -> returns immediately, the thread is free again
- New request -> make another non-blocking I/O call -> returns immediately, the thread is free again ... so on
- Data comes back from 1st request -> the same single thread picks it up again and processes it (CPU work) -> done processing? -> Free again

### Combination of multi-threading and non-blocking I/O

If non-blocking works on single-threaded program running on a single core, when would we need multi-threading?

Answer: If the number of cores is more than one, we can have the original **`#threads = #cores`**. Why? Since one thread can do non-blocking I/O, only if there are more CPU core available, we want to have many threads to take advantage of true parallelism!

### Drawbacks of non-blocking I/O

1. **Security and stability**: The APIs available to perform non-blocking I/O in Java are complex. Libraries make the job easier (`netty`, `vert.x`, `webflux`)
2. **Callback hell** (of nested callbacks): Same as in JavaScript. JavaScript provides **async/await** to solve this issue. Else, it is **Hard to read and understand**
3. **Harder to debug & test**

***If these issues can be resolved too, non-blocking I/O would definitely be better than multithreaded I/O.***

```
Cores:   [Core1] [Core2] [Core3] [Core4]
Threads: [ T1  ] [ T2  ] [ T3  ] [ T4  ]
Model:   #threads = #cores

Each Tn:
   - Uses non-blocking I/O
   - Handles many requests via callbacks

So overall:

Core1/T1: [R1,R2,... via non-blocking I/O]
Core2/T2: [R101,R102,...]
Core3/T3: [R201,R202,...]
Core4/T4: [R301,R302,...]

We get:
   - Parallelism across cores (T1..T4)
   - Concurrency within each thread (many I/Os per thread)
```

## Virtual threads and high performance I/O

The threads we have used so far are called "Platform threads" (provided by the JVM)
- Each platform thread object has a `run()` and a `start()` method
- Each platform thread is a 'thin wrapper' over an 'OS Thread'
- It is the OS thread that runs on the CPU, is managed by the OS, etc. Users have no control over the management and scheduling 

However, platform threads can be seen as "costly" because:
1. Every platform thread is mapped `1:1` with an OS thread (and created too many threads is not a good idea as we have seen so far)
2. Have a **fixed-size stack** memory (to store local variables)

```
            Your Java code (Platform thread)

          +---------------------------+
          |  Platform Thread (T1)    |
          |  - start()               |
          |  - run()                 |
          +------------+------------+
                       |
                       |  1 : 1 mapping
                       v
          +---------------------------+
          |      OS Thread (#1)      |
          |  - scheduled by OS       |
          |  - runs on CPU core      |
          +------------+------------+
                       |
                       v
                    [ CPU ]


Multiple platform threads:

 +---------------------------+      +---------------------------+
 |  Platform Thread (T1)    |      |  Platform Thread (T2)    |
 +------------+------------+      +------------+------------+
              |                              |
              v                              v
 +---------------------------+      +---------------------------+
 |      OS Thread (#1)      |      |      OS Thread (#2)      |
 +------------+------------+      +------------+------------+
              |                              |
              v                              v
          [ CPU core ]                  [ CPU core ]
```

### Introduction to a virtual thread

A **virtual thread** is an ordinary Java object in its heap!
- It is entirely managed by the Java JVM. The OS does not know of its existence!
- As a result, the JVM is responsible for managing its state and scheduling!

**NOTE: ONLY AVAILABLE IN JAVA 21 AND BEYOND**

Every virtual thread runs on one of a fixed size of platform threads (known as "carrier threads") the JVM creates:
1. When at least one virtual thread is created, the JVM creates a fixed pool of Platform/Carrier threads. But, this is never a 1:1 mapping (much less)
2. Usually the number of Platform/Carrier threads created is `= # cores` and not more
3. JVM takes care of mounting and unmounting the virtual threads on platform threads
    - State and instruction pointer are saved for the VT in case it needs to wait and be removed from a carrier thread
        - This is saved on a heap (not fixed size stack like in the case of a platform thread): Cheaper, lighter
    - Unmount: Save state, schedule another waiting thread, if any
    - Mount: Check which carrier thread is free, and resume VT there
        - No free carrier thread? VT needs to wait!

```
          Java Heap (your objects, incl. virtual threads)
          -----------------------------------------------
          |  Virtual Thread V1   (ordinary Java object) |
          |  Virtual Thread V2   (ordinary Java object) |
          |  Virtual Thread V3   (ordinary Java object) |
          |  ...                                        |
          -----------------------------------------------
                 ^             ^              ^
                 |             |              |
                 |  scheduled by JVM runtime |
                 +-------------+--------------+


      JVM creates a small pool of Platform/Carrier Threads
      (usually ~= # CPU cores) [web:357][web:361][web:370]

          +--------------------------+
          |  Platform Thread P1      |  <-- OS Thread #1 (carrier)
          +--------------------------+
          |  Platform Thread P2      |  <-- OS Thread #2 (carrier)
          +--------------------------+
          |  Platform Thread P3      |  <-- OS Thread #3 (carrier)
          +--------------------------+
          |  ...                     |
          +--------------------------+


Mounting virtual threads on carriers (many:few, not 1:1) [web:357][web:358][web:364]

   Time slice A:                 Time slice B:

   V1 runs on P1                 V3 runs on P1
   V2 runs on P2                 V4 runs on P2
   V3 waiting                    V1 waiting

   (JVM decides which virtual     (JVM remounts other virtual
    thread runs on which          threads on the same small set
    platform/carrier thread)      of carrier threads)

```

Key points:
- Virtual threads live as Java objects in the heap; OS doesn’t see them
- JVM, not the OS, schedules them onto a **fixed-size** pool of platform/carrier threads, usually ≈ number of cores.
- Many virtual threads ↔ few carrier threads (no 1:1 mapping).

Benefits of virtual threads:
1. **Creating it is cheap**:Less expensive to manage Java objects than to manages platform threads (Context switching, stack, etc)
2. More peformant! i.e faster: **No context switch overhead** on the underlying Carrier/Platform threads at the OS level! (Why? JVM manages scheduling of VTs within a Platform thead)
3. It is **garbage collected** by the JVM once it has finished its operation!

```java
// Works only from Java 21+ (onwards)

import java.util.ArrayList;
import java.util.List;

public class VirtualThreadsDemo {
    private static final int NUMBER_OF_VIRTUAL_THREADS = 1000;
    public static void main(String[] args) throws InterruptedException {
        Runnable runnable = () -> System.out.println("Inside thread: " + Thread.currentThread());

        List<Thread> virtualThreads = new ArrayList<>();

        for (int i = 0; i < NUMBER_OF_VIRTUAL_THREADS; i++) {
            Thread virtualThread = Thread.ofVirtual().unstarted(runnable); // Syntax: Way to initialize a virtual thread!
            virtualThreads.add(virtualThread);
        }

        for (Thread virtualThread : virtualThreads) {
            virtualThread.start();
        }

        for (Thread virtualThread : virtualThreads) {
            virtualThread.join();
        }
    }
}
```

### High-performance Non-blocking I/O with virtual threads

For Non-blocking I/O with virtual threads, the key benefit is that we can perform the operational just like a simple, blocking call:
```java
public void handleRequest (HttpExchange exchange) {
    Request request = parseUserRequest(exchange); // Fast CPU operation
    Data data = readFromDatabase(request); // NOT SLOW / BLOCKING) IF VIRTUAL THREADS USED
    sendPageToUser(data, exchange); // Fast CPU operation
}
```

It is still non-blocking. How? 
- In virtual threads, the blocking I/O calls are internally mapped to the non blocking I/O objects
- Hence, the virtual thread can internally be mounted and unmounted if it is waiting idly on an I/O operation
- So a single Platform/Carrier thread can have multiple VTs scheduled on them just like a non-blocking I/O tasks would 
    - All without the need for the user to write complex non-blocking code 

Virtuals threads (best of both worlds: Combination of non-blocking I/O and multi-threading concepts):
1. Performance: optimal
2. Safety/stability: No issues
3. Code writing: easy
4. Code reading: easy
5. Testing: easy
6. Debugging: easy

Virtual threads are useful **beyond** nob-blocking I/O use-cases since they are cheaper and faster than traditional threads. Some of the built-in methods have been refactored to use virtual threads by Java:
1. `Thread.sleep()`
2. Locks: `Reentrant.lock()`
3. Semaphores: `Semaphore.acquire()`
4. Networking APIs - Socket/Datagram (TCP/UDP)

... so on

Bottom-line: Virtual threads are awesome!

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class IoBoundApplicationV2 {
    private static final int NUMBER_OF_TASKS = 10_000;

    public static void main(String[] args) {
        System.out.printf("Running %d tasks\n", NUMBER_OF_TASKS);

        long start = System.currentTimeMillis();
        performTasks();
        System.out.printf("Tasks took %dms to complete\n", System.currentTimeMillis() - start);
    }

    private static void performTasks() {
        // To use virtual threads: Replace `Executors.newCachedThreadPool()` with `Executors.newVirtualThreadPerTaskExecutor()`
        try (ExecutorService executorService = Executors.newVirtualThreadPerTaskExecutor()) {

            for (int i = 0; i < NUMBER_OF_TASKS; i++) {
                executorService.submit(new Runnable() {
                    @Override
                    public void run() {
                        for (int j = 0; j < 100; j++) {
                            blockingIoOperation();
                        }
                    }
                });
            }
        }
    }

    // Simulates a long blocking IO
    private static void blockingIoOperation() {
        System.out.println("Executing a blocking task from thread: " + Thread.currentThread());
        try {
            Thread.sleep(10);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
    }
}
```

### Virtual threads best practices

1. **CPU only operations**: **Virtual threads provide NO benefit** over regular threads in terms of performance
2. **Latency**: **Virtual threads provide NO benefit** over regular threads since whether it is run concurrently or not, the total time for a thread to finish what it needs to do will not change (overall execution time)
3. **Only benefit of Virtual Threads = `THROUGHPUT`** ✅ (Run more tasks while the CPU is waiting on one task using VT)
    - Additionally, VTs are better in the case of **short & frequent blocking calls**
        - Why? Context switches of the platform threads are avoided with VTs (VTs have only mounting/unmounting overheads which is much smaller than CS)
        - Possible solution: "Batch" short I/O operations into less frequent long I/O operations

Best practices for Virtual threads:
1. **Never create a fixed size pool of VTs**:
    - JVM already does the pool creation internally for the platform/carrier threads that the VTs will run on
2. **Preferred way to use VTs**: `Executors.newVirtualThreadPerTaskExecutor()`
    - Creates a new VT internally for *every task submitted to this executor service*
    - Helps the user focus on working on a "simple, thread per task mental model"!
3. **Virtual threads are always Daemon threads** - Never prevent our application from exiting
    - If we try to set it on a VT object with `setDaemon`, an exception is thrown!
4. **Virtual threads always have a default priority** - Setting it makes no sense
    - If we try to set it on a VT object with `setPriority`, it has no effect

Observability and debugging VTs:
- Breakpoints in IDEs will work as expected even though platform threads supporting the VT is hidden
- Follow best practices since VTs can be in the thousands to millions (as they are so easy & cheap to create). Debugging so many threads is generally harder.
