<!-- TOC --><a name="http-server-construction-using-java"></a>
# HTTP server construction using plain Java

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [HTTP server construction using Java](#http-server-construction-using-java)
   * [Part 1: The Foundation, Sockets, Ports, and Booting Up](#part-1-the-foundation-sockets-ports-and-booting-up)
      + [ASCII Diagram: The Network Telephone System](#ascii-diagram-the-network-telephone-system)
      + [2. What is HTTP, Really?](#2-what-is-http-really)
      + [3. Java: Step 1 - Booting Up the Server (The Listening Post)](#3-java-step-1-booting-up-the-server-the-listening-post)
         - [The Non-Trivial Concept: The "Backlog"](#the-non-trivial-concept-the-backlog)
         - [The Java Code (Part 1)](#the-java-code-part-1)
         - [ASCII Diagram: The Backlog (Waiting Room)](#ascii-diagram-the-backlog-waiting-room)
      + [4. Comparison: Step 1 in Node.js](#4-comparison-step-1-in-nodejs)
         - [The Node.js Code (Part 1)](#the-nodejs-code-part-1)
      + [Summary of Part 1](#summary-of-part-1)
   * [`java.net.InetSocketAddress` (The GPS Coordinates)](#javanetinetsocketaddress-the-gps-coordinates)
      + [What is it?](#what-is-it)
      + [Why do we need it?](#why-do-we-need-it)
      + [ASCII Diagram: Forging the Address](#ascii-diagram-forging-the-address)
   * [`java.io.IOException` (The Disaster Plan)](#javaioioexception-the-disaster-plan)
      + [What is it?](#what-is-it-1)
      + [Why do we need it?](#why-do-we-need-it-1)
      + [ASCII Diagram: The Disaster Scenario](#ascii-diagram-the-disaster-scenario)
      + [3. Comparison: JavaScript & Node.js](#3-comparison-javascript-nodejs)
         - [The Address (Node.js)](#the-address-nodejs)
         - [The Disaster Plan (Node.js)](#the-disaster-plan-nodejs)
      + [4. Summary Table](#4-summary-table)
   * [Part 2: The Router (Contexts) and Directing Traffic](#part-2-the-router-contexts-and-directing-traffic)
      + [1. The Non-Trivial Concept: The "Prefix" Trap](#1-the-non-trivial-concept-the-prefix-trap)
         - [ASCII Diagram: The Receptionist's Rules](#ascii-diagram-the-receptionists-rules)
      + [2. Java: Building the Contexts](#2-java-building-the-contexts)
         - [The Java Code (Part 2)](#the-java-code-part-2)
      + [3. Comparison: JavaScript & Node.js](#3-comparison-javascript-nodejs-1)
         - [ASCII Diagram: The Node.js Funnel](#ascii-diagram-the-nodejs-funnel)
         - [The Node.js Code (Part 2)](#the-nodejs-code-part-2)
      + [4. Summary Table](#4-summary-table-1)
   * [Part 3: The Handler (The Kitchen) and Serving the Webpage](#part-3-the-handler-the-kitchen-and-serving-the-webpage)
      + [1. The Non-Trivial Concept: The `HttpExchange` Box](#1-the-non-trivial-concept-the-httpexchange-box)
         - [ASCII Diagram: The Golden Order](#ascii-diagram-the-golden-order)
      + [2. Java: Writing the Handler](#2-java-writing-the-handler)
         - [The Java Code (Part 3)](#the-java-code-part-3)
      + [3. Comparison: JavaScript & Node.js](#3-comparison-javascript-nodejs-2)
         - [ASCII Diagram: Java vs. Node.js Objects](#ascii-diagram-java-vs-nodejs-objects)
         - [The Node.js Code (Part 3)](#the-nodejs-code-part-3)
      + [4. Summary Table](#4-summary-table-2)
         - [The Byte Calculation Trap](#the-byte-calculation-trap)
   * [Part 4: Reading Incoming Data (GET vs. POST)](#part-4-reading-incoming-data-get-vs-post)
      + [1. The Non-Trivial Concept: No Magic Dictionaries](#1-the-non-trivial-concept-no-magic-dictionaries)
         - [ASCII Diagram: The Raw Data Problem](#ascii-diagram-the-raw-data-problem)
      + [2. Java: Reading GET Requests (Query Parameters)](#2-java-reading-get-requests-query-parameters)
         - [The Java Code (Reading GET)](#the-java-code-reading-get)
      + [3. Java: Reading POST Requests (The Body)](#3-java-reading-post-requests-the-body)
         - [ASCII Diagram: The InputStream Pipe](#ascii-diagram-the-inputstream-pipe)
         - [The Java Code (Reading POST)](#the-java-code-reading-post)
      + [4. Comparison: JavaScript & Node.js](#4-comparison-javascript-nodejs)
         - [ASCII Diagram: Node.js Data Chunks](#ascii-diagram-nodejs-data-chunks)
         - [The Node.js Code](#the-nodejs-code)
      + [5. Summary Table](#5-summary-table)
   * [Part 5: Concurrency and Threading](#part-5-concurrency-and-threading)
      + [1. The Non-Trivial Problem: The "Blocking" Nightmare](#1-the-non-trivial-problem-the-blocking-nightmare)
         - [ASCII Diagram: The Blocking Timeline](#ascii-diagram-the-blocking-timeline)
      + [2. Java's Solution: The `ExecutorService`](#2-javas-solution-the-executorservice)
         - [Option A: `newFixedThreadPool(10)`](#option-a-newfixedthreadpool10)
         - [Option B: `newCachedThreadPool()`](#option-b-newcachedthreadpool)
      + [3. The Complete Java Example (Simulating the Fix)](#3-the-complete-java-example-simulating-the-fix)
         - [ASCII Diagram: The Thread Pool Timeline](#ascii-diagram-the-thread-pool-timeline)
      + [4. Comparison: The Node.js Reality Check](#4-comparison-the-nodejs-reality-check)
         - [The Node.js "CPU-Bound" Trap](#the-nodejs-cpu-bound-trap)
         - [How Node.js fixes this (The Modern Way)](#how-nodejs-fixes-this-the-modern-way)
   * [Part 6: Handling JSON Requests and Responses](#part-6-handling-json-requests-and-responses)
      + [1. The Non-Trivial Concept: The Missing Translator](#1-the-non-trivial-concept-the-missing-translator)
      + [ASCII Diagram: The JSON Translation](#ascii-diagram-the-json-translation)
      + [2. Java: Sending and Receiving JSON](#2-java-sending-and-receiving-json)
      + [3. Comparison: JavaScript & Node.js](#3-comparison-javascript-nodejs-3)
   * [Part 7: Handling Auth (Cookies & JWTs)](#part-7-handling-auth-cookies-jwts)
      + [1. The Non-Trivial Concept: The "Headers" Vault](#1-the-non-trivial-concept-the-headers-vault)
      + [ASCII Diagram: The Bouncer at the Club](#ascii-diagram-the-bouncer-at-the-club)
      + [2. Java: Reading the Headers](#2-java-reading-the-headers)
      + [3. Comparison: JavaScript & Node.js](#3-comparison-javascript-nodejs-4)
   * [4. Summary Table: JSON and Auth](#4-summary-table-json-and-auth)

<!-- TOC end -->

Let's dive incredibly deep into this. Because building a server from absolute scratch involves several moving parts, we are going to break this down into a multi-part masterclass. 

<!-- TOC --><a name="part-1-the-foundation-sockets-ports-and-booting-up"></a>
## Part 1: The Foundation, Sockets, Ports, and Booting Up

We will cover what is actually happening at the hardware/network level, and how to write the Java code to open the "doors" of your server.

Before HTTP even exists, computers need a way to physically connect. 

Imagine your computer is a massive apartment building.
* **The IP Address:** This is the street address of the building (e.g., `192.168.1.5`). It gets the data to your computer.
* **The Port:** This is the specific apartment number inside the building (e.g., Port `8080`). 
* **The Socket:** This is the actual telephone sitting inside that specific apartment. 

If a web browser wants to talk to your Java program, it cannot just yell at the building. It must dial the exact apartment number (Port) and wait for your Java program to pick up the phone (Socket).

<!-- TOC --><a name="ascii-diagram-the-network-telephone-system"></a>
### ASCII Diagram: The Network Telephone System
```text
[ THE BROWSER (Client) ]                       [ YOUR COMPUTER ]
IP: 104.20.15.1                                IP: 192.168.1.5

(Wants to talk to your Java Server)
      |
      v
[ Client Socket ] ====== (The Internet) =====> [ Port 80 ]   (Closed door - Web Server)
                                               [ Port 443 ]  (Closed door - Secure Web)
                                               [ Port 8080 ] <-- YOUR JAVA PROGRAM IS LISTENING HERE!
                                                     |
                                               [ Server Socket ] (Picks up the connection)
```

<!-- TOC --><a name="2-what-is-http-really"></a>
### 2. What is HTTP, Really?

Once the browser and your Java program pick up the Sockets, they are connected. But Sockets only send **raw bytes** (1s and 0s). 

If you pick up a phone and the other person speaks French, and you speak Japanese, the connection is useless. **HTTP (Hypertext Transfer Protocol)** is simply the agreed-upon language. It is literally just plain text formatted in a very specific, strict way.

If you read the raw bytes coming over the socket from a browser, it looks exactly like this plain text:
```text
GET /index.html HTTP/1.1
Host: localhost:8080
User-Agent: Mozilla/5.0
Accept-Language: en-US
```

If we used raw `java.net.Socket` libraries, we would have to write hundreds of lines of code to read this text letter-by-letter, find the spaces, and figure out what the browser wants. 

Instead, we will use the **`com.sun.net.httpserver`** package. This library sits on top of raw Sockets and automatically translates that block of text into easy-to-use Java Objects.

<!-- TOC --><a name="3-java-step-1-booting-up-the-server-the-listening-post"></a>
### 3. Java: Step 1 - Booting Up the Server (The Listening Post)

Let's write the code to create the server, open Port 8080, and start listening.

<!-- TOC --><a name="the-non-trivial-concept-the-backlog"></a>
#### The Non-Trivial Concept: The "Backlog"
When you create a server, you must define the "Backlog." 
Imagine your Java program is taking a phone call from Client A. Suddenly, Client B, C, and D call at the exact same millisecond. 

The **Backlog** is the size of the "Waiting Room" line. If the backlog is set to 10, the server will put 10 people on hold. If an 11th person calls, the server instantly hangs up on them (Connection Refused).

<!-- TOC --><a name="the-java-code-part-1"></a>
#### The Java Code (Part 1)
```java
import com.sun.net.httpserver.HttpServer;
import java.net.InetSocketAddress; // Explained in the next section why this is needed
import java.io.IOException; // Explained in the next section why this is needed

public class MyMasterServer {

    public static void main(String[] args) {
        
        try {
            // 1. Define the Address (Port 8080)
            // We use InetSocketAddress to represent an IP and a Port.
            InetSocketAddress address = new InetSocketAddress(8080);
            
            // 2. The Backlog (Waiting Room Size)
            // Putting '0' tells Java: "Just use the operating system's default waiting room size."
            int backlog = 0;
            
            // 3. Create the Server
            HttpServer server = HttpServer.create(address, backlog);
            
            // 4. Turn the server on!
            server.start();
            
            System.out.println("Success! Server is listening on Port 8080...");
            
        } catch (IOException e) {
            // If Port 8080 is already being used by another app (like Skype), this will crash!
            System.out.println("Failed to start server: " + e.getMessage());
        }
    }
}
```

<!-- TOC --><a name="ascii-diagram-the-backlog-waiting-room"></a>
#### ASCII Diagram: The Backlog (Waiting Room)
```text
[ Browser A ] ---> (Talking to Java)
[ Browser B ] ---> (In Waiting Room - Slot 1)
[ Browser C ] ---> (In Waiting Room - Slot 2)
[ Browser D ] ---> (In Waiting Room - Slot 3)
[ Browser E ] ---> X CONNECTION REFUSED! (Waiting room is full!)
```

<!-- TOC --><a name="4-comparison-step-1-in-nodejs"></a>
### 4. Comparison: Step 1 in Node.js

Node.js approaches booting up the server with much less configuration. It hides the concept of the "Backlog" from you by default (though you can configure it if you dig deep).

Because Node.js is asynchronous, it doesn't need a big waiting room in the same way Java does. Instead of dealing with one caller at a time while others wait, Node.js puts everyone on hold instantly, takes their order, sends it to the kitchen, and moves to the next person in milliseconds.

<!-- TOC --><a name="the-nodejs-code-part-1"></a>
#### The Node.js Code (Part 1)
```javascript
const http = require('http'); // The built-in library

// 1. Create the server object
// (We leave the parenthesis empty for now. We will add the logic later).
const server = http.createServer(); 

// 2. Turn the server on!
// We give it the Port (8080). 
// The callback function () => {} runs exactly once when the server successfully starts.
server.listen(8080, () => {
    console.log("Success! Node Server is listening on Port 8080...");
});
```

<!-- TOC --><a name="summary-of-part-1"></a>
### Summary of Part 1

At this exact moment, both our Java program and our Node.js program are running. They have successfully claimed Port 8080 from the Operating System. 

If you open your web browser right now and type `http://localhost:8080`, your browser will connect to the server! 

**However**, because we haven't built a "Router" (Context) or a "Kitchen" (Handler) yet, the browser will just sit there staring at a blank white screen until it times out, because our server doesn't know how to say hello back.


<!-- TOC --><a name="javanetinetsocketaddress-the-gps-coordinates"></a>
## `java.net.InetSocketAddress` (The GPS Coordinates)

If your computer is a massive apartment building, the `InetSocketAddress` is the exact mailing label. 

<!-- TOC --><a name="what-is-it"></a>
### What is it?
The word "Inet" stands for Internet. This class is a strict, formal blueprint that combines two pieces of information into one single package:
1.  **The IP Address** (Which building?)
2.  **The Port Number** (Which apartment door?)

<!-- TOC --><a name="why-do-we-need-it"></a>
### Why do we need it?
When you tell Java to create an `HttpServer`, Java refuses to just accept the number `8080`. It demands a formal `InetSocketAddress` object because it needs to know *which* network card to listen on. (Some servers have multiple network cards, like one for the public internet and one for a private internal network).

By doing `new InetSocketAddress(8080)`, you are telling Java: *"Listen on Port 8080, and accept connections from ANY of this computer's IP addresses."*

<!-- TOC --><a name="ascii-diagram-forging-the-address"></a>
### ASCII Diagram: Forging the Address
```text
[ RAW DATA ]                    [ THE JAVA OBJECT ]                  [ THE SERVER ]
 Port: 8080      =======>                                 =======> 
 IP: "Any"       =======>    [ InetSocketAddress ]        =======>  HttpServer.create()
                              (The Mailing Label)
```


<!-- TOC --><a name="javaioioexception-the-disaster-plan"></a>
## `java.io.IOException` (The Disaster Plan)

This is one of the most famous (and sometimes annoying) concepts in Java: **Checked Exceptions**. 

<!-- TOC --><a name="what-is-it-1"></a>
### What is it?
"IO" stands for **Input / Output**. An `IOException` is a specialized alarm bell that rings whenever your Java program tries to talk to the "outside world" (the hard drive, the network, the keyboard) and something goes terribly wrong.

<!-- TOC --><a name="why-do-we-need-it-1"></a>
### Why do we need it?
Java is obsessed with safety. When you try to start a server on Port 8080, what if Skype or a totally different Node.js app is already using Port 8080? 

The Operating System will block Java from opening the door. Because this failure happens *outside* of Java's control, Java **forces** you to write a disaster plan (a `try/catch` block) before it even lets you compile the code. If you don't import `IOException` and handle it, Java throws a tantrum and refuses to run.


<!-- TOC --><a name="ascii-diagram-the-disaster-scenario"></a>
### ASCII Diagram: The Disaster Scenario
```text
  [ YOUR JAVA APP ] --------> "Hey OS, give me Port 8080!"
                                        |
  [ OPERATING SYSTEM ]                  v
     |--- Port 80 is free.        [ PORT 8080 is locked by Skype! ]
     |--- Port 443 is free.             |
                                        v
  [ ALARM BELL RINGS ] <----- (Throws IOException)
          |
  [ CATCH BLOCK ] ---> Prints: "Failed to start server. Port in use!" (Program doesn't crash completely)
```


<!-- TOC --><a name="3-comparison-javascript-nodejs"></a>
### 3. Comparison: JavaScript & Node.js

Node.js handles both of these concepts in a much more relaxed, invisible way.

<!-- TOC --><a name="the-address-nodejs"></a>
#### The Address (Node.js)
In Node, you don't need a special `InetSocketAddress` object. You just pass the raw number directly into the `listen()` function. Under the hood, Node.js builds the network binding for you.

```javascript
// Node.js doesn't need an object, just the raw number
server.listen(8080); 
```

<!-- TOC --><a name="the-disaster-plan-nodejs"></a>
#### The Disaster Plan (Node.js)
Node.js does not use "Checked Exceptions." It will not force you to write a `try/catch` block before you run your code. 

If Port 8080 is busy in Node.js, the server will try to start, fail, and emit an asynchronous `'error'` event. If you didn't write code to listen for that specific event, your Node.js app will just violently crash at runtime with an `EADDRINUSE` error.

```javascript
// Node.js way of handling the IOException equivalent
server.on('error', (err) => {
    if (err.code === 'EADDRINUSE') {
        console.log("Failed to start server. Port in use!");
    }
});
```


<!-- TOC --><a name="4-summary-table"></a>
### 4. Summary Table

| Concept | Java Approach | Node.js Approach |
| :--- | :--- | :--- |
| **Defining the Port** | Requires strict `InetSocketAddress` object | Accepts a simple `int` directly |
| **Handling Network Errors** | Forced `try/catch` with `IOException` | Optional `.on('error')` event listener |
| **Philosophy** | Strict, explicit, and forces you to prepare for the worst. | Flexible, implicit, and relies on developer discipline to handle errors. |

<!-- TOC --><a name="part-2-the-router-contexts-and-directing-traffic"></a>
## Part 2: The Router (Contexts) and Directing Traffic

Right now, our server has a door (Port 8080), but if a web browser walks in and says, *"I want to see the /login page,"* our server just stares blankly. It needs a **Router**.

In Java's built-in HTTP library, a Router is called a **Context**. Think of it like a receptionist sitting in the lobby of your server.


<!-- TOC --><a name="1-the-non-trivial-concept-the-prefix-trap"></a>
### 1. The Non-Trivial Concept: The "Prefix" Trap

Before we write the code, we must understand how Java reads URLs. 

When you create a Context in Java, you are creating a **Prefix Matcher**, not an *exact* matcher. This trips up almost every beginner.

If you create a Context for `/`, you might think it only handles the exact homepage (e.g., `localhost:8080/`). But because `/` is the *prefix* for literally everything (`/home`, `/about`, `/secret-files`), a Context for `/` will accidentally swallow **every single request** unless you make more specific Contexts!

<!-- TOC --><a name="ascii-diagram-the-receptionists-rules"></a>
#### ASCII Diagram: The Receptionist's Rules
```text
[ INCOMING REQUEST: "GET /store/shoes" ]
          |
          v
[ THE JAVA RECEPTIONIST (Router) ]
   |
   +-- Rule 1: Do I have a Context for "/store/shoes"? -> NO.
   |
   +-- Rule 2: Do I have a Context for "/store"? ------> YES! (Sends to StoreHandler)
   |
   +-- Rule 3: Do I have a Context for "/"? -----------> (The Catch-All Backup)
```
*Java always checks for the most specific, longest matching Context first.*


<!-- TOC --><a name="2-java-building-the-contexts"></a>
### 2. Java: Building the Contexts

To build the router, we use `server.createContext()`. It takes two arguments:
1.  **The Path** (The String URL, like `/home`)
2.  **The Handler** (The "Kitchen" that will actually build the webpage. We will deep-dive into Handlers in Part 3, so for now, we will just use placeholders).

<!-- TOC --><a name="the-java-code-part-2"></a>
#### The Java Code (Part 2)
```java
import com.sun.net.httpserver.HttpServer;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;
import java.net.InetSocketAddress;

public class MyMasterServer {
    public static void main(String[] args) throws Exception {
        
        HttpServer server = HttpServer.create(new InetSocketAddress(8080), 0);
        
        // --- STEP 2: THE ROUTER (CONTEXTS) ---
        
        // 1. A specific page
        server.createContext("/login", new LoginHandler());
        
        // 2. Another specific page
        server.createContext("/home", new HomeHandler());
        
        // 3. The "Catch-All" (Must be just "/")
        // If they ask for "/about" and it doesn't exist, it falls down to this one!
        server.createContext("/", new DefaultHandler());
        
        server.start();
        System.out.println("Server is running with 3 routes...");
    }

    // (Placeholder Handlers for Part 3)
    static class LoginHandler implements HttpHandler { 
        public void handle(HttpExchange t) {} 
    }
    static class HomeHandler implements HttpHandler { 
        public void handle(HttpExchange t) {} 
    }
    static class DefaultHandler implements HttpHandler { 
        public void handle(HttpExchange t) {} 
    }
}
```

<!-- TOC --><a name="3-comparison-javascript-nodejs-1"></a>
### 3. Comparison: JavaScript & Node.js

Node.js approaches routing entirely differently. In bare-bones Node.js, there is no "receptionist" built in. You don't map paths to Handlers beforehand. 

Instead, the server just dumps every single request into one giant function, and you have to act as the receptionist yourself using `if / else` statements.

<!-- TOC --><a name="ascii-diagram-the-nodejs-funnel"></a>
#### ASCII Diagram: The Node.js Funnel
```text
[ /login ] [ /home ] [ /about ]
       \       |       /
        \      |      /
      [ ONE GIANT FUNCTION ]
               |
         if (url == '/login') -> Do Login
         else if (url == '/home') -> Do Home
         else -> 404 Not Found
```

<!-- TOC --><a name="the-nodejs-code-part-2"></a>
#### The Node.js Code (Part 2)
```javascript
const http = require('http');

const server = http.createServer((request, response) => {
    
    // We are the receptionist now! We check request.url manually.
    if (request.url === '/login') {
        // Handle Login
    } 
    else if (request.url === '/home') {
        // Handle Home
    } 
    else if (request.url === '/') {
        // Handle Default Homepage
    }
    else {
        // We have to manually write the "Catch-All" 404 Error!
        response.writeHead(404);
        response.end("Page Not Found");
    }
    
});

server.listen(8080);
```


<!-- TOC --><a name="4-summary-table-1"></a>
### 4. Summary Table

| Feature | Java `HttpServer` | Bare-bones Node.js `http` |
| :--- | :--- | :--- |
| **How to Route** | `createContext("/path", Handler)` | Manual `if(req.url === '/path')` |
| **Matching Logic** | Prefix Matching (e.g., `/app` catches `/app/users`) | Exact String Matching (unless you write custom Regex logic) |
| **Catch-All (404s)** | `createContext("/", DefaultHandler)` | The final `else { }` block |
| **Architecture** | Object-Oriented (One Class per Route) | Procedural (One giant IF block) |

*(Note: Because the Node.js way gets very messy when you have 100 pages, Node.js developers almost always download a 3rd-party library called **Express.js** to make it look exactly like the Java Context system!)*


<!-- TOC --><a name="part-3-the-handler-the-kitchen-and-serving-the-webpage"></a>
## Part 3: The Handler (The Kitchen) and Serving the Webpage

Our server is listening on Port 8080 (Part 1), and our Router knows that if someone goes to `/home`, it should send them to the `HomeHandler` (Part 2). 

Now, we actually have to build the `HomeHandler`. This is where we read what the user wants and bake the HTML to send back to them.

<!-- TOC --><a name="1-the-non-trivial-concept-the-httpexchange-box"></a>
### 1. The Non-Trivial Concept: The `HttpExchange` Box

In many programming languages, when a user connects, you are handed two separate items: a **Request** (what they want) and a **Response** (what you will send back). 

Java does things differently. It hands you a single, unified box called an **`HttpExchange`**. This box represents the entire conversation. 

**The Golden Rule of HttpExchange:** You must do things in a strictly chronological order. 
1. Check the request.
2. Send the "Headers" (the metadata, like the 200 OK success code).
3. Send the "Body" (the actual text or HTML).
4. Close the box.

If you try to send the HTML body *before* you send the Headers, Java will panic and crash the connection.

<!-- TOC --><a name="ascii-diagram-the-golden-order"></a>
#### ASCII Diagram: The Golden Order
```text
[ THE HTTPEXCHANGE BOX ]
          |
          |-- STEP 1: Read the Request 
          |           "Is this a GET (read) or POST (submit)?"
          |
          |-- STEP 2: Send Headers (MUST BE DONE BEFORE STEP 3)
          |           "200 OK! I am sending you 45 bytes of text."
          |
          |-- STEP 3: Open the Output Pipe & Write Data
          |           "<html><h1>Hello!</h1></html>"
          |
          +-- STEP 4: Close the Pipe
                      (If you forget this, the browser spins forever!)
```


<!-- TOC --><a name="2-java-writing-the-handler"></a>
### 2. Java: Writing the Handler

Let's write the exact code for the `HomeHandler` we registered in Part 2. 

To create a Handler, we must create a class that implements Java's `HttpHandler` interface. This forces us to write a `handle()` method.

<!-- TOC --><a name="the-java-code-part-3"></a>
#### The Java Code (Part 3)
```java
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;
import java.io.IOException;
import java.io.OutputStream;

// We implement the interface, which forces us to write the "handle" method
public class HomeHandler implements HttpHandler {
    
    @Override
    public void handle(HttpExchange exchange) throws IOException {
        
        // 1. Check the request method (GET, POST, etc.)
        String requestMethod = exchange.getRequestMethod();
        System.out.println("User made a " + requestMethod + " request to /home");
        
        // 2. Prepare the food (The HTML response)
        String htmlResponse = "<html><body><h1>Welcome to the Java Kitchen!</h1></body></html>";
        
        // 3. Send the Headers (Status 200 = OK. We also tell it how long the text is)
        // Note: .getBytes().length is required because Java counts raw bytes, not letters!
        exchange.sendResponseHeaders(200, htmlResponse.getBytes().length);
        
        // 4. Open the pipe to the user's browser
        OutputStream outputPipe = exchange.getResponseBody();
        
        // 5. Push the HTML down the pipe
        outputPipe.write(htmlResponse.getBytes());
        
        // 6. Close the pipe! (Crucial)
        outputPipe.close();
    }
}
```


<!-- TOC --><a name="3-comparison-javascript-nodejs-2"></a>
### 3. Comparison: JavaScript & Node.js

Node.js developers do not get a single `HttpExchange` box. Instead, the Node.js server automatically splits the conversation into two separate objects for you right from the start: `req` (Request) and `res` (Response).

However, the **Golden Rule** still applies! You must write the Headers before you send the Body, and you must end the response.

<!-- TOC --><a name="ascii-diagram-java-vs-nodejs-objects"></a>
#### ASCII Diagram: Java vs. Node.js Objects
```text
JAVA'S APPROACH:
[ HttpExchange ] ---> Contains BOTH Request data and Response tools.

NODE.JS APPROACH:
[ Request (req) ] ---> Only contains what the user asked for.
[ Response (res) ] --> Only contains tools to send data back.
```

<!-- TOC --><a name="the-nodejs-code-part-3"></a>
#### The Node.js Code (Part 3)
```javascript
// Inside the server callback from Part 2...

if (request.url === '/home') {
    
    // 1. Check the request method
    console.log("User made a " + request.method + " request to /home");
    
    // 2. Prepare the food
    const htmlResponse = "<html><body><h1>Welcome to the Node Kitchen!</h1></body></html>";
    
    // 3. Send the Headers (Status 200 = OK)
    // Node.js calculates the byte length automatically, so we just set the Content-Type.
    response.writeHead(200, { 'Content-Type': 'text/html' });
    
    // 4 & 5 & 6. Write the body AND close the pipe all in one command!
    response.end(htmlResponse);
}
```


<!-- TOC --><a name="4-summary-table-2"></a>
### 4. Summary Table

| Step | Java (`HttpExchange`) | Node.js (`req` / `res`) |
| :--- | :--- | :--- |
| **Get HTTP Method** | `exchange.getRequestMethod()` | `req.method` |
| **Send Headers** | `exchange.sendResponseHeaders(200, length)` | `res.writeHead(200, {...})` |
| **Write Body** | `OutputStream os = exchange.getResponseBody(); os.write(bytes);` | `res.write(string)` or `res.end(string)` |
| **Close Connection**| `os.close()` | `res.end()` |

<!-- TOC --><a name="the-byte-calculation-trap"></a>
#### The Byte Calculation Trap
Notice in the Java code we used `htmlResponse.getBytes().length`. 

If you just type `htmlResponse.length()`, Java counts the number of *characters*. But emojis and special symbols take up multiple bytes! If you send the character count instead of the byte count, and your HTML contains an emoji, the browser will chop off the last few letters of your webpage because the size calculation was wrong! Node.js handles this math for you securely behind the scenes.

<!-- TOC --><a name="part-4-reading-incoming-data-get-vs-post"></a>
## Part 4: Reading Incoming Data (GET vs. POST)

Up until now, our server has only been talking *to* the user. Now, we are going to listen. When a user sends data to a server, they usually do it in one of two ways:

1. **GET Request (The URL variables):** Like searching for shoes on a website: `localhost:8080/search?item=shoes`
2. **POST Request (The Body):** Like submitting a massive registration form with passwords and files. This data is hidden inside the HTTP package, not the URL.

<!-- TOC --><a name="1-the-non-trivial-concept-no-magic-dictionaries"></a>
### 1. The Non-Trivial Concept: No Magic Dictionaries

In modern web frameworks (like Spring Boot for Java or Express for Node.js), if a user sends `?name=John&age=25`, the framework magically hands you an easy-to-use dictionary object where you just ask for `data.get("name")`.

When you build a server from *scratch* using the basic packages, **there is no magic**. The server just hands you the raw, unformatted text string: `"name=John&age=25"`. You are entirely responsible for chopping that string into pieces using string manipulation!

<!-- TOC --><a name="ascii-diagram-the-raw-data-problem"></a>
#### ASCII Diagram: The Raw Data Problem
```text
[ BROWSER ] ---> Sends: /profile?name=John&age=25 ---> [ YOUR SERVER ]

[ THE MAGIC WAY (Frameworks) ]          [ THE SCRATCH WAY (What we have to do) ]
data.name == "John"                     1. Get raw string: "name=John&age=25"
data.age == 25                          2. Split by "&" -> ["name=John", "age=25"]
                                        3. Split by "=" -> ["name", "John"]
```


<!-- TOC --><a name="2-java-reading-get-requests-query-parameters"></a>
### 2. Java: Reading GET Requests (Query Parameters)

Let's write a Handler that reads the URL to see what the user searched for. We use `exchange.getRequestURI().getQuery()` to grab everything after the `?` mark.

<!-- TOC --><a name="the-java-code-reading-get"></a>
#### The Java Code (Reading GET)
```java
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;
import java.io.IOException;
import java.io.OutputStream;
import java.net.URI;

public class SearchHandler implements HttpHandler {
    @Override
    public void handle(HttpExchange exchange) throws IOException {
        
        // 1. Grab the URI (The full web address)
        URI requestURI = exchange.getRequestURI();
        
        // 2. Extract just the query part (e.g., "item=shoes&color=red")
        String query = requestURI.getQuery();
        
        String responseText = "";
        
        if (query != null) {
            // We have to parse it manually!
            // This splits "item=shoes" into an array: ["item", "shoes"]
            String[] keyValuePair = query.split("="); 
            
            if (keyValuePair.length == 2) {
                responseText = "You searched for: " + keyValuePair[1];
            }
        } else {
            responseText = "You didn't search for anything!";
        }
        
        // 3. Send back the response
        exchange.sendResponseHeaders(200, responseText.getBytes().length);
        OutputStream os = exchange.getResponseBody();
        os.write(responseText.getBytes());
        os.close();
    }
}
```


<!-- TOC --><a name="3-java-reading-post-requests-the-body"></a>
### 3. Java: Reading POST Requests (The Body)

If the user submits a form, the data is not in the URL. It is hidden in the `HttpExchange` box as an **InputStream** (a pipe of raw bytes). 

Just like we use an `OutputStream` to push data *out* to the user, we use an `InputStream` to suck data *in* from the user.

<!-- TOC --><a name="ascii-diagram-the-inputstream-pipe"></a>
#### ASCII Diagram: The InputStream Pipe
```text
[ USER SUBMITS FORM ]
"username=admin&pass=123"
         |
         v
[ INTERNET WIRE ]
         |
         v
[ InputStream (The Intake Pipe) ] ---> [ JAVA: Reads Bytes ] ---> Converts to String
```

<!-- TOC --><a name="the-java-code-reading-post"></a>
#### The Java Code (Reading POST)
```java
import java.io.InputStream;
import java.io.InputStreamReader;
import java.io.BufferedReader;
// ... other imports ...

public class FormHandler implements HttpHandler {
    @Override
    public void handle(HttpExchange exchange) throws IOException {
        
        // Only accept POST requests here
        if ("POST".equalsIgnoreCase(exchange.getRequestMethod())) {
            
            // 1. Get the Intake Pipe
            InputStream is = exchange.getRequestBody();
            
            // 2. Create a Reader to translate raw bytes into text
            InputStreamReader isr = new InputStreamReader(is, "utf-8");
            BufferedReader reader = new BufferedReader(isr);
            
            // 3. Read the incoming text
            // Note: For large files, you'd use a loop. For simple forms, readLine() works.
            String formData = reader.readLine(); 
            
            System.out.println("User submitted: " + formData);
            
            // 4. Send a success message back
            String response = "Form received!";
            exchange.sendResponseHeaders(200, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}
```


<!-- TOC --><a name="4-comparison-javascript-nodejs"></a>
### 4. Comparison: JavaScript & Node.js

Node.js is identical in concept: there is no magic dictionary built into the raw `http` module either. However, how Node reads the POST body is drastically different because of its Event-Driven architecture.

Instead of opening a pipe and actively reading from it like Java, Node.js waits for the data to splash against it in "chunks."

<!-- TOC --><a name="ascii-diagram-nodejs-data-chunks"></a>
#### ASCII Diagram: Node.js Data Chunks
```text
[ BROWSER ] ---> Sends large form data
                       |
[ NODE SERVER ] <--- (Chunk 1 Event fires) -- "user=adm"
[ NODE SERVER ] <--- (Chunk 2 Event fires) -- "in&pass"
[ NODE SERVER ] <--- (Chunk 3 Event fires) -- "=123"
[ NODE SERVER ] <--- (End Event fires) -----> We stitch it together manually!
```

<!-- TOC --><a name="the-nodejs-code"></a>
#### The Node.js Code
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    
    if (req.method === 'POST' && req.url === '/submit') {
        let body = '';
        
        // 1. Listen for data chunks splashing in
        req.on('data', (chunk) => {
            body = body + chunk.toString(); // Stitch it together
        });
        
        // 2. Listen for the end of the data stream
        req.on('end', () => {
            console.log("User submitted: " + body);
            
            res.writeHead(200);
            res.end("Form received!");
        });
    }
});
```

<!-- TOC --><a name="5-summary-table"></a>
### 5. Summary Table

| Action | Java | JavaScript / Node.js |
| :--- | :--- | :--- |
| **Get URL Query** | `exchange.getRequestURI().getQuery()` | `req.url` (Requires manual splitting) |
| **Get POST Body** | Use `exchange.getRequestBody()` (InputStream) | Listen to `req.on('data')` events |
| **Data Format** | Raw Bytes -> Requires `BufferedReader` | Buffer Chunks -> Requires `.toString()` |
| **Parsing Data** | Manual String splitting (`.split("=")`) | Manual String splitting |

Right now, your server can listen, route, speak, and read. It is fully functional! 

But what happens if 5,000 users try to submit that form at the exact same millisecond? Our current Java server will process them one by one, making the 5,000th user wait a very long time.

<!-- TOC --><a name="part-5-concurrency-and-threading"></a>
## Part 5: Concurrency and Threading

Let's dive much deeper into **Part 5: Concurrency and Threading**. This is the difference between a server you build for a school project and a server you deploy to millions of users.

To truly understand why Thread Pools are magic, we first have to see what happens when a server completely breaks down under pressure.


<!-- TOC --><a name="1-the-non-trivial-problem-the-blocking-nightmare"></a>
### 1. The Non-Trivial Problem: The "Blocking" Nightmare

Imagine you have two web pages on your server:
1.  `/fast`: A simple text page that loads instantly.
2.  `/slow`: A page that downloads a massive file or calculates a huge database report. It takes exactly **5 seconds** to finish.

If you don't use an Executor (by setting it to `null`), your Java server operates on the **Main Thread**. It can only do one single thing at a time. 

If User A goes to `/slow`, the server stops everything and waits for 5 seconds. If User B goes to `/fast` just one millisecond later, **User B's browser will spin and freeze for 5 seconds**, even though their page is supposed to be instant!

<!-- TOC --><a name="ascii-diagram-the-blocking-timeline"></a>
#### ASCII Diagram: The Blocking Timeline
```text
TIME (Seconds):   0...1...2...3...4...5...6...
                  |---|---|---|---|---|---|---
User A (/slow):   [========= COOKING ========] (Gets food at 5s)
User B (/fast):    (Waiting in the cold...)  |[ COOKING ] (Gets food at 6s!)
```
User B had to wait for User A's heavy math to finish. This is terrible user experience.


<!-- TOC --><a name="2-javas-solution-the-executorservice"></a>
### 2. Java's Solution: The `ExecutorService`

Java solves this by creating an `ExecutorService` using the `Executors` factory. Instead of the Main Thread doing the cooking, the Main Thread becomes a pure "Dispatcher." It just answers the door, grabs a Worker Thread from the "Pool," hands them the request, and goes back to the door.

You have two main choices for your Thread Pool:

<!-- TOC --><a name="option-a-newfixedthreadpool10"></a>
#### Option A: `newFixedThreadPool(10)`
* **What it does:** Hires exactly 10 workers when the server starts. They never leave, and no more are ever hired.
* **Best for:** Standard, predictable web traffic. It protects your computer's RAM from overflowing because you strictly limit the number of workers.

<!-- TOC --><a name="option-b-newcachedthreadpool"></a>
#### Option B: `newCachedThreadPool()`
* **What it does:** Starts with 0 workers. If 100 people connect at once, it instantly creates 100 workers. If a worker sits idle for 60 seconds, they are fired (destroyed) to save memory.
* **Best for:** Traffic that has massive, sudden spikes (like selling concert tickets) but is usually quiet.


<!-- TOC --><a name="3-the-complete-java-example-simulating-the-fix"></a>
### 3. The Complete Java Example (Simulating the Fix)

Here is the complete, runnable code demonstrating how the `FixedThreadPool` saves the day. We simulate a 5-second delay using `Thread.sleep(5000)`.

```java
import com.sun.net.httpserver.HttpServer;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;
import java.net.InetSocketAddress;
import java.io.IOException;
import java.io.OutputStream;
import java.util.concurrent.Executors; // The Thread Pool Manager

public class ConcurrentServer {
    public static void main(String[] args) throws Exception {
        
        HttpServer server = HttpServer.create(new InetSocketAddress(8080), 0);
        
        // 1. Create the routes
        server.createContext("/fast", new FastHandler());
        server.createContext("/slow", new SlowHandler());
        
        // 2. THE MAGIC FIX: We hire 10 workers!
        // Try changing this to 'null' later and watch how User B gets blocked.
        server.setExecutor(Executors.newFixedThreadPool(10)); 
        
        server.start();
        System.out.println("Multi-Threaded Server running on port 8080...");
    }

    // --- THE INSTANT KITCHEN ---
    static class FastHandler implements HttpHandler {
        @Override
        public void handle(HttpExchange exchange) throws IOException {
            String response = "That was fast!";
            exchange.sendResponseHeaders(200, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
            System.out.println("Served /fast request!");
        }
    }

    // --- THE 5-SECOND KITCHEN ---
    static class SlowHandler implements HttpHandler {
        @Override
        public void handle(HttpExchange exchange) throws IOException {
            try {
                // We force this specific worker thread to freeze for 5 seconds
                System.out.println("Starting /slow request... this will take 5 seconds.");
                Thread.sleep(5000); 
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            
            String response = "Finally finished the slow report!";
            exchange.sendResponseHeaders(200, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
            System.out.println("Served /slow request!");
        }
    }
}
```

<!-- TOC --><a name="ascii-diagram-the-thread-pool-timeline"></a>
#### ASCII Diagram: The Thread Pool Timeline
```text
TIME (Seconds):   0...1...2...3...4...5...
                  |---|---|---|---|---|---
User A (/slow):   [========= WORKER 1 IS COOKING =========] (Done at 5s)
User B (/fast):    [ WORKER 2 COOKS ] (Done at 1s!)
```
Because Worker 1 is trapped doing the slow job, the Main Server simply hands User B's request to Worker 2. User B gets their page instantly!


<!-- TOC --><a name="4-comparison-the-nodejs-reality-check"></a>
### 4. Comparison: The Node.js Reality Check

We talked earlier about how Node.js uses a single-threaded Event Loop. 

If the `/slow` request in Node.js is waiting for a database to return data, Node.js handles it beautifully using asynchronous callbacks. The single Node chef puts the database task in the oven and serves User B.

**BUT... what if the `/slow` request is heavy math?** What if the server itself has to encrypt a massive file, or calculate prime numbers in a giant `while` loop?



<!-- TOC --><a name="the-nodejs-cpu-bound-trap"></a>
#### The Node.js "CPU-Bound" Trap
If you force Node.js to do heavy math on its single thread, **the entire server freezes for everyone.** Node.js has no other workers to pass the job to!

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    
    if (req.url === '/slow') {
        // HEAVY MATH: This freezes the ONE AND ONLY thread!
        // No other users can connect while this loop runs.
        let count = 0;
        for (let i = 0; i < 5000000000; i++) {
            count++; 
        }
        res.end("Done with heavy math!");
    } 
    
    else if (req.url === '/fast') {
        // If User A is on '/slow', User B CANNOT reach this code until User A is done!
        res.end("That was fast!");
    }
});

server.listen(8080);
```

<!-- TOC --><a name="how-nodejs-fixes-this-the-modern-way"></a>
#### How Node.js fixes this (The Modern Way)
To match Java's performance on heavy math, Node.js recently introduced `worker_threads`. You have to manually spin up a separate mini-Node.js instance in the background to handle the math, which is much more complicated to code than Java's simple `Executors.newFixedThreadPool(10)`.

| Scenario | Java Server (With Thread Pool) | Node.js Server |
| :--- | :--- | :--- |
| **Waiting for a Database (I/O)** | Worker thread waits. Other users are fine. | Event Loop waits asynchronously. Other users are fine. |
| **Heavy Math (CPU Bound)** | Worker thread does math. Other users are fine! | **Main Thread freezes!** All other users are blocked! |


<!-- TOC --><a name="part-6-handling-json-requests-and-responses"></a>
## Part 6: Handling JSON Requests and Responses

Today, almost no modern web app sends data using the old `name=John&age=25` format we saw in Part 4. They use **JSON (JavaScript Object Notation)**, which looks like this: `{"name": "John", "age": 25}`.

<!-- TOC --><a name="1-the-non-trivial-concept-the-missing-translator"></a>
### 1. The Non-Trivial Concept: The Missing Translator

This is where Java's standard library shows its age. **Java does not have a built-in JSON parser.** If you receive a JSON string in Java, it is just a dumb block of text. To turn that text into a real Java Object, developers almost always download a common third-party library like **Gson** (by Google) or **Jackson**. 

If you refuse to use external libraries, you have to write a custom String-splitter to hunt for quotes and colons, which is an absolute nightmare if the JSON has nested arrays!

<!-- TOC --><a name="ascii-diagram-the-json-translation"></a>
### ASCII Diagram: The JSON Translation
```text
[ BROWSER ] --- Sends: {"user":"John"} ---> [ JAVA SERVER ]

THE MANUAL WAY (Painful):
1. Find index of "user"
2. Find index of ":"
3. Extract text between quotes -> "John"

THE STANDARD WAY (Using the Gson library):
1. Gson.fromJson(jsonText, User.class) -> Instantly creates a Java Object!
```

<!-- TOC --><a name="2-java-sending-and-receiving-json"></a>
### 2. Java: Sending and Receiving JSON

Even without an external library, we can easily *send* and *receive* the raw JSON text. The secret is telling the browser exactly what language we are speaking by setting the **Content-Type Header**.

```java
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;

public class JsonHandler implements HttpHandler {
    @Override
    public void handle(HttpExchange exchange) throws IOException {
        
        // 1. RECEIVING JSON (Exactly like reading a POST body in Part 4)
        if ("POST".equalsIgnoreCase(exchange.getRequestMethod())) {
            InputStream is = exchange.getRequestBody();
            String incomingJson = new String(is.readAllBytes()); 
            System.out.println("Received raw JSON text: " + incomingJson);
        }

        // 2. SENDING JSON BACK
        String responseJson = "{ \"status\": \"success\", \"message\": \"Hello JSON!\" }";
        
        // 3. THE MAGIC HEADER: Tell the browser this is JSON, not HTML!
        exchange.getResponseHeaders().set("Content-Type", "application/json");
        
        // 4. Send the response
        exchange.sendResponseHeaders(200, responseJson.getBytes().length);
        OutputStream os = exchange.getResponseBody();
        os.write(responseJson.getBytes());
        os.close();
    }
}
```

<!-- TOC --><a name="3-comparison-javascript-nodejs-3"></a>
### 3. Comparison: JavaScript & Node.js

Node.js absolutely destroys Java here. Because JSON stands for *JavaScript* Object Notation, the Node.js engine understands it natively. `JSON.parse()` and `JSON.stringify()` are built right into the language.

```javascript
// Node.js JSON Handling
const http = require('http');

const server = http.createServer((req, res) => {
    let body = '';
    req.on('data', chunk => { body += chunk.toString(); });
    
    req.on('end', () => {
        // 1. Built-in magic! Turns text into a real Object instantly.
        const userObj = JSON.parse(body); 
        console.log("Received name: " + userObj.name);

        // 2. Set the magic header
        res.writeHead(200, { 'Content-Type': 'application/json' });
        
        // 3. Built-in magic! Turns Object back into text.
        res.end(JSON.stringify({ status: "success", message: "Hello JSON!" }));
    });
});
```


<!-- TOC --><a name="part-7-handling-auth-cookies-jwts"></a>
## Part 7: Handling Auth (Cookies & JWTs)

HTTP has the memory of a goldfish. It is **Stateless**. If you log in at 1:00 PM, and click a link at 1:01 PM, the server has absolutely no idea who you are. 

To fix this, the server gives the browser a "Name Tag" (a Cookie or a JWT token) when they log in. Every time the browser makes a new request, it must wear that Name Tag.

<!-- TOC --><a name="1-the-non-trivial-concept-the-headers-vault"></a>
### 1. The Non-Trivial Concept: The "Headers" Vault

Where do we put the Name Tag? We don't put it in the URL (too easily stolen), and we don't put it in the body. We put it in the **HTTP Headers**.

* **Cookies:** Sent via the `Cookie` header.
* **JWT (JSON Web Tokens):** Sent via the `Authorization` header, usually looking like `Bearer eyJhbGciOi...`

<!-- TOC --><a name="ascii-diagram-the-bouncer-at-the-club"></a>
### ASCII Diagram: The Bouncer at the Club
```text
[ REQUEST 1: LOG IN ] ---> [ JAVA BARKEEP ] ---> "Valid password. Here is a VIP wristband (JWT)."
                                |
[ REQUEST 2: /secure ] --> [ JAVA BOUNCER ]
     (Wears Wristband)          |
                                +---> Checks 'Authorization' Header.
                                +---> "Ah, I see the wristband. Go right in!"
```

<!-- TOC --><a name="2-java-reading-the-headers"></a>
### 2. Java: Reading the Headers

To build our "Bouncer," we just need to pull the `Headers` object out of our `HttpExchange` box and check for the `Authorization` key.

```java
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.Headers;
import java.io.IOException;
import java.io.OutputStream;

public class SecureHandler implements HttpHandler {
    @Override
    public void handle(HttpExchange exchange) throws IOException {
        
        // 1. Grab all the incoming headers from the browser
        Headers headers = exchange.getRequestHeaders();
        
        // 2. Look for the "Authorization" header
        // getFirst() is used because a header can technically have multiple values
        String authHeader = headers.getFirst("Authorization");
        
        // 3. The Bouncer Logic
        if (authHeader != null && authHeader.startsWith("Bearer ")) {
            
            // Extract just the token part (remove the word "Bearer ")
            String token = authHeader.substring(7);
            
            // (In a real app, you would verify the JWT math here)
            if (token.equals("super-secret-jwt-token-123")) {
                sendResponse(exchange, 200, "Welcome to the VIP area!");
                return;
            }
        }
        
        // 4. Kicked out! (401 Unauthorized)
        sendResponse(exchange, 401, "Access Denied! Go away.");
    }
    
    // Helper method to keep code clean
    private void sendResponse(HttpExchange exchange, int statusCode, String response) throws IOException {
        exchange.sendResponseHeaders(statusCode, response.getBytes().length);
        OutputStream os = exchange.getResponseBody();
        os.write(response.getBytes());
        os.close();
    }
}
```

<!-- TOC --><a name="3-comparison-javascript-nodejs-4"></a>
### 3. Comparison: JavaScript & Node.js

Node.js puts all the headers into a simple `req.headers` dictionary. Note that Node.js automatically converts all header names to **lowercase** to avoid confusion, so you look for `req.headers.authorization` instead of `Authorization`.

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
    
    // 1. The Bouncer Logic (Node automatically lowercases header keys)
    const authHeader = req.headers.authorization;
    
    if (authHeader && authHeader.startsWith("Bearer ")) {
        
        const token = authHeader.split(" ")[1]; // Grab the second word
        
        if (token === "super-secret-jwt-token-123") {
            res.writeHead(200);
            return res.end("Welcome to the VIP area!");
        }
    }
    
    // 2. Kicked out!
    res.writeHead(401);
    res.end("Access Denied! Go away.");
});
```


<!-- TOC --><a name="4-summary-table-json-and-auth"></a>
## 4. Summary Table: JSON and Auth

| Feature | Java | JavaScript / Node.js |
| :--- | :--- | :--- |
| **Parsing JSON** | Requires 3rd-party library (Gson/Jackson) | Built-in (`JSON.parse()`) |
| **Sending JSON** | Convert String to Bytes + Set `Content-Type` Header | `JSON.stringify()` + Set Header |
| **Reading Auth Headers**| `exchange.getRequestHeaders().getFirst("Authorization")` | `req.headers.authorization` |
| **Header Capitalization**| Case-sensitive depending on how you search | Automatically lowercased by Node |
