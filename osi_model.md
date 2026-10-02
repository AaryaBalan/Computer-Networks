# Computer Networks — OSI Model & TCP/IP Model

## Table of Contents

### Chapter 10 — OSI Model

1. [What is the OSI Model?](#1-what-is-the-osi-model)
2. [Why Do We Need the OSI Model?](#2-why-do-we-need-the-osi-model)
3. [The 7 Layers of the OSI Model](#3-the-7-layers-of-the-osi-model)
4. [Layer 7 — Application Layer](#4-layer-7--application-layer)
5. [Layer 6 — Presentation Layer](#5-layer-6--presentation-layer)
6. [Layer 5 — Session Layer](#6-layer-5--session-layer)
7. [Layer 4 — Transport Layer](#7-layer-4--transport-layer)
8. [Layer 3 — Network Layer](#8-layer-3--network-layer)
9. [Layer 2 — Data Link Layer](#9-layer-2--data-link-layer)
10. [Layer 1 — Physical Layer](#10-layer-1--physical-layer)
11. [How Data Travels Through All 7 Layers](#11-how-data-travels-through-all-7-layers)
12. [Data Units at Each Layer](#12-data-units-at-each-layer)
13. [IP Address vs MAC Address](#13-ip-address-vs-mac-address)
14. [Logical Addressing vs Physical Addressing](#14-logical-addressing-vs-physical-addressing)
15. [Deep Why Questions — OSI](#15-deep-why-questions--osi)
16. [Hands-On Experience](#16-hands-on-experience)

### Chapter 11 — TCP/IP Model

17. [What is the TCP/IP Model?](#17-what-is-the-tcpip-model)
18. [TCP/IP Model Layers](#18-tcpip-model-layers)
19. [OSI vs TCP/IP](#19-osi-vs-tcpip)
20. [Deep Why Questions — TCP/IP](#20-deep-why-questions--tcpip)
21. [Hands-On Experience — TCP/IP](#21-hands-on-experience--tcpip)
22. [Interview Revision](#22-interview-revision)
23. [Final Mental Model](#23-final-mental-model)

---

# Chapter 10 — OSI Model

---

# 1. What is the OSI Model?

## Definition

**OSI stands for Open Systems Interconnection.**

The OSI model is a standard conceptual model used to understand how two or more computers communicate with each other.

Instead of treating networking as one huge complicated process, we divide it into **7 smaller layers**.

Each layer has a specific responsibility.

### In one sentence

> **The OSI model divides computer communication into seven layers, where each layer performs a specific networking function.**

---

# 2. Why Do We Need the OSI Model?

Imagine you send a WhatsApp message:

```text
"Hey, where are you?"
```

It looks extremely simple from your perspective.

You:

```text
Open WhatsApp
     ↓
Type message
     ↓
Press Send
```

But internally, a huge amount of work happens.

Your message has to:

```text
Application
    ↓
Data processing
    ↓
Transport
    ↓
IP addressing
    ↓
Routing
    ↓
MAC addressing
    ↓
Physical transmission
    ↓
Internet
    ↓
Receiver
```

There may be:

- Your application
- Your network interface
- Your router
- Your ISP
- Multiple networks
- Multiple routers
- IP addresses
- Physical cables or wireless signals
- The receiver's network
- The receiver's device
- The receiver's application

Trying to understand all of this as one giant process would be extremely difficult.

So networking is divided into **layers**.

---

# Simple Analogy — Sending a Parcel

Imagine sending a parcel from Chennai to another country.

You don't personally do everything.

Instead:

```text
You
 ↓
Prepare the package
 ↓
Write destination address
 ↓
Give it to courier
 ↓
Courier chooses transportation
 ↓
Route is selected
 ↓
Package travels through different locations
 ↓
Local delivery
 ↓
Receiver
```

Networking works in a similar conceptual way.

Each stage has a particular responsibility.

---

# Why Is Layering Useful?

Suppose something goes wrong.

If the network is not working, instead of checking everything randomly, we can ask:

```text
Is the application working?
        ↓
Is transport working?
        ↓
Is the IP configuration correct?
        ↓
Is the MAC/link working?
        ↓
Is the physical connection working?
```

This makes troubleshooting much easier.

---

# 3. The 7 Layers of the OSI Model

The OSI model has **7 layers**.

From top to bottom:

| Layer | Name | Main Responsibility |
|---:|---|---|
| 7 | Application | Application-level communication |
| 6 | Presentation | Data representation, encryption, compression |
| 5 | Session | Managing communication sessions |
| 4 | Transport | End-to-end data delivery |
| 3 | Network | IP addressing and routing |
| 2 | Data Link | Frames and MAC addressing |
| 1 | Physical | Bits and physical signals |

The order is:

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

Easy abbreviation:

```text
A
P
S
T
N
D
P
```

---

# OSI Model at a Glance

```text
┌──────────────────────────────┐
│ 7. APPLICATION               │
│ What the application wants   │
├──────────────────────────────┤
│ 6. PRESENTATION              │
│ Represent / protect data     │
├──────────────────────────────┤
│ 5. SESSION                   │
│ Manage communication session │
├──────────────────────────────┤
│ 4. TRANSPORT                 │
│ Deliver data between apps    │
├──────────────────────────────┤
│ 3. NETWORK                   │
│ IP + routing                 │
├──────────────────────────────┤
│ 2. DATA LINK                 │
│ MAC + frames                 │
├──────────────────────────────┤
│ 1. PHYSICAL                  │
│ Bits + signals               │
└──────────────────────────────┘
```

---

# 4. Layer 7 — Application Layer

## What is the Application Layer?

The Application layer is the layer closest to the user.

This is where network applications provide functionality to users.

Examples:

- Web browsers
- Messaging applications
- Email applications
- Skype
- Chrome
- Other network applications

You use the application without needing to know how the lower networking layers work.

---

# Example — WhatsApp

Suppose you open WhatsApp and type:

```text
Hello
```

You interact with:

```text
WhatsApp
```

not directly with:

```text
TCP
IP
MAC
Electrical signals
Radio signals
```

The application is responsible for providing the interface through which you perform the action.

Conceptually:

```text
You
 ↓
WhatsApp
 ↓
Networking stack
 ↓
Internet
```

---

# What is a Protocol?

A **protocol** is a set of rules that determines how communication takes place.

Some application-layer protocols include:

- HTTP
- FTP
- Telnet
- DNS

For example:

```text
Browser
   ↓
HTTP
   ↓
Web server
```

The application doesn't need to manually create physical signals.

The lower layers take care of that.

---

# Deep Why Question

## Why doesn't WhatsApp directly create IP packets?

Because that is not its responsibility.

The application says essentially:

```text
"I want to send this data."
```

Then lower layers handle the networking work.

This separation is extremely important.

Imagine if every application had to implement:

```text
IP routing
MAC addressing
TCP
Ethernet
Wi-Fi
Physical signals
```

Every application would become incredibly complicated.

Instead:

```text
Application
     ↓
Transport
     ↓
Network
     ↓
Data Link
     ↓
Physical
```

Each layer performs its own job.

---

# 5. Layer 6 — Presentation Layer

The Presentation layer is concerned with how data is represented.

Important responsibilities include:

1. Translation
2. Encoding
3. Encryption
4. Decryption
5. Compression
6. Abstraction

Think of this layer as:

> **"How should the data be represented, protected, and prepared?"**

---

# 5.1 Translation

Different computer systems can represent data differently.

For example, character representations can involve standards such as:

```text
ASCII
EBCDIC
```

The Presentation layer deals with translating data into an appropriate representation.

Conceptually:

```text
Application data
       ↓
Presentation
       ↓
Machine-understandable representation
```

---

# Simple Example

Suppose the application has:

```text
HELLO
```

The computer ultimately needs to represent that information in a machine-readable form.

Conceptually:

```text
"HELLO"
   ↓
Character representation
   ↓
Machine representation
```

---

# 5.2 Encoding

Encoding changes data into a particular representation.

Conceptually:

```text
Original data
     ↓
Encoding
     ↓
Encoded representation
```

The purpose is to represent data in a form that can be processed or transmitted appropriately.

---

# 5.3 Encryption

Encryption protects information by transforming it into a form that is not directly readable.

Example:

```text
Original:

"MEET AT 5 PM"
```

After encryption:

```text
Encrypted data
```

The receiver uses decryption to recover the original information.

```text
Original message
      ↓
  Encryption
      ↓
Protected data
      ↓
    Network
      ↓
  Decryption
      ↓
Original message
```

---

# Simple Analogy — Secret Letter

Imagine writing:

```text
MEET AT 5 PM
```

on a piece of paper.

Anyone who gets the paper can read it.

Instead, you convert it into a secret code.

Only someone who knows how to decode it can understand it.

That is the basic idea behind encryption.

---

# 5.4 Compression

Why compress data?

Because smaller data requires less data to be transported.

For example:

```text
Before:

████████████████████████████████
```

After compression:

```text
██████████
```

Conceptually:

```text
Large data
    ↓
Compression
    ↓
Smaller data
    ↓
Transmission
```

There are two important types:

```text
Lossless
Lossy
```

---

# Lossless Compression

Nothing is intentionally lost.

```text
Original
   ↓
Compression
   ↓
Compressed
   ↓
Decompression
   ↓
Original
```

Therefore:

```text
Original = Recovered data
```

---

# Lossy Compression

Some information can be discarded to reduce the size.

```text
Original
   ↓
Lossy compression
   ↓
Smaller representation
```

The recovered result is not necessarily identical to the original.

The choice depends on the situation.

---

# 5.5 Abstraction

Abstraction means hiding unnecessary internal complexity.

For example, when you use WhatsApp, you simply think:

```text
Send message
```

You don't need to think about:

```text
How is the data encoded?
How is it represented?
How is it transmitted?
How are the bits physically sent?
```

Those details are handled by lower layers.

---

# 5.6 SSL

SSL stands for:

> **Secure Sockets Layer**

It is associated with:

- Encryption
- Decryption

The important idea for now is that security mechanisms can protect communication.

---

# Presentation Layer Summary

| Function | Simple Meaning |
|---|---|
| Translation | Convert data representation |
| Encoding | Represent data in a particular format |
| Encryption | Protect data |
| Decryption | Recover protected data |
| Compression | Reduce data size |
| Abstraction | Hide unnecessary complexity |

---

# Deep Why Questions

## Why do we need translation?

Because different systems may represent information differently.

A suitable common representation allows systems to interpret the information correctly.

---

## Why compress data?

Because smaller data means less data needs to be transported.

---

## Why encrypt data?

Because information travelling across a network should not simply be readable by anyone who happens to obtain it.

---

# 6. Layer 5 — Session Layer

The Session layer deals with establishing and managing communication sessions.

Think of a session as:

> **A period of communication between two parties.**

A session can conceptually go through:

```text
Establish
   ↓
Maintain
   ↓
Exchange data
   ↓
Terminate
```

---

# Example — Online Shopping

Imagine using an online shopping website.

```text
Open website
    ↓
Login
    ↓
Session established
    ↓
Browse products
    ↓
Add product
    ↓
Payment
    ↓
Transaction completed
    ↓
Session ends / logout
```

The idea of maintaining the communication session belongs to the Session layer in the OSI model.

---

# Authentication

Authentication answers:

> **"Who are you?"**

Example:

```text
Username
Password
   ↓
Authentication
```

If the credentials are correct:

```text
User identified
```

---

# Authorization

Authorization answers:

> **"What are you allowed to do?"**

Example:

```text
User authenticated
       ↓
What permissions does the user have?
       ↓
Access allowed / denied
```

---

# Authentication vs Authorization

| Concept | Question |
|---|---|
| Authentication | Who are you? |
| Authorization | What are you allowed to do? |

### Easy memory trick

```text
Authentication
→ Identity

Authorization
→ Permission
```

---

# Why Separate Session Management?

Consider:

```text
Session Layer
      ↓
"I manage the communication session."

Transport Layer
      ↓
"I transport the data."
```

These are different responsibilities.

If every layer tried to perform every job, the system would become complicated.

Layering keeps responsibilities separate.

---

# Deep Why Question

## Why shouldn't the Session layer handle all data transportation itself?

Because session management and data transportation are different problems.

For example:

```text
Session:
"Are we communicating?"

Transport:
"How should the data be delivered?"
```

Different responsibilities can therefore be handled independently.

---

# 7. Layer 4 — Transport Layer

The Transport layer is one of the most important layers for interviews.

Its main responsibility is:

> **Transporting data between applications.**

Important concepts:

- TCP
- UDP
- Segmentation
- Port numbers
- Sequence numbers
- Flow control
- Error control
- Checksum
- Connection-oriented communication
- Connectionless communication

---

# 7.1 What is a Protocol?

A protocol defines the rules for communication.

At the Transport layer, two important protocols are:

```text
TCP
UDP
```

---

# 7.2 Segmentation

Suppose you want to send a huge file:

```text
████████████████████████████████████████████████
```

Sending it as one enormous unit would be inconvenient.

The Transport layer divides the data into smaller pieces.

This is called:

> **Segmentation**

For example:

```text
Large data
    ↓
┌─────────┐
│Segment 1│
├─────────┤
│Segment 2│
├─────────┤
│Segment 3│
├─────────┤
│Segment 4│
└─────────┘
```

These smaller units are called **segments**.

---

# Why Segment Data?

Imagine transporting 1000 books.

Instead of putting everything into one giant truck that must successfully travel from Chennai to the destination, you can divide the load into manageable shipments.

Similarly, networking can divide large data into smaller units.

---

# 7.3 Port Numbers

Suppose your computer is running:

```text
Chrome
WhatsApp
Email
Game
```

All of them can communicate over the network.

Now imagine a packet arrives at your computer.

The computer needs to know:

> **Which application should receive this data?**

This is where **port numbers** become important.

A transport segment contains source and destination port information.

Conceptually:

```text
Incoming data
     ↓
Destination port
     ↓
Correct application
```

---

# Simple Analogy — Apartment Building

Imagine:

```text
Building
   ↓
IP address
```

Inside the building:

```text
Room 101
Room 102
Room 103
```

The IP helps identify the machine/network destination.

The port helps identify the particular service/application.

Conceptually:

```text
IP   → Which machine?
Port → Which application/service?
```

---

# 7.4 Sequence Numbers

Suppose data is divided into:

```text
Segment 1
Segment 2
Segment 3
Segment 4
```

The receiver might not necessarily process them in the exact order they were originally sent.

For example:

```text
Received:

Segment 3
Segment 1
Segment 4
Segment 2
```

Sequence information allows the receiver to reconstruct the correct order:

```text
1 → 2 → 3 → 4
```

Therefore:

> **Sequence numbers help identify the order of segments.**

---

# Deep Why Question

## What would happen without sequence information?

Imagine receiving:

```text
"The"
"world"
"Hello"
```

You need to know whether the original sentence was:

```text
Hello the world
```

or:

```text
The world Hello
```

Ordering information allows the receiver to reconstruct the intended sequence.

---

# 7.5 Flow Control

Suppose:

```text
Sender = 40 Mbps
Receiver = 20 Mbps
```

The sender can produce data faster than the receiver can process it.

If the sender continuously sends at:

```text
40 Mbps
```

while the receiver can only handle:

```text
20 Mbps
```

the receiver can become overwhelmed.

This is why we need:

> **Flow control**

Flow control regulates how much data is sent so that the receiver can handle it.

---

# Simple Analogy — Filling a Bottle

Imagine:

```text
Tap →→→→→ Bottle
```

Suppose the tap provides water extremely quickly.

But the bottle can only accept water slowly.

Eventually:

```text
OVERFLOW!
```

Flow control is conceptually like controlling the tap so that the receiver isn't overwhelmed.

---

# 7.6 Error Control

During transmission, data may:

- Get lost
- Become corrupted

Therefore, networking needs mechanisms to detect and deal with transmission problems.

This is called:

> **Error control**

---

# 7.7 Checksum

A checksum is associated with the data so that the receiver can check whether the received data is valid/correct.

Conceptually:

```text
Data
  +
Checksum
  ↓
Transmission
  ↓
Receiver
  ↓
Check
```

If the calculated/checking result doesn't match the expected value, the receiver can determine that something went wrong.

---

# 7.8 TCP

TCP stands for:

> **Transmission Control Protocol**

TCP is **connection-oriented**.

The basic idea is:

```text
Sender
   ↓
Establish communication
   ↓
Send data
   ↓
Receiver
   ↓
Acknowledgement
   ↓
Sender knows data was received
```

---

# TCP and Acknowledgement

Suppose:

```text
Sender → Segment 1 → Receiver
```

The receiver can respond:

```text
Receiver → ACK → Sender
```

The sender now knows that the receiver received the relevant data.

Conceptually:

```text
Sender
   │
   │ Data
   ▼
Receiver
   │
   │ ACK
   ▼
Sender
```

---

# TCP Example — File Transfer

Suppose you download a file.

```text
File
 ↓
Segments
 ↓
TCP
 ↓
Network
 ↓
Receiver
```

The communication can involve acknowledgement and reliability mechanisms.

Examples where reliable delivery is important include:

- Email
- File transfer

---

# 7.9 UDP

UDP stands for:

> **User Datagram Protocol**

UDP is **connectionless**.

The sender can send data without establishing the same type of connection-oriented communication used by TCP.

Conceptually:

```text
Sender
   ↓
Data
   ↓
Receiver
```

There is no requirement for the same acknowledgement/feedback mechanism described for TCP.

---

# Why Can UDP Be Faster?

TCP performs additional mechanisms for reliable communication.

UDP avoids some of this overhead.

Therefore, UDP can be faster.

The trade-off is that some packets may be lost.

---

# UDP Example — Real-Time Communication

Imagine a live game.

Suppose a player's position is:

```text
x = 100
y = 200
```

Then a new position arrives:

```text
x = 105
y = 200
```

If one old update is lost, the game can continue with newer information.

For real-time applications, waiting for every lost packet to be retransmitted may be undesirable.

Examples include:

- Gaming
- Video conferencing

---

# TCP vs UDP

| Feature | TCP | UDP |
|---|---|---|
| Communication | Connection-oriented | Connectionless |
| Feedback | Acknowledgement/feedback | No equivalent feedback mechanism |
| Reliability focus | Higher | Lower |
| Overhead | Higher | Lower |
| Speed | Generally slower | Generally faster |
| Example | Email, file transfer | Gaming, video conferencing |

---

# Deep Why Questions — Transport Layer

## Why divide data into segments?

To break large amounts of data into smaller manageable units.

---

## Why are port numbers needed?

Because one computer can run many applications simultaneously.

```text
Computer
├── Browser
├── WhatsApp
├── Email
└── Game
```

The port helps identify the intended application/service.

---

## Why are sequence numbers needed?

Because data is divided into multiple segments and the receiver needs ordering information.

---

## Why is flow control needed?

Because sender and receiver can operate at different speeds.

```text
Sender   = 40 Mbps
Receiver = 20 Mbps
```

---

## Why does TCP use acknowledgement?

To give the sender feedback that data was received.

---

## Why can UDP be useful for gaming?

Because real-time applications can prioritize speed and current information instead of waiting for every missing packet.

---

# 8. Layer 3 — Network Layer

The Network layer is responsible for moving data between different networks.

The important concepts are:

- IP addresses
- Logical addressing
- Packets
- Routing
- Path selection
- Load balancing
- Routers

---

# 8.1 Logical Addressing

The Network layer uses **logical addressing**.

The main example is:

> **IP addressing**

A packet can contain:

```text
Source IP
Destination IP
```

---

# What is an IP Packet?

Conceptually:

```text
Segment
   +
Source IP
   +
Destination IP
   ↓
IP Packet
```

The packet now contains information that allows it to be routed toward its destination.

---

# Simple Analogy — Postal Address

Suppose you want to send a parcel:

```text
From:
Chennai

To:
Bangalore
```

The delivery system needs destination information.

Similarly:

```text
Source IP
Destination IP
```

provide logical addressing information for network communication.

---

# 8.2 Routing

Routing means:

> **Moving a data packet from its source toward its destination through an appropriate path.**

Imagine:

```text
Computer A
    ↓
Router
    ↓
Router
    ↓
Router
    ↓
Computer B
```

The packet may travel through several intermediate routers.

---

# 8.3 Why Do We Need Routing?

Imagine there are multiple possible paths:

```text
             Router B
            /        \
           /          \
Computer A              Computer D
           \          /
            \        /
             Router C
```

Which path should the packet use?

The network needs to determine an appropriate path.

---

# Routing Algorithms

Routing can involve routing algorithms.

The material mentions:

> **Dijkstra's algorithm**

This is a shortest-path algorithm.

The important idea is:

```text
Network
   ↓
Possible paths
   ↓
Calculate appropriate path
   ↓
Forward packet
```

---

# 8.4 Load Balancing

Suppose:

```text
Path A → Very crowded
Path B → Lightly loaded
```

It can be useful to distribute traffic rather than forcing everything through one overloaded path.

Conceptually:

```text
Traffic
   ↓
Multiple possible paths
   ↓
Distribute traffic
   ↓
Reduce excessive load
```

This idea is called:

> **Load balancing**

---

# 8.5 Router

A router connects different networks and forwards packets between them.

For example:

```text
Network A
    ↓
  Router
    ↓
Network B
```

A router examines packet information and determines where the packet should go next.

---

# Deep Why Questions

## Why does the Network layer need IP addresses?

Because packets need logical source and destination information.

---

## Why can't two computers simply communicate directly?

They can communicate directly in some situations, but when devices are located on different networks, intermediate networking devices may be required.

---

## Why is routing necessary?

Because there can be multiple possible paths between source and destination.

---

# 9. Layer 2 — Data Link Layer

The Data Link layer deals with communication over a local/link-level network.

The major concepts are:

- MAC addresses
- Physical addressing
- Frames
- Media Access Control
- Error detection

---

# 9.1 MAC Address

A MAC address identifies a network interface.

A typical MAC address looks like:

```text
AA:BB:CC:DD:EE:FF
```

A computer can have multiple network interfaces.

For example:

```text
Laptop
├── Wi-Fi adapter
│      └── MAC address
│
└── Ethernet adapter
       └── MAC address
```

Therefore, one computer can have multiple MAC addresses.

---

# 9.2 Frame

The Data Link layer's data unit is called a:

> **Frame**

Conceptually:

```text
IP Packet
    ↓
Data Link processing
    ↓
Frame
```

A frame can contain MAC addressing information.

---

# 9.3 Physical Addressing

The Data Link layer deals with:

> **Physical addressing**

The important distinction is:

```text
IP
 ↓
Logical addressing
 ↓
Network layer
```

versus:

```text
MAC
 ↓
Physical addressing
 ↓
Data Link layer
```

---

# 9.4 Media Access Control

Media Access Control, or MAC, deals with controlling how devices access the communication medium.

In simple terms:

> **Who gets to put data onto the shared communication medium, and how is that data handled?**

The layer also deals with things such as error detection.

---

# Example — Wi-Fi

Imagine:

```text
Laptop
   ↓
Wi-Fi
   ↓
Router
```

At the Network layer:

```text
Source IP
Destination IP
```

At the Data Link layer:

```text
Source MAC
Destination MAC
```

The data is carried in a frame.

---

# Deep Why Question

## Why do we need both IP and MAC addresses?

Because they serve different purposes.

Think:

```text
IP
→ Logical identity/location
→ Network layer
→ Routing between networks
```

and:

```text
MAC
→ Network interface identity at the link level
→ Data Link layer
→ Local/link communication
```

---

# Simple Analogy

Imagine a university.

```text
University
    ↓
Building
    ↓
Room
```

A broad address helps locate the building.

A more local identifier helps identify the specific destination within that local environment.

Similarly, networking uses different types of addressing at different layers.

---

# 10. Layer 1 — Physical Layer

The Physical layer is the lowest OSI layer.

It deals with the actual physical transmission of information.

Examples:

- Cables
- Hardware
- Electrical signals
- Light signals
- Radio signals
- Bits

---

# 10.1 Bits

At the Physical layer, data is represented as bits:

```text
0
1
0
1
1
0
```

Higher layers deal with things such as:

```text
Data
Segments
Packets
Frames
```

But eventually everything has to become a physical signal.

---

# 10.2 How Are Bits Physically Transmitted?

## Electrical Cable

```text
Bits
 ↓
Electrical signals
 ↓
Cable
```

---

## Optical Fiber

```text
Bits
 ↓
Light signals
 ↓
Optical fiber
```

---

## Wi-Fi

```text
Bits
 ↓
Radio signals
 ↓
Wireless medium
```

---

# Simple Analogy — Road

Imagine a highway.

The highway itself is the physical medium.

Cars physically travel on it.

Similarly, the Physical layer is concerned with the actual medium through which information travels.

---

# 10.3 Receiving Data

At the receiving machine:

```text
Physical signal
      ↓
Physical layer
      ↓
Bits
      ↓
Data Link layer
      ↓
Frame
      ↓
Higher layers
```

So the receiver converts the physical signal back into meaningful digital information.

---

# Deep Why Question

## Why can't the Physical layer directly understand a packet?

Because a packet is a logical data structure.

The Physical layer is concerned with physically transmitting bits.

Eventually:

```text
Packet
   ↓
Frame
   ↓
Bits
   ↓
Physical signal
```

---

# 11. How Data Travels Through All 7 Layers

Now let's connect everything.

Suppose you send:

```text
"Hello"
```

to your friend.

---

# Sender Side

## Layer 7 — Application

You type:

```text
Hello
```

into a messaging application.

```text
You
 ↓
Messaging application
 ↓
"Hello"
```

---

# Layer 6 — Presentation

The data may be:

```text
Translated
Encoded
Encrypted
Compressed
```

Conceptually:

```text
"Hello"
   ↓
Presentation processing
   ↓
Prepared data
```

---

# Layer 5 — Session

The communication session is managed.

```text
Session
   ↓
Communication
```

---

# Layer 4 — Transport

The data is divided into segments.

```text
Data
 ↓
Segment 1
Segment 2
Segment 3
```

Transport-related information can include:

```text
Source port
Destination port
Sequence information
Checksum
```

depending on the protocol.

---

# Layer 3 — Network

The Network layer adds logical addressing:

```text
Source IP
Destination IP
```

Now we have an IP packet.

```text
Segment
   ↓
IP addressing
   ↓
Packet
```

---

# Layer 2 — Data Link

The Data Link layer handles the link-level delivery.

MAC addresses are involved:

```text
Source MAC
Destination MAC
```

The result is a:

```text
Frame
```

---

# Layer 1 — Physical

The frame is ultimately transmitted as bits/signals.

```text
Frame
 ↓
Bits
 ↓
Physical signal
```

The physical signal may be:

```text
Electrical
Light
Radio
```

---

# Complete Sender Flow

```text
Application
     ↓
Presentation
     ↓
Session
     ↓
Transport
     ↓
Network
     ↓
Data Link
     ↓
Physical
     ↓
Internet / Network
```

---

# Receiver Side

At the receiving device, the process moves upward:

```text
Physical
     ↓
Data Link
     ↓
Network
     ↓
Transport
     ↓
Session
     ↓
Presentation
     ↓
Application
```

Eventually:

```text
"Hello"
```

appears in the receiving application.

---

# Complete Communication

```text
                SENDER
                   │
                   ▼
        ┌───────────────────┐
        │  7. Application   │
        ├───────────────────┤
        │  6. Presentation  │
        ├───────────────────┤
        │  5. Session       │
        ├───────────────────┤
        │  4. Transport     │
        ├───────────────────┤
        │  3. Network       │
        ├───────────────────┤
        │  2. Data Link     │
        ├───────────────────┤
        │  1. Physical      │
        └─────────┬─────────┘
                  │
                  ▼
             NETWORK
                  │
                  ▼
        ┌─────────┴─────────┐
        │  1. Physical      │
        ├───────────────────┤
        │  2. Data Link     │
        ├───────────────────┤
        │  3. Network       │
        ├───────────────────┤
        │  4. Transport     │
        ├───────────────────┤
        │  5. Session       │
        ├───────────────────┤
        │  6. Presentation  │
        ├───────────────────┤
        │  7. Application   │
        └─────────┬─────────┘
                  │
                  ▼
              RECEIVER
```

---

# Important Concept — Encapsulation

One very useful way to understand the sender-side process is **encapsulation**.

Imagine you have a letter.

You first write the message:

```text
Hello
```

Then you put it into an envelope.

Then the envelope gets an address.

Then it gets placed into a delivery system.

Networking works similarly.

Conceptually:

```text
Application Data
      ↓
Transport adds information
      ↓
Segment
      ↓
Network adds IP information
      ↓
Packet
      ↓
Data Link adds MAC/link information
      ↓
Frame
      ↓
Physical transmission
      ↓
Bits
```

At the receiver, the process is reversed.

This is called **decapsulation**.

```text
Bits
 ↓
Frame
 ↓
Packet
 ↓
Segment
 ↓
Application data
```

---

# 12. Data Units at Each Layer

Different layers use different names for the data they handle.

| Layer | Data Unit |
|---|---|
| Application | Data / Message |
| Presentation | Data |
| Session | Data |
| Transport | Segment |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

The important chain is:

```text
Data
 ↓
Segment
 ↓
Packet
 ↓
Frame
 ↓
Bits
```

At the receiver:

```text
Bits
 ↓
Frame
 ↓
Packet
 ↓
Segment
 ↓
Data
```

---

# 13. IP Address vs MAC Address

This is extremely important.

| Feature | IP Address | MAC Address |
|---|---|---|
| Layer | Network | Data Link |
| Address type | Logical | Physical |
| Main role | Network-level addressing | Link/interface-level addressing |
| Associated unit | Packet | Frame |

---

# Example

Suppose:

```text
Computer A
```

has:

```text
Source IP
Source MAC
```

and:

```text
Computer B
```

has:

```text
Destination IP
Destination MAC
```

The packet uses IP addressing.

The frame uses MAC addressing.

---

# 14. Logical Addressing vs Physical Addressing

## Logical Addressing

Logical addressing happens at the Network layer.

It uses:

```text
Source IP
Destination IP
```

Its purpose is to help with communication between networks.

---

# Physical Addressing

Physical/link-level addressing happens at the Data Link layer.

It uses:

```text
Source MAC
Destination MAC
```

---

# Easy Memory Trick

```text
IP
 ↓
Logical
 ↓
Network
 ↓
Routing
```

```text
MAC
 ↓
Physical/link-level
 ↓
Data Link
 ↓
Frame
```

---

# Postal Analogy

Imagine sending a parcel.

The destination could be:

```text
Country
 ↓
City
 ↓
Area
```

This is like the broad logical destination.

Then, when the parcel reaches the local area, it needs to be delivered to the particular local destination.

This is a useful mental model for understanding why networking has different addressing mechanisms.

---

# 15. Deep Why Questions — OSI

## Q1. Why does OSI have seven layers?

Because networking contains many different responsibilities.

Instead of putting everything into one huge system:

```text
Application
Data representation
Session
Transport
Routing
Local delivery
Physical transmission
```

we separate them into layers.

---

## Q2. Why not use one layer for everything?

Because that would create enormous complexity.

For example, imagine every application had to know:

```text
How TCP works
How IP works
How routing works
How MAC addressing works
How Ethernet works
How Wi-Fi works
How physical signals work
```

That would make software extremely complicated.

Layering gives each part a clear responsibility.

---

## Q3. Why are port numbers required?

Because one computer can run multiple applications.

```text
Computer
├── Browser
├── WhatsApp
├── Email
└── Game
```

The IP can identify the network destination, while the port helps identify the service/application.

---

## Q4. Why does the Network layer use IP?

Because communication between different networks needs logical addressing.

```text
Source
   ↓
Destination
```

The IP addresses provide that logical addressing information.

---

## Q5. Why does Data Link use MAC?

Because local/link-level communication needs addressing at the network-interface level.

---

## Q6. Why does the Physical layer need signals?

Because information ultimately needs to travel through an actual physical medium.

That medium could involve:

```text
Electrical signals
Light
Radio
```

---

## Q7. Why can't IP addresses alone do everything?

Because IP and MAC operate at different layers and solve different problems.

```text
IP
→ Network layer
→ Logical addressing

MAC
→ Data Link layer
→ Link-level addressing
```

---

## Q8. Why does TCP use acknowledgements?

Because the sender needs feedback that the receiver received the data.

```text
Sender → Data → Receiver
Sender ← ACK  ← Receiver
```

---

## Q9. Why doesn't UDP work exactly like TCP?

Because UDP does not use the same connection-oriented acknowledgement mechanism.

This reduces overhead and can make it faster.

---

## Q10. Why is flow control necessary?

Because:

```text
Sender speed ≠ Receiver speed
```

Example:

```text
Sender   = 40 Mbps
Receiver = 20 Mbps
```

The receiver cannot necessarily process everything at the sender's rate.

---

## Q11. Why are sequence numbers useful?

Because data may be divided into multiple segments.

The receiver needs to know their ordering.

---

## Q12. Why is a checksum useful?

Because the receiver needs a way to detect whether the received data is correct or has been corrupted.

---

# 16. Hands-On Experience

The best way to understand networking is to connect the theory to your own Linux machine.

---

# Practical 1 — Find Your IP Address

Run:

```bash
ip addr
```

or:

```bash
ip a
```

Look for something similar to:

```text
inet 192.168.x.x
```

This is an IP address assigned to a network interface.

### Think

Ask yourself:

```text
Which interface is connected?

What is its IP?

Is it IPv4 or IPv6?
```

---

# Practical 2 — Find Your MAC Address

Run:

```bash
ip link
```

Look for:

```text
link/ether xx:xx:xx:xx:xx:xx
```

That is the MAC address of the interface.

---

# Practical 3 — Compare IP and MAC

Run:

```bash
ip addr
```

Then:

```bash
ip link
```

Find:

```text
IP address
MAC address
```

Now connect them to the OSI model:

```text
IP
 ↓
Network layer
 ↓
Logical addressing
```

and:

```text
MAC
 ↓
Data Link layer
 ↓
Link-level/physical addressing
```

---

# Practical 4 — Test Connectivity

Run:

```bash
ping google.com
```

You should see responses if communication succeeds.

The output can show information such as:

```text
time
packet responses
```

This gives you a practical way to observe network communication.

---

# Practical 5 — Observe Routing

Run:

```bash
traceroute google.com
```

If it is not installed:

```bash
sudo apt install traceroute
```

Then:

```bash
traceroute google.com
```

You can observe multiple hops.

For example conceptually:

```text
Your computer
     ↓
Router
     ↓
ISP
     ↓
Router
     ↓
Router
     ↓
Destination
```

This makes the Network layer's routing concept much easier to visualize.

---

# Practical 6 — Observe DNS

Run:

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

You can inspect DNS information.

This helps connect application-level networking concepts with actual network commands.

---

# Practical 7 — Inspect Ports

Run:

```bash
ss -tuln
```

You can see ports on which services are listening.

This connects directly to the Transport layer concept:

```text
IP
 ↓
Machine/network destination

Port
 ↓
Application/service
```

---

# Practical 8 — Capture Packets with Wireshark

Install Wireshark:

```bash
sudo apt install wireshark
```

Open Wireshark and start capturing.

Then run:

```bash
ping google.com
```

In Wireshark, filter:

```text
icmp
```

Now you can inspect actual network traffic.

---

# Practical 9 — Observe TCP

In Wireshark, use:

```text
tcp
```

Look for:

- Source port
- Destination port
- Sequence information
- Acknowledgement information

This gives you a practical connection to the Transport layer.

---

# Practical 10 — Observe UDP

Use:

```text
udp
```

in Wireshark.

Compare TCP and UDP.

Think:

```text
TCP
 ↓
Connection-oriented
 ↓
Acknowledgement/feedback
```

versus:

```text
UDP
 ↓
Connectionless
 ↓
No equivalent feedback mechanism
```

---

# Mini Practical Challenge

Run:

```bash
ip a
```

Answer:

1. What is your IP address?
2. Which interface has it?
3. Is it IPv4 or IPv6?

Now:

```bash
ip link
```

Answer:

4. What is your MAC address?

Now:

```bash
ip route
```

Answer:

5. What is your default route?
6. Which interface is used?

Now:

```bash
ping google.com
```

Answer:

7. Does it receive replies?
8. What is the response time?

Finally:

```bash
traceroute google.com
```

Answer:

9. How many hops are shown?
10. Why does the packet pass through multiple devices?

---

# Real-Life Example — Sending "Hey!"

Suppose you send:

```text
Hey!
```

through a messaging application.

---

## Layer 7 — Application

You type:

```text
Hey!
```

The messaging application handles the user interaction.

```text
User
 ↓
Messaging App
```

---

## Layer 6 — Presentation

The data may be:

```text
Translated
Encoded
Encrypted
Compressed
```

depending on the communication process.

---

## Layer 5 — Session

The communication session is managed.

```text
Session
 ↓
Communication
```

---

## Layer 4 — Transport

The data can be divided:

```text
Data
 ↓
Segment 1
Segment 2
Segment 3
```

Transport information can include:

```text
Ports
Sequence information
Checksum
```

TCP or UDP may be involved.

---

## Layer 3 — Network

The Network layer handles:

```text
Source IP
Destination IP
Routing
```

The result is an IP packet.

---

## Layer 2 — Data Link

The packet is handled at the link level.

```text
Source MAC
Destination MAC
```

The result is a frame.

---

## Layer 1 — Physical

The frame becomes a physical representation:

```text
Electrical signals
OR
Light
OR
Radio
```

---

# Receiver Side

The process conceptually reverses:

```text
Physical
 ↓
Data Link
 ↓
Network
 ↓
Transport
 ↓
Session
 ↓
Presentation
 ↓
Application
 ↓
"Hey!"
```

---

# Peer-to-Peer Concept in OSI

We can conceptually imagine:

```text
Sender Application
       ↕
Receiver Application
```

and:

```text
Sender Transport
       ↕
Receiver Transport
```

and so on.

But remember:

> This is a conceptual model.

The actual data physically travels down the sender's stack, through the network, and then up the receiver's stack.

---

# Complete Conceptual Route

```text
Sender Application
       ↓
Sender Presentation
       ↓
Sender Session
       ↓
Sender Transport
       ↓
Sender Network
       ↓
Sender Data Link
       ↓
Sender Physical
       ↓
     Network
       ↓
Receiver Physical
       ↓
Receiver Data Link
       ↓
Receiver Network
       ↓
Receiver Transport
       ↓
Receiver Session
       ↓
Receiver Presentation
       ↓
Receiver Application
```

---

# OSI — Quick Revision Table

| Layer | Remember This |
|---|---|
| 7. Application | Applications communicate |
| 6. Presentation | Translation, encoding, encryption, compression |
| 5. Session | Manage communication sessions |
| 4. Transport | TCP, UDP, segments, ports, flow/error control |
| 3. Network | IP, packets, routing |
| 2. Data Link | MAC, frames, link-level communication |
| 1. Physical | Bits, cables, signals |

---

# Chapter 11 — TCP/IP Model

# 17. What is the TCP/IP Model?

The TCP/IP model is another way of organizing networking functions.

TCP/IP is also referred to as the:

> **Internet Protocol Suite**

It is similar to the OSI model, but it uses fewer layers.

---

# 18. TCP/IP Model Layers

The model contains 5 layers:

```text
1. Application
2. Transport
3. Network
4. Data Link
5. Physical
```

Visual representation:

```text
┌──────────────────────┐
│ Application          │
├──────────────────────┤
│ Transport            │
├──────────────────────┤
│ Network              │
├──────────────────────┤
│ Data Link            │
├──────────────────────┤
│ Physical             │
└──────────────────────┘
```

---

# 19. OSI vs TCP/IP

The two models are very similar in their overall idea:

> Networking responsibilities are divided into layers.

The major difference is the number of layers.

```text
OSI
→ 7 layers

TCP/IP
→ 5 layers
```

---

# How Are the Layers Mapped?

In OSI:

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

In TCP/IP:

```text
Application
Transport
Network
Data Link
Physical
```

The TCP/IP Application layer combines the responsibilities represented by the OSI:

```text
Application
Presentation
Session
```

Conceptually:

```text
OSI                          TCP/IP

Application ────────┐
Presentation ───────┼────── Application
Session ────────────┘

Transport ───────────────── Transport

Network ─────────────────── Network

Data Link ───────────────── Data Link

Physical ────────────────── Physical
```

---

# Comparison Table

| OSI | TCP/IP |
|---|---|
| Application | Application |
| Presentation | Application |
| Session | Application |
| Transport | Transport |
| Network | Network |
| Data Link | Data Link |
| Physical | Physical |

Therefore:

```text
OSI    = 7 layers
TCP/IP = 5 layers
```

---

# Why Does TCP/IP Have Fewer Layers?

The three OSI layers:

```text
Application
Presentation
Session
```

are combined into:

```text
Application
```

in the TCP/IP model.

So:

```text
3 OSI layers
      ↓
1 TCP/IP layer
```

The remaining four layers correspond directly.

---

# Deep Why Questions — TCP/IP

## Why do we have both OSI and TCP/IP models?

Both provide a layered way to understand networking.

The major structural difference is:

```text
OSI    → 7 layers
TCP/IP → 5 layers
```

---

## What do they have in common?

Both divide networking into separate responsibilities.

For example, both have concepts corresponding to:

```text
Application
Transport
Network
Data Link
Physical
```

---

## What is the biggest structural difference?

The OSI model separates:

```text
Application
Presentation
Session
```

while TCP/IP combines them into:

```text
Application
```

---

# 20. Deep Why Questions — TCP/IP

### Question 1

Why does TCP/IP have fewer layers?

Because the Application, Presentation, and Session responsibilities are combined into one Application layer.

---

### Question 2

What is common between the two models?

Both use layers to divide networking responsibilities.

---

### Question 3

How many layers are there?

```text
OSI    → 7
TCP/IP → 5
```

---

# 21. Hands-On Experience — TCP/IP

The same Linux commands can help you connect practical networking to the TCP/IP model.

---

## IP Information

```bash
ip a
```

Think:

```text
IP
 ↓
Network layer
```

---

## MAC Information

```bash
ip link
```

Think:

```text
MAC
 ↓
Data Link layer
```

---

## Routing

```bash
ip route
```

Think:

```text
Routing
 ↓
Network layer
```

---

## Connectivity

```bash
ping google.com
```

This lets you observe network communication.

---

## DNS

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

This lets you inspect DNS-related information.

---

## Ports

```bash
ss -tuln
```

This lets you observe listening ports and connect them with Transport-layer concepts.

---

# 22. Interview Revision

## Q1. What is OSI?

OSI stands for:

> **Open Systems Interconnection**

It is a conceptual model that divides networking into seven layers.

---

## Q2. How many layers are in OSI?

```text
7
```

---

## Q3. Name the seven layers.

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

---

## Q4. What is the Application layer?

The layer closest to network applications and user interaction.

Examples:

```text
Browser
Messaging application
Email application
```

---

## Q5. What does the Presentation layer do?

It deals with:

```text
Translation
Encoding
Encryption
Decryption
Compression
Abstraction
```

---

## Q6. What does the Session layer do?

It deals with:

```text
Establishing sessions
Managing sessions
Maintaining communication
Terminating sessions
```

---

## Q7. What does the Transport layer do?

Important concepts:

```text
TCP
UDP
Segmentation
Ports
Sequence numbers
Flow control
Error control
Checksum
```

---

## Q8. What is a segment?

A smaller unit of data created when large data is divided at the Transport layer.

---

## Q9. Why are ports needed?

Because multiple applications can communicate on the same computer.

```text
IP
 ↓
Computer/network destination

Port
 ↓
Application/service
```

---

## Q10. What does the Network layer do?

It deals with:

```text
IP addressing
Logical addressing
Packets
Routing
Path selection
Load balancing
```

---

## Q11. What is logical addressing?

Addressing using IP addresses at the Network layer.

---

## Q12. What is a packet?

A Network-layer data unit containing network-level information such as source and destination IP addresses.

---

## Q13. What does the Data Link layer do?

It deals with:

```text
MAC addresses
Frames
Physical/link-level addressing
Media Access Control
Error detection
```

---

## Q14. What is a MAC address?

A MAC address identifies a network interface at the link level.

---

## Q15. What is a frame?

A frame is the Data Link layer's data unit.

---

## Q16. What does the Physical layer do?

It handles:

```text
Bits
Hardware
Cables
Electrical signals
Light signals
Radio signals
```

---

## Q17. What are the data units?

```text
Transport → Segment
Network   → Packet
Data Link → Frame
Physical  → Bits
```

---

## Q18. What is TCP?

TCP is a connection-oriented transport protocol.

It uses acknowledgement/feedback mechanisms for reliable communication.

---

## Q19. What is UDP?

UDP is a connectionless transport protocol.

It does not use the same acknowledgement/feedback mechanism as TCP and can therefore have lower overhead.

---

## Q20. Why can UDP be faster?

Because it avoids some of the additional mechanisms used by TCP.

---

## Q21. Examples of TCP usage?

```text
Email
File transfer
```

---

## Q22. Examples of UDP usage?

```text
Gaming
Video conferencing
```

---

## Q23. What is TCP/IP?

TCP/IP is a networking model/protocol suite commonly associated with Internet communication.

---

## Q24. How many layers does TCP/IP have?

```text
5
```

---

## Q25. Name them.

```text
Application
Transport
Network
Data Link
Physical
```

---

## Q26. OSI vs TCP/IP?

```text
OSI
→ 7 layers

TCP/IP
→ 5 layers
```

The TCP/IP Application layer combines:

```text
OSI Application
OSI Presentation
OSI Session
```

---

# 23. Final Mental Model

If someone asks you:

> **"Explain what happens when you send a message over the Internet."**

Think like this:

```text
                    USER
                      ↓
             "Send this message"
                      ↓
             ┌─────────────────┐
             │  APPLICATION    │
             │  User interacts │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │  PRESENTATION   │
             │  Represent      │
             │  Encrypt        │
             │  Compress       │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │    SESSION      │
             │ Manage session  │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │   TRANSPORT     │
             │ TCP / UDP       │
             │ Segments        │
             │ Ports           │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │    NETWORK      │
             │ IP              │
             │ Routing         │
             │ Packets         │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │   DATA LINK     │
             │ MAC             │
             │ Frames          │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │    PHYSICAL     │
             │ Bits            │
             │ Signals         │
             └────────┬────────┘
                      ↓
                  INTERNET
                      ↓
             ┌─────────────────┐
             │    PHYSICAL     │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │   DATA LINK     │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │    NETWORK      │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │   TRANSPORT     │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │    SESSION      │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │  PRESENTATION   │
             └────────┬────────┘
                      ↓
             ┌─────────────────┐
             │   APPLICATION   │
             │ Friend sees it  │
             └─────────────────┘
```

---

# The Most Important OSI Chain

Memorize this first:

```text
Application
    ↓
Presentation
    ↓
Session
    ↓
Transport
    ↓
Network
    ↓
Data Link
    ↓
Physical
```

Then attach one idea to each:

```text
Application
→ What the user wants

Presentation
→ Prepare/represent/protect the data

Session
→ Manage communication

Transport
→ Deliver data between applications

Network
→ Find the path between networks

Data Link
→ Deliver over the local/link network

Physical
→ Actually transmit bits
```

---

# The Most Important Addressing Chain

```text
IP Address
    ↓
Logical Addressing
    ↓
Network Layer
    ↓
Routing
```

versus:

```text
MAC Address
    ↓
Link-level / Physical Addressing
    ↓
Data Link Layer
    ↓
Frame
```

---

# The Most Important Data-Unit Chain

```text
Application
    ↓
DATA
    ↓
Transport
    ↓
SEGMENT
    ↓
Network
    ↓
PACKET
    ↓
Data Link
    ↓
FRAME
    ↓
Physical
    ↓
BITS
```

At the receiver:

```text
BITS
 ↓
FRAME
 ↓
PACKET
 ↓
SEGMENT
 ↓
DATA
```

---

# Encapsulation — Remember This

When sending:

```text
Data
 ↓
Segment
 ↓
Packet
 ↓
Frame
 ↓
Bits
```

When receiving:

```text
Bits
 ↓
Frame
 ↓
Packet
 ↓
Segment
 ↓
Data
```

This is one of the most important mental models in networking.

---

# OSI vs TCP/IP — Final Diagram

```text
             OSI                         TCP/IP

      ┌───────────────┐           ┌───────────────┐
      │ Application   │           │               │
      ├───────────────┤           │               │
      │ Presentation  │ ────────► │ Application   │
      ├───────────────┤           │               │
      │ Session       │           │               │
      ├───────────────┤           ├───────────────┤
      │ Transport     │ ────────► │ Transport     │
      ├───────────────┤           ├───────────────┤
      │ Network       │ ────────► │ Network       │
      ├───────────────┤           ├───────────────┤
      │ Data Link     │ ────────► │ Data Link     │
      ├───────────────┤           ├───────────────┤
      │ Physical      │ ────────► │ Physical      │
      └───────────────┘           └───────────────┘

          7 Layers                    5 Layers
```

---

# One-Minute Revision

```text
OSI
→ Open Systems Interconnection
→ 7 layers

7. Application
→ Applications and user interaction

6. Presentation
→ Translation
→ Encoding
→ Encryption / Decryption
→ Compression
→ Abstraction

5. Session
→ Establish
→ Manage
→ Maintain
→ Terminate communication sessions

4. Transport
→ TCP
→ UDP
→ Segmentation
→ Ports
→ Sequence numbers
→ Flow control
→ Error control
→ Checksum

3. Network
→ IP
→ Logical addressing
→ Packets
→ Routing
→ Path selection
→ Load balancing

2. Data Link
→ MAC
→ Frames
→ Link-level addressing
→ Media Access Control
→ Error detection

1. Physical
→ Hardware
→ Bits
→ Electrical signals
→ Light signals
→ Radio signals


TCP/IP
→ 5 layers

Application
Transport
Network
Data Link
Physical


OSI:
Application
Presentation
Session

        ↓

TCP/IP:
Application
```

---