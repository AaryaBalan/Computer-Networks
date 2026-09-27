# Chapter 3: Client-Server Architecture

> **Topic:** How the Internet Actually Works — Client, Server, Requests, Responses, Protocols, HTTP Methods, Status Codes, Network Requests, and More

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [What Is a Client?](#2-what-is-a-client)
3. [What Is a Server?](#3-what-is-a-server)
4. [Client-Server Architecture](#4-client-server-architecture)
5. [Example: Opening google.com](#5-example-opening-googlecom)
6. [Can Your Computer Be a Server?](#6-can-your-computer-be-a-server)
7. [Client and Server on the Same Computer](#7-client-and-server-on-the-same-computer)
8. [What Actually Happens When a Web Page Loads?](#8-what-actually-happens-when-a-web-page-loads)
9. [Browser Developer Tools](#9-browser-developer-tools)
10. [The Network Tab](#10-the-network-tab)
11. [What Is a Request?](#11-what-is-a-request)
12. [What Is a Response?](#12-what-is-a-response)
13. [GET Request](#13-get-request)
14. [POST Request](#14-post-request)
15. [HTTP Methods](#15-http-methods)
16. [Status Codes](#16-status-codes)
17. [HTML, JavaScript, JSON, PNG and Other Resources](#17-html-javascript-json-png-and-other-resources)
18. [What Is an IP Address?](#18-what-is-an-ip-address)
19. [How Does google.com Become an IP Address?](#19-how-does-googlecom-become-an-ip-address)
20. [What Are Protocols?](#20-what-are-protocols)
21. [What Do the Network Tab Columns Mean?](#21-what-do-the-network-tab-columns-mean)
22. [Domain](#22-domain)
23. [Status](#23-status)
24. [Initiator](#24-initiator)
25. [Type](#25-type)
26. [Transferred](#26-transferred)
27. [Size](#27-size)
28. [Time](#28-time)
29. [Deep Why Questions](#29-deep-why-questions)
30. [Hands-On Experiment](#30-hands-on-experiment)
31. [Mental Model](#31-mental-model)
32. [Chapter Summary](#32-chapter-summary)
33. [Questions to Test Yourself](#33-questions-to-test-yourself)

---

# 1. Introduction

We generally know **what the Internet is**, and we may know how the Internet started.

But knowing *what* something is and knowing *how* it works internally are two completely different things.

For example:

> You know that typing `google.com` opens Google.

But:

> How does your computer know where Google is?
>
> How does the request travel from your computer to Google?
>
> How does Google know what you requested?
>
> How does Google send the response back?
>
> How does the browser convert that response into the webpage you see?

These are the questions that Client-Server Architecture begins to answer.

---

# 2. What Is a Client?

## Definition

A **client** is a device or software application that sends a request to another system to obtain some service or resource.

In web applications, the browser running on your computer or phone commonly acts as the client.

### Example

You open your browser and type:

```text
google.com
````

Your browser sends a request to Google's servers.

Therefore:

Your Browser → Client
Google Server → Server

---

## Simple Analogy

Think of a restaurant.

You = customer

Waiter = communication interface

Kitchen = server

You ask:

> "Give me a pizza."

The kitchen prepares the pizza and gives it back through the waiter.

Similarly:

```text
Client
   |
   | Request
   ↓
Server
   |
   | Response
   ↓
Client
```

---

# 3. What Is a Server?

## Definition

A **server** is a system that receives requests from clients and provides the requested service, data, or resource.

For example, Google's servers receive requests from browsers and return the resources required to construct Google's webpage.

---

## Simple Analogy

Imagine a library.

You are the client.

You ask:

> "Give me this book."

The librarian/system searches for the book and gives it to you.

```text
You
 ↓
Request
 ↓
Library
 ↓
Response
 ↓
Book
```

Similarly:

```text
Browser
   ↓
Request
   ↓
Google Server
   ↓
Response
   ↓
Web Page / Resources
```

---

# 4. Client-Server Architecture

Client-server architecture is a model in which two sides communicate:

* **Client**
* **Server**

The client requests something.

The server processes that request and sends back a response.

### Basic flow

```text
        REQUEST
Client ───────────────→ Server
       ←───────────────
        RESPONSE
```

---

## Example

You type:

```text
google.com
```

The browser sends a request.

```text
Browser
   |
   | "I want google.com"
   ↓
Google Server
```

Google's server processes the request and sends resources back.

```text
Google Server
   |
   | HTML + CSS + JS + Images + Data
   ↓
Browser
```

The browser then uses those resources to construct the webpage.

---

# 5. Example: Opening google.com

Let's understand the simplified version first.

Suppose your computer is:

```text
YOUR COMPUTER
```

You open a browser and type:

```text
google.com
```

You press Enter.

### Step 1 — Client creates a request

Your browser acts as the client.

```text
Browser
   |
   | Request
   ↓
Google Server
```

### Step 2 — Google receives the request

Google's server receives the request.

The server essentially says:

> "I received a request. Let me provide what was requested."

### Step 3 — Server sends a response

Google sends resources back.

For example:

```text
HTML
CSS
JavaScript
Images
JSON
Fonts
etc.
```

### Step 4 — Browser processes the response

The browser receives those resources and uses them to construct the webpage.

```text
Browser
   ↓
Receive HTML
   ↓
Parse HTML
   ↓
Request additional resources
   ↓
Receive CSS / JS / Images / JSON
   ↓
Render webpage
```

---

# 6. Can Your Computer Be a Server?

Yes!

Your computer can absolutely act as a server.

A common example is:

```text
localhost
```

For example:

```text
http://localhost:3000
```

Suppose you create a Node.js application:

```javascript
const express = require("express");

const app = express();

app.get("/", (req, res) => {
    res.send("Hello World");
});

app.listen(3000);
```

Now your computer is running a server.

You can open:

```text
http://localhost:3000
```

in your browser.

The architecture becomes:

```text
Same Computer

┌──────────────────────────┐
│        Your PC           │
│                          │
│  Browser = Client        │
│       ↓                  │
│  Node.js = Server        │
│                          │
└──────────────────────────┘
```

---

# 7. Client and Server on the Same Computer

This is an important concept.

A single physical machine can simultaneously act as:

* Client
* Server

For example:

```text
Browser
   |
   | HTTP Request
   ↓
localhost:3000
   |
   ↓
Node.js Server
   |
   | HTTP Response
   ↓
Browser
```

The client and server do not necessarily have to be two different physical computers.

---

## Important Distinction

### Client/Server is about roles.

It is NOT necessarily about physical machines.

A machine can be:

```text
Client
```

in one communication and:

```text
Server
```

in another communication.

---

# 8. What Actually Happens When a Web Page Loads?

When you type:

```text
google.com
```

and press Enter, it may look like one simple action.

Internally, many things happen.

The browser may need to:

1. Find Google's server.
2. Resolve the domain name.
3. Establish network communication.
4. Send an HTTP request.
5. Receive an HTTP response.
6. Receive HTML.
7. Parse the HTML.
8. Discover CSS files.
9. Discover JavaScript files.
10. Discover images.
11. Request those resources.
12. Receive those resources.
13. Execute JavaScript.
14. Construct the page.
15. Render the final result.

So:

```text
One webpage
     ↓
Many network requests
     ↓
Many responses
     ↓
Many resources
```

This is why opening a single website can produce many network requests.

---

# 9. Browser Developer Tools

Modern browsers provide developer tools that allow us to inspect what is happening internally.

For example, in Chrome/Firefox:

```text
Right Click
     ↓
Inspect
     ↓
Network
```

The Network tab allows you to observe the requests made by the webpage.

---

# 10. The Network Tab

Suppose you open:

```text
google.com
```

and open:

```text
Developer Tools → Network
```

Then refresh the page.

You may see many entries.

For example:

```text
Name             Method     Status     Type
------------------------------------------------
google.com       GET        200        document
style.css        GET        200        stylesheet
script.js        GET        200        script
logo.png         GET        200        image
data.json        GET        200        fetch
```

This shows an important fact:

> Loading one webpage can involve many individual requests.

---

# 11. What Is a Request?

A **request** is a message sent by a client to a server asking the server to perform an operation or provide a resource.

For example:

```text
Browser → Server
```

The browser might say conceptually:

```text
GET /index.html
```

Meaning:

> "Please give me `/index.html`."

---

## Request Contains Information

An HTTP request can contain things such as:

```text
Method
URL
Headers
Body
```

For example:

```http
GET /users HTTP/1.1
Host: example.com
```

The exact structure depends on the HTTP version and request.

---

# 12. What Is a Response?

A **response** is the message sent by the server back to the client after processing a request.

```text
Client
  |
  | Request
  ↓
Server
  |
  | Response
  ↓
Client
```

A response can contain:

```text
Status Code
Headers
Body
```

For example:

```http
HTTP/1.1 200 OK
Content-Type: text/html
```

followed by HTML content.

---

# 13. GET Request

One of the most common HTTP methods is:

```text
GET
```

A GET request is generally used to retrieve data or a resource.

Example:

```http
GET /products
```

Conceptually:

> "Give me the products."

Another example:

```text
GET /profile
```

means:

> "Give me the profile resource."

---

## Browser Example

When you enter:

```text
https://google.com
```

the browser commonly makes a GET request for the webpage.

The Network tab may show:

```text
Method: GET
```

---

# 14. POST Request

Another important HTTP method is:

```text
POST
```

POST is commonly used when sending data to a server, often to create something or trigger processing.

Example:

```http
POST /users
```

with a request body such as:

```json
{
    "name": "Aarya",
    "email": "aarya@example.com"
}
```

Conceptually:

```text
Client
   |
   | POST + Data
   ↓
Server
```

The server processes the submitted information.

---

# 15. HTTP Methods

HTTP provides different methods for expressing the intended operation.

Common methods include:

| Method | Common Purpose              |
| ------ | --------------------------- |
| GET    | Retrieve data               |
| POST   | Submit/create/process data  |
| PUT    | Replace/update a resource   |
| PATCH  | Partially update a resource |
| DELETE | Delete a resource           |

Example:

```text
GET /users
```

Retrieve users.

```text
POST /users
```

Create a user.

```text
PATCH /users/10
```

Update part of user 10.

```text
DELETE /users/10
```

Delete user 10.

> The exact behavior is defined by the application's API design, but these are the standard/common semantics.

---

# 16. Status Codes

When the server sends a response, it also sends a **status code**.

Status codes tell the client what happened with the request.

Example:

```text
200
```

means the request was successful.

---

## Common Status Code Categories

HTTP status codes are grouped into five categories.

| Range | Meaning           |
| ----- | ----------------- |
| 1xx   | Informational     |
| 2xx   | Successful        |
| 3xx   | Redirection       |
| 4xx   | Client-side error |
| 5xx   | Server-side error |

---

## 200 OK

```text
200
```

means the request was successfully processed.

Example:

```text
GET /index.html
→ 200 OK
```

---

## 404 Not Found

```text
404
```

generally means the requested resource could not be found.

Example:

```text
GET /does-not-exist
→ 404 Not Found
```

---

## 500 Internal Server Error

```text
500
```

indicates that the server encountered an error while processing the request.

```text
Client
  |
  | Request
  ↓
Server
  |
  | Something went wrong
  ↓
500
```

---

# 17. HTML, JavaScript, JSON, PNG and Other Resources

When you load a website, the server may return different kinds of resources.

For example:

### HTML

```text
index.html
```

Contains the structure of the webpage.

---

### CSS

```text
style.css
```

Controls presentation and styling.

---

### JavaScript

```text
app.js
```

Contains program logic executed by the browser.

---

### PNG

```text
logo.png
```

An image resource.

---

### JSON

```text
users.json
```

Structured data.

Example:

```json
{
    "name": "Aarya",
    "age": 20
}
```

---

## Important Idea

A webpage is not necessarily one file.

It may be composed of:

```text
HTML
 +
CSS
 +
JavaScript
 +
Images
 +
Fonts
 +
JSON/API data
 +
Other resources
```

The browser requests these resources separately.

---

# 18. What Is an IP Address?

A computer communicating over an IP network needs an address so that network traffic can be delivered to the correct destination.

An IP address identifies a network interface/address used for communication.

Examples of IPv4 addresses:

```text
142.250.x.x
8.8.8.8
192.168.1.10
```

There are two major IP versions:

```text
IPv4
IPv6
```

---

## Why Don't We Type IP Addresses?

Imagine having to remember:

```text
142.250.x.x
```

for Google.

That would be inconvenient.

Instead, humans use domain names:

```text
google.com
```

The system that translates domain names into IP addresses is:

```text
DNS
```

---

# 19. How Does google.com Become an IP Address?

This is one of the important questions that the chapter is preparing us to understand.

You type:

```text
google.com
```

But network communication ultimately needs an IP address.

So the system performs DNS resolution.

Conceptually:

```text
google.com
     |
     ↓
    DNS
     |
     ↓
IP Address
```

For example:

```text
google.com
     ↓
DNS lookup
     ↓
IP address
     ↓
Connect to destination
```

> The exact process can involve browser caches, OS caches, DNS resolvers, recursive DNS servers, authoritative DNS servers, and other details. These are part of the deeper networking layers.

---

# 20. What Are Protocols?

A **protocol** is a set of rules that defines how systems communicate.

Imagine two people trying to communicate.

If one person speaks English and the other only understands Japanese, communication becomes difficult.

Computers similarly need agreed rules.

Protocols define things such as:

* How messages are formatted
* How messages are sent
* How data is interpreted
* How errors are handled
* How communication occurs

---

## Examples of Network Protocols

```text
HTTP
HTTPS
DNS
TCP
UDP
IP
```

Each has a different responsibility.

---

## Simple Analogy

Imagine sending a parcel.

You need rules for:

```text
Address
Packaging
Transportation
Delivery
Confirmation
```

Networking protocols similarly define communication rules.

---

# 21. What Do the Network Tab Columns Mean?

When you inspect the Network tab, you may see columns such as:

```text
Name
Method
Status
Domain
Initiator
Type
Transferred
Size
Time
```

Let's understand each one.

---

# 22. Domain

The **domain** identifies the domain/host associated with the request.

Example:

```text
google.com
```

or:

```text
api.example.com
```

A webpage can communicate with multiple domains.

For example:

```text
example.com
api.example.com
cdn.example.com
fonts.example.com
```

---

# 23. Status

The status column shows the HTTP response status.

Examples:

```text
200
301
302
404
500
```

For example:

```text
200 → Successful
404 → Resource not found
500 → Server error
```

---

# 24. Initiator

The **initiator** helps identify what caused a request to happen.

For example, a request may be triggered by:

```text
HTML
JavaScript
CSS
Browser navigation
Another resource
```

Example:

```javascript
fetch("/users");
```

This JavaScript code can cause a network request.

The Network panel can help you trace the request back to the code or resource that initiated it.

---

# 25. Type

The **Type** column tells you what kind of resource/request was involved.

Examples:

```text
document
script
stylesheet
image
font
fetch
xhr
media
```

For example:

```text
index.html → document
app.js     → script
style.css  → stylesheet
logo.png   → image
data.json  → fetch
```

---

# 26. Transferred

The **Transferred** column indicates the amount of data transferred over the network for that resource/request.

For example:

```text
1.2 KB
35 KB
250 KB
2 MB
```

The transferred amount can be affected by things such as compression and caching.

For example, the original resource might be larger than the compressed data sent over the network.

---

# 27. Size

The **Size** column indicates the resource size represented by the browser's network information.

It is important to distinguish:

```text
Transferred
```

from:

```text
Size
```

They may differ.

For example:

```text
Transferred: 20 KB
Size:        100 KB
```

This can happen because the resource may have been compressed during transfer.

Caching can also affect what is transferred.

---

# 28. Time

The **Time** column tells you approximately how long the request took.

Example:

```text
120 ms
850 ms
2.1 s
```

A request's overall time can involve multiple phases, such as:

```text
Queueing
DNS
Connection
TLS
Request
Waiting
Download
```

This is why a request taking:

```text
500 ms
```

doesn't necessarily mean the server spent 500 ms executing application code.

---

# 29. Deep Why Questions

The goal is not just to memorize definitions.

You should be able to answer:

---

## Q1. Why do we need a server?

Because clients often need centralized services or resources that they cannot provide themselves.

For example:

```text
Browser
   ↓
Request user profile
   ↓
Server
   ↓
Database
   ↓
User profile
   ↓
Browser
```

The server can:

* Store data
* Process requests
* Authenticate users
* Access databases
* Apply business logic
* Return results

---

## Q2. Why can't the browser directly access the database?

Because databases are generally kept behind an application/server layer.

A typical architecture is:

```text
Browser
   ↓
Backend Server
   ↓
Database
```

rather than:

```text
Browser
   ↓
Database
```

The backend can enforce:

* Authentication
* Authorization
* Validation
* Business rules
* Security
* Data transformations

---

## Q3. Why does one webpage create many requests?

Because the webpage can depend on many resources.

For example:

```text
HTML
 ↓
CSS
 ↓
JavaScript
 ↓
Images
 ↓
Fonts
 ↓
API data
```

Each resource may require its own request.

Therefore:

```text
1 webpage ≠ 1 request
```

A webpage may require many requests.

---

## Q4. Why do we need HTTP methods?

Because the server needs to understand what the client wants to do.

Compare:

```text
GET /users
```

with:

```text
POST /users
```

The URL can be the same, but the intended operation can be different.

---

## Q5. Why do we need status codes?

The client needs a standardized way to understand the result.

For example:

```text
200 → Success
404 → Not found
500 → Server error
```

Without status information, the client would have less structured information about the result.

---

## Q6. Why do we need domain names if IP addresses exist?

Because domain names are easier for humans to remember.

Instead of:

```text
142.xxx.xxx.xxx
```

we can use:

```text
google.com
```

DNS connects the human-friendly name with network addressing.

---

## Q7. Why can the same computer be both client and server?

Because "client" and "server" describe roles in communication.

For example:

```text
Browser → Client
Node.js → Server
```

on the same physical machine.

The distinction is about who requests and who provides a service in a particular interaction.

---

## Q8. Why does localhost work without the public Internet?

Because your machine can communicate with services running locally.

For example:

```text
Browser
   ↓
localhost:3000
   ↓
Node.js
```

The traffic does not need to travel to Google's servers or across the public Internet.

---

# 30. Hands-On Experiment

The best way to understand client-server architecture is to build one.

## Experiment 1 — Create a Local Server

Create a Node.js project.

```bash
mkdir client-server-demo
cd client-server-demo
npm init -y
npm install express
```

Create:

```text
server.js
```

Add:

```javascript
const express = require("express");

const app = express();

app.get("/", (req, res) => {
    res.send("Hello from the server!");
});

app.listen(3000, () => {
    console.log("Server running on port 3000");
});
```

Run:

```bash
node server.js
```

You should see:

```text
Server running on port 3000
```

---

## Experiment 2 — Open the Client

Open your browser:

```text
http://localhost:3000
```

Architecture:

```text
Browser
  |
  | GET /
  ↓
localhost:3000
  |
  ↓
Express Server
  |
  | "Hello from the server!"
  ↓
Browser
```

---

# Experiment 3 — Inspect the Request

Open:

```text
Developer Tools
→ Network
```

Refresh:

```text
http://localhost:3000
```

Look at the request.

You should observe information such as:

```text
Method: GET
Status: 200
Type: document
```

This directly demonstrates:

```text
Client
   ↓
GET request
   ↓
Server
   ↓
200 response
   ↓
Client
```

---

# Experiment 4 — Create a POST Endpoint

Add:

```javascript
app.use(express.json());

app.post("/users", (req, res) => {
    console.log(req.body);

    res.json({
        message: "User received",
        user: req.body
    });
});
```

Now the server can receive JSON.

Example request:

```http
POST /users
Content-Type: application/json
```

Body:

```json
{
    "name": "Aarya",
    "age": 20
}
```

The server receives:

```javascript
req.body
```

and sends a response.

---

# Experiment 5 — Observe Different Status Codes

Add:

```javascript
app.get("/success", (req, res) => {
    res.status(200).send("Success");
});

app.get("/not-found", (req, res) => {
    res.status(404).send("Not Found");
});

app.get("/error", (req, res) => {
    res.status(500).send("Internal Server Error");
});
```

Now visit:

```text
http://localhost:3000/success
```

You get:

```text
200
```

Visit:

```text
http://localhost:3000/not-found
```

You get:

```text
404
```

Visit:

```text
http://localhost:3000/error
```

You get:

```text
500
```

This makes HTTP status codes much easier to understand.

---

# 31. Mental Model

The most important mental model from this chapter is:

```text
             INTERNET / NETWORK
                    │
                    │
                    ▼
              ┌──────────┐
              │  SERVER  │
              └──────────┘
                    ▲
                    │
              RESPONSE
                    │
                    │
              REQUEST
                    │
                    ▼
              ┌──────────┐
              │  CLIENT  │
              └──────────┘
```

A more realistic web architecture:

```text
                ┌──────────────┐
                │   Browser    │
                │   Client     │
                └──────┬───────┘
                       │
                       │ HTTP Request
                       ▼
                ┌──────────────┐
                │ Web Server / │
                │ Backend      │
                └──────┬───────┘
                       │
                       │ Query
                       ▼
                ┌──────────────┐
                │   Database   │
                └──────┬───────┘
                       │
                       │ Data
                       ▼
                ┌──────────────┐
                │   Backend    │
                └──────┬───────┘
                       │
                       │ HTTP Response
                       ▼
                ┌──────────────┐
                │   Browser    │
                └──────────────┘
```

---

# 32. Chapter Summary

## Client

The system making a request.

Example:

```text
Browser
```

---

## Server

The system providing a service/resource in response to requests.

Example:

```text
Google's servers
```

---

## Request

Message sent by the client to the server.

```text
Client → Server
```

---

## Response

Message sent by the server back to the client.

```text
Server → Client
```

---

## HTTP

A major application-layer protocol used for communication between web clients and servers.

---

## GET

Commonly used to retrieve data/resources.

```text
GET /users
```

---

## POST

Commonly used to submit/create/process data.

```text
POST /users
```

---

## Status Code

Indicates the result/category of an HTTP request.

Examples:

```text
200 → Success
404 → Not Found
500 → Server Error
```

---

## Domain

Human-readable name such as:

```text
google.com
```

---

## IP Address

Network address used for IP communication.

---

## DNS

Translates/resolves domain names to IP addresses through the DNS system.

```text
google.com
     ↓
    DNS
     ↓
IP address
```

---

## Protocol

A set of communication rules.

Examples:

```text
HTTP
HTTPS
DNS
TCP
UDP
IP
```

---

## Network Tab

Browser developer-tool feature that lets you inspect network requests and responses.

---

# 33. Questions to Test Yourself

Before moving to the next chapter, make sure you can answer these without memorizing.

### Basic

1. What is a client?
2. What is a server?
3. What is client-server architecture?
4. What is a request?
5. What is a response?
6. Can one computer be both client and server?
7. What is localhost?
8. What is an IP address?
9. What is a domain name?
10. What is DNS?

### HTTP

11. What is HTTP?
12. What is a GET request?
13. What is a POST request?
14. Why do we need HTTP methods?
15. What is a status code?
16. What does `200` mean?
17. What does `404` mean?
18. What does `500` mean?

### Browser

19. Why does loading one webpage generate multiple requests?
20. What is the Network tab?
21. What is the Domain column?
22. What is the Initiator column?
23. What is the Type column?
24. What does Transferred mean?
25. What does Size mean?
26. What does Time mean?

### Deep Understanding

27. Why can't we simply use IP addresses instead of domain names?
28. Why does a webpage need multiple resources?
29. Why can a single computer act as both client and server?
30. Why does a browser need a server?
31. Why does the browser need HTTP?
32. Why are protocols necessary?
33. Why can Transferred and Size be different?
34. Why can a single page generate dozens or hundreds of requests?
35. What happens between typing `google.com` and seeing the webpage?

---

# The Big Picture

When you type:

```text
https://google.com
```

do NOT think:

```text
I typed a URL → Google appeared
```

Instead, start thinking:

```text
I entered a domain
        ↓
The system needs to resolve the destination
        ↓
A network connection is established
        ↓
The browser sends an HTTP request
        ↓
A server receives the request
        ↓
The server processes it
        ↓
The server sends an HTTP response
        ↓
The browser receives HTML
        ↓
The browser discovers more resources
        ↓
More HTTP requests are made
        ↓
CSS / JavaScript / images / data arrive
        ↓
Browser processes everything
        ↓
The browser renders the webpage
```

That is the beginning of understanding **how the Internet actually works**.

The next level of this topic is to open the Network tab and understand exactly what happens at each stage:

```text
Domain
  ↓
DNS
  ↓
IP Address
  ↓
TCP
  ↓
TLS / HTTPS
  ↓
HTTP
  ↓
Request
  ↓
Server
  ↓
Response
  ↓
Status Code
  ↓
Browser Rendering
```

This is where the simple "client sends request, server sends response" model becomes a real understanding of computer networking.