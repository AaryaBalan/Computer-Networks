# Computer Networks — Chapter 10 & 11 Notes

---

# Table of Contents

## Chapter 10 — OSI Model

1. [What is the OSI Model?](#1-what-is-the-osi-model)
2. [Why Do We Need the OSI Model?](#2-why-do-we-need-the-osi-model)
3. [Seven Layers of the OSI Model](#3-seven-layers-of-the-osi-model)
4. [Layer 7 — Application Layer](#4-layer-7--application-layer)
5. [Layer 6 — Presentation Layer](#5-layer-6--presentation-layer)
6. [Layer 5 — Session Layer](#6-layer-5--session-layer)
7. [Layer 4 — Transport Layer](#7-layer-4--transport-layer)
8. [Layer 3 — Network Layer](#8-layer-3--network-layer)
9. [Layer 2 — Data Link Layer](#9-layer-2--data-link-layer)
10.   [Layer 1 — Physical Layer](#10-layer-1--physical-layer)
11.   [OSI Model — Complete Data Flow](#11-osi-model--complete-data-flow)
12.   [Data Units at Different Layers](#12-data-units-at-different-layers)
13.   [IP Address vs MAC Address](#13-ip-address-vs-mac-address)
14.   [Logical Addressing vs Physical Addressing](#14-logical-addressing-vs-physical-addressing)
15.   [Deep Why Questions — OSI Model](#15-deep-why-questions--osi-model)
16.   [Hands-On Experience](#16-hands-on-experience--osi-model)

## Chapter 11 — TCP/IP Model

17. [What is the TCP/IP Model?](#17-what-is-the-tcpip-model)
18. [TCP/IP Model Layers](#18-tcpip-model-layers)
19. [OSI vs TCP/IP — Source-Based Comparison](#19-osi-vs-tcpip--source-based-comparison)
20. [Deep Why Questions — TCP/IP](#20-deep-why-questions--tcpip)
21. [Hands-On Experience](#21-hands-on-experience--tcpip)
22. [Interview Revision](#22-interview-revision)

---

# Chapter 10 — OSI Model (7 Layers)

---

# 1. What is the OSI Model?

## Exact Definition from the Text

The source says:

> **"The OSI model stands for Open Systems Interconnection model."**

The source explains that the OSI model was developed to provide:

> **"a standard way about how two or more computers communicate with each other."**

In simple words:

The **OSI (Open Systems Interconnection) model** is a standard conceptual model that divides computer communication into **seven different layers**.

Each layer has its own responsibility.

---

# 2. Why Do We Need the OSI Model?

The Internet is extremely complex.

When you send a message to someone, many things happen:

```text
You
 ↓
Application
 ↓
Data processing
 ↓
Session
 ↓
Transport
 ↓
Network
 ↓
Data Link
 ↓
Physical medium
 ↓
Network
 ↓
Friend's device
 ↓
Application
 ↓
Friend sees message
```

The source explains that sending a message can involve:

- An application
- Your ISP
- Different networks
- Routers
- IP addresses
- The destination device
- The destination application
- Physical transmission

Trying to understand everything at once would be difficult.

Therefore:

> The complexity is divided into smaller steps called layers.

---

# Simple Analogy — Sending a Parcel

Imagine you want to send a parcel from Chennai to another country.

You don't personally perform every operation.

Instead:

```text
You
 ↓
Package prepared
 ↓
Address added
 ↓
Courier/session arranged
 ↓
Transport arranged
 ↓
Route selected
 ↓
Local delivery
 ↓
Physical movement
 ↓
Destination
```

Networking works conceptually in a similar way.

Each layer has a particular responsibility.

---

# 3. Seven Layers of the OSI Model

The OSI model contains **7 layers**.

From top to bottom:

| Layer | Number | Name         |
| ----- | -----: | ------------ |
| 7     |      7 | Application  |
| 6     |      6 | Presentation |
| 5     |      5 | Session      |
| 4     |      4 | Transport    |
| 3     |      3 | Network      |
| 2     |      2 | Data Link    |
| 1     |      1 | Physical     |

### Easy order to remember

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

Or:

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
┌─────────────────────────────┐
│ 7. Application              │
│ User/application interaction│
├─────────────────────────────┤
│ 6. Presentation             │
│ Translation, encryption,    │
│ compression                 │
├─────────────────────────────┤
│ 5. Session                  │
│ Session management          │
├─────────────────────────────┤
│ 4. Transport                │
│ Segmentation, ports,        │
│ flow/error control          │
├─────────────────────────────┤
│ 3. Network                  │
│ IP addressing, routing      │
├─────────────────────────────┤
│ 2. Data Link                │
│ MAC addressing, frames      │
├─────────────────────────────┤
│ 1. Physical                 │
│ Bits and physical signals   │
└─────────────────────────────┘
```

---

# 4. Layer 7 — Application Layer

## What is the Application Layer?

The source explains:

> **"Application layer basically it's implemented in software."**

The application layer is where users interact with applications.

Examples mentioned in the source include:

- Browsers
- Messaging applications
- Skype
- Chrome
- Other network applications

Users can:

- Send messages
- Send files
- Send emails
- Interact with applications

---

## Simple Explanation

Suppose you open WhatsApp and type:

```text
Hello
```

You are interacting with the application.

You don't manually:

- Create packets
- Assign IP addresses
- Add MAC addresses
- Convert bits into radio signals

The application handles the user interaction.

---

## Application Layer Protocols

The source mentions examples such as:

- HTTP
- File Transfer Protocol
- Telnet
- DNS

The source says these protocols will be discussed separately later.

For now, understand:

> A protocol defines how communication/data transfer is carried out.

---

## Example

When using a browser:

```text
You
 ↓
Chrome / Browser
 ↓
Application-layer communication
 ↓
Lower OSI layers
 ↓
Internet
```

---

## Deep Why Question

### Why doesn't the user directly interact with the Transport or Network layer?

Because the user only needs to interact with the application.

For example:

You don't tell WhatsApp:

```text
"Create a TCP segment."
"Add this destination IP."
"Add this MAC address."
"Convert it into radio waves."
```

Instead:

```text
User → WhatsApp → Networking stack
```

The lower layers handle their respective responsibilities.

---

# 5. Layer 6 — Presentation Layer

The source explains several responsibilities for the presentation layer.

Main responsibilities mentioned:

1. Translation
2. Encoding
3. Encryption
4. Decryption
5. Compression
6. Abstraction

---

# 5.1 Translation

Application data can contain:

- Characters
- Letters
- Numbers
- Words

The presentation layer converts this into a machine-representable format.

The source gives the example of:

```text
ASCII
↓
Machine-representable format
```

and mentions EBCDIC.

This process is called:

> **Translation**

---

## Simple Example

Suppose the application gives:

```text
HELLO
```

The presentation layer deals with representing this data in a form suitable for machine processing/transmission.

Conceptually:

```text
Human-readable data
        ↓
Presentation layer
        ↓
Machine representation
```

---

# 5.2 Encoding

The source also mentions encoding as part of preparing the data before transmission.

Conceptually:

```text
Original data
     ↓
Encoding
     ↓
Representation suitable for processing/transmission
```

---

# 5.3 Encryption

The source explains encryption as changing the data so that it is readable only by the intended person.

Conceptually:

```text
Original message
       ↓
   Encryption
       ↓
Unreadable/protected data
       ↓
     Network
       ↓
   Decryption
       ↓
Original message
```

---

## Simple Analogy

Imagine sending a letter.

Instead of writing:

```text
MEET AT 5 PM
```

you convert it into a secret code.

Only the intended receiver knows how to decode it.

That is the basic idea behind encryption.

---

# 5.4 Compression

The source says that data is compressed so that:

- It becomes easier to transport
- Traffic can be reduced

The source mentions that compression can be:

- Lossy
- Lossless

---

## Lossless Compression

After decompression:

```text
Original data = Recovered data
```

No information is intentionally lost.

---

## Lossy Compression

Some information can be discarded to reduce size.

Conceptually:

```text
Large data
   ↓
Compression
   ↓
Smaller data
```

The source says the type depends on the situation.

---

# 5.5 Abstraction

The source explains that the presentation layer provides abstraction.

The idea is:

```text
Upper layer
    ↓
"I give you this data."
    ↓
Presentation layer
    ↓
Lower layers handle their work
```

The upper layer doesn't need to worry about every internal detail of how the data is handled.

---

# 5.6 SSL

The source mentions:

> **SSL — Secure Sockets Layer**

and associates it with:

- Encryption
- Decryption

The source says the detailed internal operation of these protocols will be covered separately.

---

# Presentation Layer — Summary

| Function    | Meaning                                                  |
| ----------- | -------------------------------------------------------- |
| Translation | Converts data into an appropriate machine representation |
| Encoding    | Represents data in a suitable form                       |
| Encryption  | Protects data                                            |
| Decryption  | Recovers protected data                                  |
| Compression | Reduces data size                                        |
| Abstraction | Hides lower-level complexity                             |

---

# Deep Why Questions

### Why do we need translation?

Different systems may represent data differently.

A standard/appropriate representation allows the data to be interpreted correctly.

---

### Why compress data?

Because smaller data can reduce the amount of data that needs to be transported.

---

### Why encrypt data?

Because data travelling through a network should not simply be readable by unintended parties.

---

# 6. Layer 5 — Session Layer

## Main Responsibility

The source says the session layer helps with:

> **"setting up and managing the connections"**

and enables:

- Sending data
- Receiving data
- Termination of connected sessions

---

# Session Lifecycle

Conceptually:

```text
Session
   ↓
Establish
   ↓
Maintain
   ↓
Exchange data
   ↓
Terminate
```

---

# 6.1 Authentication

Before a session is established, authentication may happen.

Example:

```text
Username
Password
   ↓
Authentication
```

Authentication answers:

> "Who are you?"

---

# 6.2 Authorization

After authentication, authorization determines whether the user has permission.

Example:

```text
User authenticated
       ↓
Does user have permission?
       ↓
YES → Access
NO  → Denied
```

Authorization answers:

> "What are you allowed to access?"

---

# Authentication vs Authorization

| Concept        | Question                    |
| -------------- | --------------------------- |
| Authentication | Who are you?                |
| Authorization  | What are you allowed to do? |

---

# 6.3 Session Example — Online Shopping

The source uses an online shopping example such as Flipkart/Amazon.

Conceptually:

```text
User
 ↓
Login
 ↓
Session created
 ↓
Shopping
 ↓
Payment
 ↓
Process completed
 ↓
Logout/session termination
```

The session layer conceptually deals with managing this communication session.

---

# 6.4 Abstraction Between Layers

The session layer assumes that the lower layers will perform their responsibilities.

For example:

```text
Session Layer
      ↓
"I establish/manage the session."
      ↓
Transport Layer
      ↓
"I handle data transportation."
```

The session layer doesn't need to perform the transport layer's entire job itself.

---

# Deep Why Question

### Why separate session management from data transportation?

Because establishing/managing a communication session and actually transporting data are different responsibilities.

Dividing responsibilities makes the overall networking process easier to understand and manage.

---

# 7. Layer 4 — Transport Layer

The transport layer is responsible for transporting data between applications.

The source specifically mentions:

- TCP
- UDP
- Segmentation
- Port numbers
- Sequence numbers
- Flow control
- Error control
- Checksum
- Connection-oriented transmission
- Connectionless transmission

---

# 7.1 Protocols

The source says:

> **"Protocols are nothing but how data is transferred."**

Two important protocols mentioned:

```text
TCP
UDP
```

---

# 7.2 Segmentation

Large application data is not necessarily transferred as one giant piece.

The transport layer divides data into smaller units.

This is called:

> **Segmentation**

Conceptually:

```text
Large data
──────────────────────
        ↓
Transport Layer
        ↓
┌─────┐ ┌─────┐ ┌─────┐
│Seg 1│ │Seg 2│ │Seg 3│
└─────┘ └─────┘ └─────┘
```

The source calls these smaller units:

> **Segments**

---

# 7.3 Port Numbers

Every segment contains:

- Source port number
- Destination port number

Why?

Because the destination computer may be running many applications.

For example:

```text
Computer
├── Chrome
├── WhatsApp
├── Email
└── Game
```

The port information helps the data reach the appropriate application.

---

# 7.4 Sequence Number

When data is divided:

```text
Data
 ↓
Segment 1
Segment 2
Segment 3
Segment 4
```

The segments may need to be reassembled in the correct order.

The source says:

> **"sequence number basically helps to reassemble the segments in the correct order."**

Conceptually:

```text
Received:

Segment 3
Segment 1
Segment 4
Segment 2

        ↓

Sequence numbers

        ↓

1 → 2 → 3 → 4
```

---

# 7.5 Flow Control

The source gives the following idea:

Suppose:

```text
Server sends = 40 Mbps
Client receives = 20 Mbps
```

If the sender keeps sending at 40 Mbps, the receiver may not be able to process the data at the same rate.

Therefore:

> Flow control controls the amount of data being transferred.

Simple analogy:

Imagine filling a bottle.

```text
Tap →→→→→ Bottle
```

If water enters faster than the bottle can handle:

```text
Overflow!
```

Flow control prevents this kind of mismatch in data transfer.

---

# 7.6 Error Control

The source explains that some data may:

- Get lost
- Become corrupted

The transport layer deals with such errors.

---

# 7.7 Checksum

The source says a checksum is added to every data segment.

Its purpose is to help determine whether the received data is valid/correct.

Conceptually:

```text
Data
 ↓
Checksum added
 ↓
Transmission
 ↓
Receiver
 ↓
Check data
```

---

# 7.8 TCP

The source describes TCP as:

> **Connection-oriented transmission**

The basic idea:

```text
Sender
   ↓
Send data
   ↓
Receiver
   ↓
Acknowledgement
   ↓
Sender knows data was received
```

The source gives the example:

```text
Sender → Data → Receiver
Sender ← ACK  ← Receiver
```

The acknowledgement tells the sender that the receiver received the data.

---

# TCP Example

Suppose you transfer a file.

```text
File
 ↓
Segments
 ↓
TCP
 ↓
Receiver
 ↓
Acknowledgements
```

TCP can be used where reliable delivery matters.

The source mentions:

- Email
- File transfer

as examples.

---

# 7.9 UDP

The source describes UDP as:

> **Connectionless-oriented transmission**

The source says UDP is faster because it does not provide feedback about whether data was lost.

Conceptually:

```text
Sender
  ↓
Data
  ↓
Receiver

No acknowledgement required
```

The source gives examples such as:

- Video conferencing
- Gaming

The source explains that some packets may get lost with UDP.

---

# TCP vs UDP

| Feature                  | TCP                  | UDP                        |
| ------------------------ | -------------------- | -------------------------- |
| Type mentioned in source | Connection-oriented  | Connectionless             |
| Acknowledgement          | Yes                  | No feedback mentioned      |
| Reliability              | Higher emphasis      | Less emphasis              |
| Speed                    | More overhead        | Faster                     |
| Example                  | Email, file transfer | Video conferencing, gaming |

---

# Deep Why Questions — Transport Layer

### Why divide data into segments?

Because large data can be handled as smaller units.

---

### Why are port numbers needed?

Because a computer can have multiple applications communicating simultaneously.

The data must reach the appropriate application.

---

### Why are sequence numbers needed?

Because multiple segments need to be reconstructed in the correct order.

---

### Why is flow control needed?

Because the sender and receiver may operate at different rates.

---

### Why does TCP send acknowledgements?

To provide feedback that data has been received.

---

### Why might UDP be used for gaming?

The source emphasizes speed and the absence of feedback/retransmission overhead. For real-time applications, continuing with current data can be useful even if some data is lost.

---

# 8. Layer 3 — Network Layer

The source describes the Network layer as responsible for transmission of data segments from one computer to another computer located in a **different network**.

---

# Main Responsibilities

The source mentions:

1. Logical addressing
2. IP addressing
3. Routing
4. Packet creation
5. Determining paths
6. Load balancing

---

# 8.1 Logical Addressing

IP addressing is described as:

> **Logical addressing**

The Network layer assigns:

```text
Source IP
Destination IP
```

to the data.

The resulting unit is referred to as an:

> **IP packet**

---

# Why Does a Packet Need IP Addresses?

Imagine sending a parcel.

You need:

```text
From:
Chennai

To:
Bangalore
```

Similarly, networking needs source and destination information.

Conceptually:

```text
Source IP
     +
Destination IP
     +
Data
     ↓
IP Packet
```

---

# 8.2 Routing

The source says routing means:

> Moving a data packet from source to destination.

The Network layer determines how packets should travel.

Conceptually:

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

---

# 8.3 Choosing a Path

The source asks the idea:

> What is the best path to take to send data from your computer to your friend's computer?

There can be different possible paths.

Conceptually:

```text
          Router B
         /        \
A ------            ------ D
         \        /
          Router C
```

The network needs to determine an appropriate path.

---

# 8.4 Routing Protocols

The source mentions:

- Routing protocols
- Dijkstra algorithm

and says these will be covered later.

---

# 8.5 Load Balancing

The source also mentions load balancing at the Network layer.

The idea is to prevent a path/network from becoming overloaded.

Conceptually:

```text
Traffic
  ↓
Can choose among paths
  ↓
Avoid excessive load
```

---

# 8.6 Router

The source associates routers with the Network layer.

Conceptually:

```text
Network A
    ↓
 Router
    ↓
Network B
```

A router helps move packets between networks.

---

# Deep Why Questions

### Why does the Network layer need IP addresses?

Because the packet needs logical source and destination information so that it can be routed toward the destination.

---

### Why can't we simply send data directly?

Because the sender and receiver may be on different networks and may require intermediate devices.

---

### Why is routing necessary?

Because there can be multiple possible paths between source and destination.

---

# 9. Layer 2 — Data Link Layer

The Data Link layer works with communication between computers/hosts over a more direct network link.

The source explains two different types of addressing:

```text
Network Layer
    ↓
Logical Addressing
    ↓
IP addresses

Data Link Layer
    ↓
Physical Addressing
    ↓
MAC addresses
```

---

# 9.1 MAC Address

The source describes a MAC address as:

> **"a 12-digit alpha numeric number of the network interface of your computer."**

The important idea is that different network interfaces can have different MAC addresses.

For example:

```text
Computer
├── Wi-Fi interface → MAC address A
├── Bluetooth       → MAC address B
└── Other interface → another MAC address
```

---

# Important

A computer does not necessarily have only one MAC address.

Different network interfaces can have their own MAC addresses.

---

# 9.2 Frame

The source says:

> **"frame is basically a data unit of the data link layer."**

At the Data Link layer, MAC addresses are used to form a frame.

Conceptually:

```text
IP Packet
    ↓
Add MAC information
    ↓
Frame
```

---

# 9.3 Physical Addressing

The Data Link layer performs:

> **Physical addressing**

The source contrasts this with logical addressing.

```text
Logical addressing
→ IP
→ Network layer

Physical addressing
→ MAC
→ Data Link layer
```

---

# 9.4 Media Access Control

The source mentions:

> **Media Access Control**

This deals with techniques used to get frames:

- Onto the medium
- Off the medium

The source also mentions:

- Error detection
- Controlling how data is placed/received from the medium

---

# Data Link Layer — Two Main Functions Mentioned

The source says it:

### Function 1

Allows upper layers of the OSI model to access the frames.

### Function 2

Controls how data is placed and received from the media using Media Access Control techniques.

---

# Example

Suppose:

```text
Computer A
   ↓
Wi-Fi network
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

The data is represented as a frame.

---

# Deep Why Question

### Why do we need both IP and MAC addresses?

The source distinguishes them as:

```text
IP
→ Logical addressing
→ Network layer

MAC
→ Physical addressing
→ Data Link layer
```

They serve different addressing purposes in the networking process.

---

# 10. Layer 1 — Physical Layer

The Physical layer is the hardware-oriented layer.

The source says it contains:

> **"Hardware"**

and deals with:

- Wires
- Physical media
- Electrical signals
- Light signals
- Radio signals

---

# 10.1 Bits

The Physical layer works with bits:

```text
0
1
0
1
1
0
```

Unlike higher layers, the source says it does not work with units such as:

- Packets
- Datagrams
- Segments

Instead, it deals with physical transmission of bits.

---

# 10.2 How Are Bits Transmitted?

The source mentions different physical forms.

### Electrical Cable

```text
Bits
 ↓
Electrical signals
 ↓
Cable
```

### Optical Fiber

```text
Bits
 ↓
Light signals
 ↓
Optical fiber
```

### Wi-Fi

```text
Bits
 ↓
Radio signals
 ↓
Wireless medium
```

---

# 10.3 Receiving Data

At the receiving side:

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

The source says the Physical layer receives the signal, converts it into bits, and passes it to the Data Link layer as a frame.

---

# Simple Analogy

Imagine a road.

The Physical layer is like the actual:

- Road
- Vehicle movement
- Physical medium

It is concerned with how the information physically travels.

---

# Deep Why Question

### Why does the Physical layer deal with signals instead of packets?

Because packets are logical data structures handled by higher layers.

Eventually, the information must physically travel through some medium.

That physical representation can be:

```text
Electrical
Light
Radio
```

---

# 11. OSI Model — Complete Data Flow

Now combine all seven layers.

Suppose:

```text
You send "Hello" to your friend on WhatsApp.
```

---

# Sender Side

## Step 1 — Application Layer

You type:

```text
Hello
```

The application handles the user interaction.

```text
Application
    ↓
"Hello"
```

---

## Step 2 — Presentation Layer

The data may undergo operations described by the source:

```text
Translation
Encoding
Encryption
Compression
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

## Step 3 — Session Layer

A communication session is established/managed.

```text
Session
   ↓
Manage communication
```

---

## Step 4 — Transport Layer

The data is divided into segments.

```text
Large data
   ↓
Segment 1
Segment 2
Segment 3
```

The transport layer adds information such as:

```text
Source port
Destination port
Sequence number
Checksum
```

depending on the protocol/process being discussed.

---

## Step 5 — Network Layer

The Network layer adds:

```text
Source IP
Destination IP
```

and forms an IP packet.

```text
Segment
   ↓
IP addressing
   ↓
Packet
```

---

## Step 6 — Data Link Layer

MAC addresses are used.

```text
Packet
   ↓
MAC addressing
   ↓
Frame
```

---

## Step 7 — Physical Layer

The frame ultimately becomes a physical signal representation.

```text
Frame
 ↓
Bits
 ↓
Physical signal
```

The signal can be represented through:

```text
Electrical signal
       OR
Light signal
       OR
Radio signal
```

---

# Sender-Side Flow

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

---

# Receiver Side

At the receiver, the process moves upward.

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

---

# Complete Communication

```text
                 SENDER
                    │
                    ▼
            ┌──────────────┐
            │ Application  │
            ├──────────────┤
            │ Presentation │
            ├──────────────┤
            │ Session      │
            ├──────────────┤
            │ Transport    │
            ├──────────────┤
            │ Network      │
            ├──────────────┤
            │ Data Link    │
            ├──────────────┤
            │ Physical     │
            └──────┬───────┘
                   │
                   ▼
             Network/Internet
                   │
                   ▼
            ┌──────┴───────┐
            │ Physical     │
            ├──────────────┤
            │ Data Link    │
            ├──────────────┤
            │ Network      │
            ├──────────────┤
            │ Transport    │
            ├──────────────┤
            │ Session      │
            ├──────────────┤
            │ Presentation │
            ├──────────────┤
            │ Application  │
            └──────────────┘
                   │
                   ▼
                RECEIVER
```

---

# 12. Data Units at Different Layers

The source explicitly mentions different names for data at different layers.

| OSI Layer    | Data Unit Mentioned |
| ------------ | ------------------- |
| Application  | Data/message        |
| Presentation | Data                |
| Session      | Data                |
| Transport    | Segment             |
| Network      | Packet              |
| Data Link    | Frame               |
| Physical     | Bits                |

Remember:

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

This is one of the most important distinctions in the chapter.

| Feature               | IP Address               | MAC Address                           |
| --------------------- | ------------------------ | ------------------------------------- |
| Layer                 | Network                  | Data Link                             |
| Addressing type       | Logical                  | Physical                              |
| Used for              | Network-level addressing | Physical/network-interface addressing |
| Data unit association | Packet                   | Frame                                 |
| Source's terminology  | Logical addressing       | Physical addressing                   |

---

# Example

Suppose:

```text
Computer A
IP  → Source IP
MAC → Source MAC
```

and:

```text
Computer B
IP  → Destination IP
MAC → Destination MAC
```

The packet contains IP addressing.

The frame contains MAC addressing.

---

# 14. Logical Addressing vs Physical Addressing

## Logical Addressing

Performed at the Network layer.

```text
Source IP
Destination IP
```

Used for network-level routing.

---

## Physical Addressing

Performed at the Data Link layer.

```text
Source MAC
Destination MAC
```

Used for physical/link-level delivery.

---

# Why Both?

Imagine a postal system.

### IP Address

Similar to the larger destination information:

```text
Country
City
Area
```

### MAC Address

More like identifying a particular local network interface/device on the local link.

The source's key distinction is:

```text
IP → Logical
MAC → Physical
```

---

# 15. Deep Why Questions — OSI Model

## Q1. Why does the OSI model have layers?

Because networking is complex.

Breaking it into layers allows each part of communication to have a specific responsibility.

---

## Q2. Why can't everything be handled by one layer?

Because communication involves many different responsibilities:

```text
Application interaction
Translation
Session management
Transport
Routing
MAC addressing
Physical transmission
```

Keeping these responsibilities separate makes the model easier to understand.

---

## Q3. Why does the Transport layer need port numbers?

Because one computer can have many applications.

For example:

```text
Computer
 ├── Chrome
 ├── WhatsApp
 ├── Email
 └── Game
```

The destination port helps identify the appropriate application/service.

---

## Q4. Why does the Network layer use IP?

Because the Network layer needs logical addressing to move data between networks.

---

## Q5. Why does the Data Link layer need MAC?

Because the source distinguishes physical addressing from logical addressing.

---

## Q6. Why does the Physical layer need signals?

Because eventually bits have to travel through an actual medium.

Examples mentioned:

```text
Copper/electrical
Optical fiber/light
Wi-Fi/radio
```

---

## Q7. Why can't IP addresses alone perform the entire job?

The source distinguishes Network-layer logical addressing from Data Link-layer physical addressing.

Therefore, different layers handle different parts of delivery.

---

## Q8. Why does TCP use acknowledgement?

The source explains that the receiver can send an acknowledgement to indicate that data was received.

---

## Q9. Why doesn't UDP provide the same feedback?

The source says UDP does not provide feedback about whether data was lost, which contributes to its faster behavior.

---

## Q10. Why is flow control necessary?

Because sender and receiver can operate at different speeds.

Example:

```text
Sender = 40 Mbps
Receiver = 20 Mbps
```

The sender may need to slow down.

---

## Q11. Why are sequence numbers necessary?

Because data can be divided into multiple segments.

The receiver needs to reconstruct them in the proper order.

---

## Q12. Why is checksum added?

To help determine whether received data is correct or corrupted.

---

# 16. Hands-On Experience — OSI Model

The best way to understand OSI is to observe actual network communication.

---

# Practical 1 — Find Your IP Address

## Linux

Run:

```bash
ip addr
```

or:

```bash
ip a
```

Look for your network interface.

You may see something conceptually like:

```text
inet 192.168.x.x
```

This is an IP address assigned to the interface.

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

That is the MAC address associated with that network interface.

---

# Practical 3 — Compare IP and MAC

Run:

```bash
ip addr
```

and:

```bash
ip link
```

Identify:

```text
IP address
MAC address
```

Then remember:

```text
IP
↓
Network layer
↓
Logical addressing

MAC
↓
Data Link layer
↓
Physical addressing
```

---

# Practical 4 — Test Connectivity

Run:

```bash
ping google.com
```

Observe the output.

You are testing whether communication with the destination is possible.

---

# Practical 5 — Observe the Route

Run:

```bash
traceroute google.com
```

If `traceroute` is not installed:

```bash
sudo apt install traceroute
```

Then:

```bash
traceroute google.com
```

You can observe multiple hops between your machine and the destination.

This helps visualize the Network layer's routing concept.

---

# Practical 6 — DNS Observation

Run:

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

This lets you observe DNS-related information.

The source mentioned DNS as an application-layer protocol/topic.

---

# Practical 7 — Inspect Listening Ports

Run:

```bash
ss -tuln
```

You can observe ports on which services are listening.

This helps connect the practical system to the Transport layer concept of port numbers.

---

# Practical 8 — Capture Packets

Install Wireshark:

```bash
sudo apt install wireshark
```

Open Wireshark and start capturing traffic.

Then:

```bash
ping google.com
```

Observe packets.

Try filtering:

```text
icmp
```

You can inspect packet information and begin connecting practical network traffic to the layered model.

---

# Practical 9 — Observe TCP

In Wireshark, try:

```text
tcp
```

You can inspect TCP traffic.

Look for concepts such as:

- Source port
- Destination port
- Sequence information
- Acknowledgement information

---

# Practical 10 — Observe UDP

Use:

```text
udp
```

in Wireshark.

Compare UDP traffic with TCP traffic.

Think:

```text
TCP
→ connection-oriented
→ acknowledgement/feedback

UDP
→ connectionless
→ no feedback about loss
```

according to the source's overview.

---

# Mini Practical Challenge

Run:

```bash
ip a
```

Answer:

1. What is your IP address?
2. Which interface has it?
3. What is the interface's MAC address?

Then run:

```bash
ip route
```

Answer:

4. What is your default route?
5. Which interface is used?

Then:

```bash
ping google.com
```

Answer:

6. What happens?
7. What information does `ping` show?

Then:

```bash
traceroute google.com
```

Answer:

8. How many hops are displayed?
9. Why are there multiple hops?

---

# OSI Model — One Real-Life Example

Suppose you send:

```text
"Hey!"
```

to your friend through a messaging application.

---

## Layer 7 — Application

You type:

```text
Hey!
```

The messaging application handles your interaction.

---

## Layer 6 — Presentation

The data may be:

```text
Translated
Encoded
Encrypted
Compressed
```

according to the responsibilities described in the source.

---

## Layer 5 — Session

The communication session is managed.

---

## Layer 4 — Transport

The data can be:

```text
Divided into segments
```

and information such as:

```text
Ports
Sequence number
Checksum
```

can be involved.

TCP or UDP may be used.

---

## Layer 3 — Network

The Network layer deals with:

```text
Source IP
Destination IP
Routing
```

and forms an IP packet.

---

## Layer 2 — Data Link

The packet is handled at the link level with:

```text
MAC addresses
```

forming a:

```text
Frame
```

---

## Layer 1 — Physical

The data becomes physical signals:

```text
Electrical
OR
Light
OR
Radio
```

---

# Receiver

The reverse process happens conceptually:

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

# Important Concept — Peer Communication

The source explains that conceptually each layer can be thought of as communicating with the corresponding layer on the other machine.

For example:

```text
My Application Layer
        ↕
Friend's Application Layer
```

or:

```text
My Transport Layer
        ↕
Friend's Transport Layer
```

However, this is a **conceptual model**.

The actual data travels through the lower layers, physical medium, networks, and then back up the layers at the receiver.

---

# Conceptual Route

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

# Important Exam Summary — OSI

| Layer           | Main Idea                                                          |
| --------------- | ------------------------------------------------------------------ |
| 7. Application  | User/application interaction                                       |
| 6. Presentation | Translation, encoding, encryption, compression, abstraction        |
| 5. Session      | Establishing, managing and terminating sessions                    |
| 4. Transport    | Segmentation, ports, sequence numbers, flow/error control, TCP/UDP |
| 3. Network      | IP addressing, packets, routing                                    |
| 2. Data Link    | MAC addressing, frames, media access                               |
| 1. Physical     | Hardware, bits, electrical/light/radio signals                     |

---

# Chapter 11 — TCP/IP Model (5 Layers)

# 17. What is the TCP/IP Model?

The source introduces another networking model:

> **TCP/IP Model**

The source says it is also known as the:

> **Internet Protocol Suite**

The source explains that it is similar to the OSI model but has fewer layers.

---

# 18. TCP/IP Model Layers

The source lists **5 layers**:

```text
1. Application
2. Transport
3. Network
4. Data Link
5. Physical
```

---

# TCP/IP Model

```text
┌────────────────────┐
│ Application        │
├────────────────────┤
│ Transport          │
├────────────────────┤
│ Network            │
├────────────────────┤
│ Data Link          │
├────────────────────┤
│ Physical           │
└────────────────────┘
```

---

# 19. OSI vs TCP/IP — Source-Based Comparison

The source says the models are:

> **"mostly similar"**

but differ in their layer structure.

The key difference described is that TCP/IP has **5 layers instead of 7**.

---

# Layer Mapping Given by the Source

The source explains that the OSI model's:

```text
Application
Presentation
Session
```

are merged into the TCP/IP model's:

```text
Application
```

The remaining layers correspond:

```text
OSI                         TCP/IP

Application ───────┐
Presentation ──────┼────── Application
Session ───────────┘

Transport ──────────────── Transport

Network ────────────────── Network

Data Link ──────────────── Data Link

Physical ───────────────── Physical
```

---

# Comparison Table

| OSI Model    | TCP/IP Model |
| ------------ | ------------ |
| Application  | Application  |
| Presentation | Application  |
| Session      | Application  |
| Transport    | Transport    |
| Network      | Network      |
| Data Link    | Data Link    |
| Physical     | Physical     |

Therefore:

```text
OSI = 7 layers

TCP/IP = 5 layers
```

---

# Source's Main Point

The source states that:

> The TCP/IP model is more practically used.

The uploaded source ends immediately after introducing this comparison, so no additional TCP/IP details are added here.

---

# 20. Deep Why Questions — TCP/IP

## Q1. Why does TCP/IP have fewer layers?

According to the source, the TCP/IP model reduces the number of layers by combining:

```text
OSI:
Application
Presentation
Session

        ↓

TCP/IP:
Application
```

---

## Q2. What is common between OSI and TCP/IP?

Both models divide networking responsibilities into layers.

The source describes TCP/IP as similar to OSI.

---

## Q3. What is the biggest structural difference?

```text
OSI
→ 7 layers

TCP/IP
→ 5 layers
```

The TCP/IP Application layer combines the OSI:

```text
Application
Presentation
Session
```

---

# 21. Hands-On Experience — TCP/IP

You can connect the TCP/IP model to the same Linux commands.

---

## IP Information

```bash
ip a
```

Relates to:

```text
Network layer
```

---

## MAC Information

```bash
ip link
```

Relates to:

```text
Data Link layer
```

---

## Routing

```bash
ip route
```

Relates to:

```text
Network layer
```

---

## Connectivity

```bash
ping google.com
```

Helps observe network communication.

---

## DNS

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

The source mentions DNS as an application-layer protocol/topic.

---

## Ports

```bash
ss -tuln
```

Helps observe transport-layer port concepts.

---

# 22. Interview Revision

## Q1. What is OSI?

The OSI model stands for:

> **Open Systems Interconnection model**

It provides a standard conceptual framework for communication between computers.

---

## Q2. How many layers does OSI have?

```text
7
```

---

## Q3. Name all seven layers.

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

## Q4. What does the Application layer do?

It provides the layer where users interact with network applications such as browsers and messaging applications.

---

## Q5. What does the Presentation layer do?

The source mentions:

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

It helps:

```text
Establish sessions
Manage sessions
Send/receive data
Terminate sessions
```

The source also discusses authentication and authorization in this context.

---

## Q7. What does the Transport layer do?

It handles concepts including:

```text
Segmentation
Port numbers
Sequence numbers
Flow control
Error control
Checksum
TCP
UDP
```

---

## Q8. What is a segment?

A smaller data unit produced when data is divided at the Transport layer.

---

## Q9. Why are port numbers used?

To help data reach the correct application/service on a computer.

---

## Q10. What is the Network layer responsible for?

The source mentions:

```text
Logical addressing
IP addresses
Packet creation
Routing
Path selection
Load balancing
```

---

## Q11. What is logical addressing?

The source associates logical addressing with:

```text
IP addressing
```

at the Network layer.

---

## Q12. What is a packet?

The source describes the Network layer as assigning source and destination IP addresses and forming an:

> **IP packet**

---

## Q13. What is the Data Link layer responsible for?

The source discusses:

```text
Physical addressing
MAC addresses
Frames
Media Access Control
Error detection
```

---

## Q14. What is a MAC address?

The source describes it as a 12-digit alphanumeric number associated with a network interface.

---

## Q15. What is a frame?

A frame is the Data Link layer's data unit.

---

## Q16. What does the Physical layer do?

It deals with:

```text
Hardware
Cables
Physical media
Bits
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

The source describes TCP as:

```text
Connection-oriented transmission
```

with acknowledgement/feedback.

---

## Q19. What is UDP?

The source describes UDP as:

```text
Connectionless transmission
```

and explains that it does not provide feedback about whether data was lost.

---

## Q20. Why can UDP be faster?

The source explains that it does not provide the same feedback mechanism, reducing this overhead.

---

## Q21. Give examples of TCP use from the source.

```text
Email
File transfer
```

---

## Q22. Give examples of UDP use from the source.

```text
Video conferencing
Gaming
```

---

## Q23. What is the TCP/IP model?

The source introduces it as another model, also called the:

> **Internet Protocol Suite**

---

## Q24. How many layers does TCP/IP have according to the source?

```text
5
```

---

## Q25. Name the TCP/IP layers.

```text
Application
Transport
Network
Data Link
Physical
```

---

## Q26. How are OSI and TCP/IP different?

Main structural difference discussed in the source:

```text
OSI = 7 layers

TCP/IP = 5 layers
```

The TCP/IP Application layer combines the OSI:

```text
Application
Presentation
Session
```

---

# Final Mental Model

When you send a message:

```text
                 USER
                   │
                   ▼
          ┌─────────────────┐
          │  APPLICATION    │
          │ "Send message"  │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ PRESENTATION    │
          │ Translation     │
          │ Encryption      │
          │ Compression     │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ SESSION         │
          │ Manage session  │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ TRANSPORT       │
          │ TCP / UDP       │
          │ Segments        │
          │ Ports           │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ NETWORK         │
          │ IP              │
          │ Routing         │
          │ Packets         │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ DATA LINK       │
          │ MAC             │
          │ Frames          │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ PHYSICAL        │
          │ Bits            │
          │ Signals         │
          └────────┬────────┘
                   ▼
              INTERNET
                   │
                   ▼
          ┌─────────────────┐
          │ PHYSICAL        │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ DATA LINK       │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ NETWORK         │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ TRANSPORT       │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ SESSION         │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ PRESENTATION    │
          └────────┬────────┘
                   ▼
          ┌─────────────────┐
          │ APPLICATION     │
          │ Friend receives │
          │ the message     │
          └─────────────────┘
```

---

# The Most Important Chain to Remember

```text
APPLICATION
    ↓
PRESENTATION
    ↓
SESSION
    ↓
TRANSPORT
    ↓
NETWORK
    ↓
DATA LINK
    ↓
PHYSICAL
```

Think:

```text
Application → What the user wants
Presentation → Prepare/represent the data
Session → Manage communication session
Transport → Deliver data between applications
Network → Find the route between networks
Data Link → Deliver across the local/link level
Physical → Actually transmit the bits
```

---

# The Most Important Addressing Concept

```text
IP Address
    ↓
Logical Address
    ↓
Network Layer
```

versus:

```text
MAC Address
    ↓
Physical Address
    ↓
Data Link Layer
```

---

# The Most Important Data-Unit Chain

```text
Application
    ↓
Data
    ↓
Transport
    ↓
Segment
    ↓
Network
    ↓
Packet
    ↓
Data Link
    ↓
Frame
    ↓
Physical
    ↓
Bits
```

---

# OSI vs TCP/IP — Final Memory Diagram

```text
                 OSI                    TCP/IP

        ┌─────────────────┐       ┌─────────────────┐
        │ Application     │       │                 │
        ├─────────────────┤       │                 │
        │ Presentation    │ ────► │  Application    │
        ├─────────────────┤       │                 │
        │ Session         │       │                 │
        ├─────────────────┤       ├─────────────────┤
        │ Transport       │ ────► │  Transport      │
        ├─────────────────┤       ├─────────────────┤
        │ Network         │ ────► │  Network        │
        ├─────────────────┤       ├─────────────────┤
        │ Data Link       │ ────► │  Data Link      │
        ├─────────────────┤       ├─────────────────┤
        │ Physical        │ ────► │  Physical       │
        └─────────────────┘       └─────────────────┘

             7 Layers                 5 Layers
```

---

# One-Minute Revision

```text
OSI
→ Open Systems Interconnection
→ 7 layers

7. Application
→ User/application interaction

6. Presentation
→ Translation
→ Encoding
→ Encryption/decryption
→ Compression
→ Abstraction

5. Session
→ Establish/manage/terminate sessions
→ Authentication/authorization discussed

4. Transport
→ TCP/UDP
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
→ Physical addressing
→ Frames
→ Media Access Control
→ Error detection

1. Physical
→ Hardware
→ Bits
→ Electrical signals
→ Light signals
→ Radio signals

TCP/IP
→ Internet Protocol Suite
→ 5 layers

Application
Transport
Network
Data Link
Physical

OSI:
Application + Presentation + Session
                ↓
TCP/IP:
           Application
```

---

# Final Self-Test

Without looking at the notes, try answering these:

1. What does OSI stand for?
2. Why was the OSI model developed?
3. How many OSI layers are there?
4. Name all seven layers in order.
5. What happens at the Application layer?
6. What are the major responsibilities of the Presentation layer?
7. What is translation?
8. What is encryption?
9. What is compression?
10.   What is the purpose of the Session layer?
11.   Authentication vs authorization?
12.   What is segmentation?
13.   What is a segment?
14.   Why are port numbers required?
15.   Why are sequence numbers required?
16.   What is flow control?
17.   What is error control?
18.   What is a checksum?
19.   TCP vs UDP?
20.   What is logical addressing?
21.   Why does the Network layer use IP?
22.   What is routing?
23.   What is load balancing?
24.   What is physical addressing?
25.   What is a MAC address?
26.   What is a frame?
27.   What is Media Access Control?
28.   What happens at the Physical layer?
29.   What are the different physical signal types mentioned?
30.   What is the complete sender-side OSI flow?
31.   What is the complete receiver-side OSI flow?
32.   What is the difference between an IP address and MAC address?
33.   What is a segment?
34.   What is a packet?
35.   What is a frame?
36.   What are bits?
37.   What is the TCP/IP model?
38.   How many layers does the TCP/IP model have according to the source?
39.   Which three OSI layers are merged into TCP/IP's Application layer?
40.   What is the major structural difference between OSI and TCP/IP?

---

# Core Mental Model

If you remember only one thing:

```text
                    OSI

        WHAT APPLICATION WANTS
                 ↓
          APPLICATION
                 ↓
        PREPARE THE DATA
          PRESENTATION
                 ↓
        MANAGE THE SESSION
             SESSION
                 ↓
       DELIVER BETWEEN APPS
            TRANSPORT
                 ↓
       FIND THE DESTINATION
             NETWORK
                 ↓
       LOCAL/LINK DELIVERY
            DATA LINK
                 ↓
       SEND ACTUAL SIGNALS
             PHYSICAL
```

And remember the addressing:

```text
IP  → Logical → Network layer
MAC → Physical → Data Link layer
```

And the data units:

```text
Transport → Segment
Network   → Packet
Data Link → Frame
Physical  → Bits
```

And the model comparison:

```text
OSI    → 7 layers
TCP/IP → 5 layers
```

> **Source boundary:** The uploaded material ends during the introduction of the TCP/IP model's practical usage comparison. The notes above therefore do not add a detailed TCP/IP explanation beyond what the supplied material actually contains.
