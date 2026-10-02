# Port Numbers, Internet Speed, Upload/Download, Guided & Unguided Communication, and Submarine Cables

---

# Table of Contents

- [Chapter 4 — Port Numbers](#chapter-6--port-numbers)
   - [1. What Is a Port Number?](#1-what-is-a-port-number)
   - [2. Why Is a Port Number 16 Bits?](#2-why-is-a-port-number-16-bits)
   - [3. How Many Port Numbers Are Possible?](#3-how-many-port-numbers-are-possible)
   - [4. Why Do We Need Ports?](#4-why-do-we-need-ports)
   - [5. Ports and Web Browsers](#5-ports-and-web-browsers)
   - [6. Well-Known Ports](#6-well-known-ports)
   - [7. Reserved Ports](#7-reserved-ports)
   - [8. Registered Ports](#8-registered-ports)
   - [9. MongoDB Port Example](#9-mongodb-port-example)
   - [10. SQL Server Port Example](#10-sql-server-port-example)
   - [11. Port Number Ranges](#11-port-number-ranges)
   - [12. IP Address vs Port Number](#12-ip-address-vs-port-number)
   - [13. Real-World Analogy](#13-real-world-analogy)
   - [14. Deep Why Questions — Ports](#14-deep-why-questions--ports)

- [Internet and ISP](#internet-and-isp)
   - [15. Connecting Two Computers](#15-connecting-two-computers)
   - [16. What Is an ISP?](#16-what-is-an-isp)
   - [17. The Internet as a Network](#17-the-internet-as-a-network)

- [Internet Speed](#internet-speed)
   - [18. What Does Internet Speed Mean?](#18-what-does-internet-speed-mean)
   - [19. Bit](#19-bit)
   - [20. Mbps](#20-mbps)
   - [21. Gbps](#21-gbps)
   - [22. Kbps](#22-kbps)
   - [23. Bits vs Bytes](#23-bits-vs-bytes)
   - [24. Upload Speed](#24-upload-speed)
   - [25. Download Speed](#25-download-speed)
   - [26. How to Test Internet Speed](#26-how-to-test-internet-speed)
   - [27. Deep Why Questions — Internet Speed](#27-deep-why-questions--internet-speed)

- [Communication Between Computers](#communication-between-computers)
   - [28. How Do Two Computers Communicate?](#28-how-do-two-computers-communicate)
   - [29. Guided Communication](#29-guided-communication)
   - [30. Unguided Communication](#30-unguided-communication)
   - [31. Guided vs Unguided](#31-guided-vs-unguided)
   - [32. Examples of Guided Communication](#32-examples-of-guided-communication)
   - [33. Examples of Unguided Communication](#33-examples-of-unguided-communication)

- [Chapter 5 — Submarine Cables](#chapter-7--submarine-cables)
   - [34. How Are Countries Connected?](#34-how-are-countries-connected)
   - [35. Submarine Cables](#35-submarine-cables)
   - [36. Optical Fibre Cables](#36-optical-fibre-cables)
   - [37. India and International Cable Connections](#37-india-and-international-cable-connections)
   - [38. Long-Distance Submarine Cables](#38-long-distance-submarine-cables)
   - [39. Who Operates the Infrastructure?](#39-who-operates-the-infrastructure)
   - [40. Are Internet Cables Really Under the Ocean?](#40-are-internet-cables-really-under-the-ocean)
   - [41. Why Don't Sharks/Fish Destroy the Cables?](#41-why-dont-sharksfish-destroy-the-cables)
   - [42. Other Physical Communication Media](#42-other-physical-communication-media)
   - [43. Wireless Communication](#43-wireless-communication)
   - [44. Bluetooth](#44-bluetooth)
   - [45. Wi-Fi](#45-wi-fi)
   - [46. Cellular Networks — 3G, 4G, LTE and 5G](#46-cellular-networks--3g-4g-lte-and-5g)
   - [47. Why Not Use Satellites for Everything?](#47-why-not-use-satellites-for-everything)

- [Complete Mental Model](#complete-mental-model)

- [Hands-On Experience](#hands-on-experience)

- [Deep Why Questions](#deep-why-questions)

- [Interview Questions](#interview-questions)

- [Quick Revision Sheet](#quick-revision-sheet)

---

# Chapter 4 — Port Numbers

## 1. What Is a Port Number?

In the previous chapter, we learned that an **IP address** helps identify a device/network endpoint.

But there is another problem.

A single computer can run many applications simultaneously.

For example:

```text
Your Computer
│
├── Chrome
├── VS Code
├── MongoDB
├── Node.js Server
├── Online Game
└── Chat Application
```

All these applications can communicate over a network.

So when network data reaches your computer, the computer needs to know:

> "Which application should receive this data?"

This is where **port numbers** are used.

---

## Definition from the Lecture

The instructor explains the concept as:

> "IP address will identify the computer but Port will be identifying the application."

The simplified mental model is:

```text
IP Address
    ↓
Which computer?

Port Number
    ↓
Which application/service?
```

---

# 2. Why Is a Port Number 16 Bits?

The lecture introduces port numbers as **16-bit numbers**.

A bit can have two possible values:

```text
0
1
```

Therefore, if a port number contains 16 bits:

```text
2^16
```

different combinations are possible.

---

## Binary Representation

A 16-bit value looks conceptually like:

```text
0000000000000000
```

to:

```text
1111111111111111
```

Therefore:

```text
2^16 = 65,536
```

possible numerical values exist.

Since counting starts at zero:

```text
0 → 65,535
```

are the possible numerical port values.

---

# 3. How Many Port Numbers Are Possible?

Formula:

```text
Number of possible ports = 2^16
```

Therefore:

```text
2^16
= 65,536
```

So:

```text
Port Range
0 ───────────────────────→ 65535
```

---

## Why 16 Bits?

A fixed-size 16-bit field provides enough values to distinguish many simultaneous network services/endpoints.

This allows a computer to have many different network endpoints.

---

# 4. Why Do We Need Ports?

Suppose your computer has:

```text
IP Address:
192.168.1.10
```

At the same time, you are running:

```text
Chrome
Email
Game
MongoDB
Node.js
```

Now Google sends data back to your computer.

The operating system needs to determine:

```text
Which application should receive this data?
```

The IP address only gets the packet to the appropriate network endpoint.

The port helps identify the appropriate application/service endpoint.

---

# 5. Ports and Web Browsers

The lecture uses the following example:

You type:

```text
google.com
```

Your browser sends a request to Google.

Conceptually:

```text
Browser
   |
   | Request
   ↓
Google
   |
   | Response
   ↓
Your Computer
```

When the response reaches your computer, the system needs to know:

```text
Should this data go to:

Chrome?
Email?
Game?
MongoDB?
Another application?
```

The networking stack uses port information to identify the appropriate communication endpoint.

---

# 6. Well-Known Ports

The lecture refers to certain commonly used ports as:

> "well-known ports"

These ports are standardized for commonly used services.

A classic example is:

```text
HTTP → Port 80
```

and:

```text
HTTPS → Port 443
```

So conceptually:

```text
HTTP
  ↓
Port 80
```

```text
HTTPS
  ↓
Port 443
```

---

## Why Standard Ports?

Imagine if every developer chose a random port for HTTP.

One computer might expect:

```text
HTTP → 5000
```

Another:

```text
HTTP → 8321
```

Another:

```text
HTTP → 4217
```

Standard ports provide common conventions.

---

# 7. Reserved Ports

The lecture explains the idea of reserved ports as ports associated with established/common services.

The traditional port-number classification is:

```text
0–1023
```

These are commonly called the **well-known/system port range**.

---

## Example

HTTP uses:

```text
80
```

HTTPS uses:

```text
443
```

These are inside:

```text
0–1023
```

---

# 8. Registered Ports

The lecture then discusses the range:

```text
1024
```

through approximately:

```text
49152
```

This corresponds to the commonly known **registered port range**:

```text
1024–49151
```

These ports are associated with registered applications/services.

---

## Port Classification

The standard conceptual division is:

|       Range | Common Name               | General Idea                     |
| ----------: | ------------------------- | -------------------------------- |
|      0–1023 | Well-known/System         | Common standardized services     |
|  1024–49151 | Registered                | Registered applications/services |
| 49152–65535 | Dynamic/Private/Ephemeral | Often used dynamically           |

---

# 9. MongoDB Port Example

The lecture gives MongoDB as an example and mentions:

```text
27017
```

MongoDB commonly uses:

```text
27017
```

as its default port.

For example:

```text
localhost:27017
```

means:

```text
localhost
   ↓
Your computer

27017
   ↓
MongoDB service
```

---

## Example

If your application runs on:

```text
localhost:3000
```

and MongoDB runs on:

```text
localhost:27017
```

then:

```text
localhost:3000
       ↓
Your backend application

localhost:27017
       ↓
MongoDB
```

Both services are on the same computer but use different ports.

---

# 10. SQL Server Port Example

The lecture mentions:

```text
1433
```

for SQL Server.

Microsoft SQL Server commonly uses:

```text
TCP 1433
```

as its default port for the default instance.

So:

```text
localhost:1433
```

can represent a SQL Server endpoint.

---

# 11. Port Number Ranges

The complete range is:

```text
0–65535
```

Conceptually:

```text
0
│
├── Well-known/System
│   0–1023
│
├── Registered
│   1024–49151
│
└── Dynamic / Private / Ephemeral
    49152–65535
│
65535
```

---

# 12. IP Address vs Port Number

This is one of the most important concepts.

Suppose:

```text
192.168.1.10:3000
```

Break it into:

```text
192.168.1.10
       ↓
IP address
```

and:

```text
3000
 ↓
Port
```

So:

```text
192.168.1.10:3000
```

means:

> Network endpoint at IP `192.168.1.10`, using port `3000`.

---

# 13. Real-World Analogy

Imagine a large apartment building.

```text
100 Main Street
```

is the building address.

Inside it:

```text
Apartment 101
Apartment 102
Apartment 103
...
```

The analogy is:

```text
IP Address
    ↓
Building address

Port
    ↓
Specific apartment/service
```

So:

```text
192.168.1.10:3000
```

can be mentally visualized as:

```text
Building:
192.168.1.10

Apartment:
3000
```

---

# 14. Deep Why Questions — Ports

## Q1. Why can't the IP address identify the application?

Because multiple applications can run on the same computer.

Example:

```text
192.168.1.10
│
├── Browser
├── Game
├── MongoDB
├── Node.js
└── Chat Application
```

The IP identifies the network endpoint.

The port helps identify the application/service endpoint.

---

## Q2. Why are ports numbers instead of application names?

Computers use structured numerical identifiers because networking protocols and operating systems need compact fields for identifying endpoints.

Instead of:

```text
Send to "Chrome"
```

network communication uses a numerical port.

---

## Q3. Why can two applications not normally listen on the exact same IP and port?

Because the operating system needs to uniquely associate an incoming network endpoint with a listening socket.

For example:

```text
127.0.0.1:3000
```

cannot normally have two unrelated servers simultaneously bind to the exact same address/port combination.

---

## Q4. Can two computers use the same port?

Yes.

For example:

```text
Computer A → 192.168.1.10:3000
Computer B → 192.168.1.20:3000
```

There is no conflict because the IP addresses are different.

---

## Q5. Can one computer use many ports?

Absolutely.

For example:

```text
localhost:3000
localhost:5000
localhost:8080
localhost:27017
```

can represent different services on the same machine.

---

# Internet and ISP

# 15. Connecting Two Computers

Imagine:

```text
Your Computer
      |
      |
   Internet
      |
      |
Friend's Computer
```

Your computer and your friend's computer may be in completely different countries.

The Internet provides the interconnected network infrastructure through which they can communicate.

---

# 16. What Is an ISP?

ISP stands for:

```text
Internet Service Provider
```

The instructor describes an ISP as:

> "a person that connects you with the entire of the internet"

More accurately, an ISP is a company or organization that provides Internet connectivity.

Examples generally include:

```text
Jio
Airtel
BSNL
ACT
```

depending on the user's location.

---

## Simple Analogy

Think of the ISP as a highway connection.

```text
Your House
    ↓
ISP
    ↓
Internet
    ↓
Other Networks
    ↓
Other Countries
```

Your ISP provides your connection to the wider Internet.

---

# 17. The Internet as a Network

The Internet is not one giant computer.

It is a massive interconnected collection of:

```text
Computers
Servers
Routers
Networks
ISPs
Data centers
Undersea cables
Fiber links
Wireless networks
```

Conceptually:

```text
Your Device
    ↓
Home Router
    ↓
ISP
    ↓
Internet
    ↓
Other Networks
    ↓
Destination
```

---

# Internet Speed

# 18. What Does Internet Speed Mean?

The lecture asks:

> If someone says their Internet speed is `1 Mbps`, what does that mean?

A common mistake is to interpret:

```text
Mbps
```

as:

```text
Megabytes per second
```

That is incorrect.

---

# 19. Bit

A **bit** is a binary digit.

It can have:

```text
0
```

or:

```text
1
```

So:

```text
1 bit = 0 or 1
```

---

# 20. Mbps

Mbps means:

```text
Megabits per second
```

not:

```text
Megabytes per second
```

Break it down:

```text
M
↓
Mega

bit
↓
bit

s
↓
second
```

Therefore:

```text
Mbps
=
Megabits per second
```

---

## What Does 1 Mbps Mean?

Using the decimal networking convention:

```text
1 Mbps
=
1,000,000 bits/second
```

So a 1 Mbps connection can theoretically transfer approximately:

```text
1,000,000 bits
```

per second at the stated link rate.

---

# 21. Gbps

Gbps means:

```text
Gigabits per second
```

Using decimal SI prefixes:

```text
1 Gbps
=
1,000,000,000 bits/second
```

or:

```text
10^9 bits/second
```

---

# 22. Kbps

Kbps means:

```text
Kilobits per second
```

Using decimal networking units:

```text
1 Kbps
=
1,000 bits/second
```

---

# 23. Bits vs Bytes

This distinction is extremely important.

```text
bit
```

is represented by:

```text
b
```

while:

```text
byte
```

is represented by:

```text
B
```

Therefore:

```text
Mb
```

means:

```text
Megabits
```

while:

```text
MB
```

means:

```text
Megabytes
```

---

## 1 Byte = 8 Bits

Therefore:

```text
1 byte = 8 bits
```

So:

```text
8 Mbps
```

is approximately:

```text
1 MB/s
```

before accounting for protocol overhead and other real-world effects.

---

# 24. Upload Speed

The lecture defines uploading conceptually as:

> "you are sending data from one computer to another computer that is known as upload"

So:

```text
Your Computer
      |
      | Data
      ↓
Internet
      ↓
Server
```

is uploading.

---

## Examples

Uploading:

```text
Photo → Instagram
Video → YouTube
File → Google Drive
Code → GitHub
```

All involve sending data from your device toward another system.

---

# 25. Download Speed

The lecture describes downloading as receiving data.

```text
Server
   |
   | Data
   ↓
Internet
   |
   ↓
Your Computer
```

Examples:

```text
Downloading a movie
Downloading a PDF
Loading a webpage
Downloading a software package
Receiving a file
```

---

# 26. How to Test Internet Speed

The instructor suggests using an online speed test.

A speed test generally measures things such as:

```text
Download speed
Upload speed
Latency
```

Common speed-test services include:

```text
Speedtest
Fast.com
```

The exact results can vary based on:

- Server selected
- Network congestion
- Wi-Fi signal
- ISP routing
- Device performance
- Time of day
- Other network activity

---

# 27. Deep Why Questions — Internet Speed

## Q1. Why is Internet speed measured in bits?

Network transmission rates are conventionally specified in bits per second.

Therefore:

```text
Mbps
Gbps
Kbps
```

refer to bit rates.

---

## Q2. Why does my 100 Mbps Internet not download files at 100 MB/s?

Because:

```text
Mbps ≠ MB/s
```

A 100 Mbps connection corresponds theoretically to:

```text
100 / 8
=
12.5 MB/s
```

before overhead and other practical limitations.

---

## Q3. Why can actual speed be lower than the advertised speed?

Because real-world throughput can be affected by:

```text
Protocol overhead
Wi-Fi interference
Network congestion
Server limitations
Routing
Device limitations
Signal quality
```

---

## Q4. Is Mbps the same as MBps?

No.

```text
Mbps
↓
Megabits per second
```

while:

```text
MBps
↓
Megabytes per second
```

Since:

```text
1 Byte = 8 bits
```

they differ by a factor of approximately 8.

---

# Communication Between Computers

# 28. How Do Two Computers Communicate?

The lecture introduces two broad ways communication can occur:

```text
Guided
```

and:

```text
Unguided
```

---

# 29. Guided Communication

The instructor defines guided communication conceptually as communication where:

> "there's a set of path already defined"

For example:

```text
Computer A
     |
     | Physical wire
     |
Computer B
```

The physical medium guides the signal along a defined path.

---

# 30. Unguided Communication

Unguided communication occurs without a physical wire providing a single fixed path.

Examples mentioned in the lecture:

```text
Wi-Fi
Bluetooth
Wireless communication
```

Conceptually:

```text
Device A
   ))) ))))
      Wireless
   (((( (((
Device B
```

The signal travels through the wireless medium rather than a physical cable between the two endpoints.

---

# 31. Guided vs Unguided

| Feature         | Guided                  | Unguided                              |
| --------------- | ----------------------- | ------------------------------------- |
| Physical medium | Yes                     | No physical cable between endpoints   |
| Path            | Guided by medium        | Wireless propagation                  |
| Examples        | Fiber, coaxial cable    | Wi-Fi, Bluetooth, cellular            |
| Communication   | Through physical medium | Through electromagnetic/radio signals |

---

# 32. Examples of Guided Communication

The lecture mentions physical communication media such as:

### Optical Fiber

```text
Fiber Cable
```

Uses light to transmit information.

---

### Coaxial Cable

```text
Coaxial Cable
```

Uses electrical signaling through a specialized cable structure.

---

### Submarine Fiber Cables

Long fiber-optic cables laid across the ocean floor connect countries and regions.

---

# 33. Examples of Unguided Communication

The lecture mentions:

```text
Bluetooth
Wi-Fi
3G
4G
LTE
5G
```

These use wireless communication.

---

# Chapter 5 — Submarine Cables

# 34. How Are Countries Connected?

A common misconception is:

> "The Internet is somewhere in the cloud."

The physical infrastructure is much more concrete.

Countries and continents are connected through a combination of:

```text
Fiber-optic cables
Submarine cables
Terrestrial networks
Wireless links
Satellites
Data centers
Routers
```

One particularly important component is **submarine fiber-optic cables**.

---

# 35. Submarine Cables

The lecture refers to submarine cable maps and mentions:

```text
submarine cable.com
```

as a place where submarine cable information can be explored.

The key idea is:

```text
Country A
    |
    |
Submarine Fiber Cable
    |
    |
Country B
```

These cables physically run through the oceans.

---

# 36. Optical Fibre Cables

Optical fiber uses light to carry information.

Conceptually:

```text
Digital Data
     ↓
Electrical/optical conversion
     ↓
Light pulses
     ↓
Fiber
     ↓
Light detection
     ↓
Digital Data
```

A fiber-optic cable can carry huge amounts of data over long distances.

---

# 37. India and International Cable Connections

The lecture gives examples of international connections involving India.

It mentions locations such as:

```text
Chennai
Kochi/Cochin
Mumbai
Sri Lanka
Dubai
Oman
UAE
Singapore
Malaysia
```

The exact cable routes depend on the particular submarine cable system.

The important concept is:

```text
India
 |
 +── Sri Lanka
 |
 +── Middle East
 |
 +── Southeast Asia
 |
 +── Other international networks
```

These connections allow Indian networks to communicate with networks in other countries.

---

# 38. Long-Distance Submarine Cables

The lecture mentions a cable of approximately:

```text
28,000 km
```

and describes it as passing through locations including:

```text
Japan
South Korea
China
Malaysia
India
UAE
Israel
Italy
UK
```

The purpose of this example is to demonstrate the enormous physical scale of Internet infrastructure.

One cable system can span multiple countries and continents.

---

# 39. Who Operates the Infrastructure?

The lecture explains the infrastructure at a high level:

```text
Large infrastructure operators
        ↓
Regional/smaller entities
        ↓
Internet Service Providers
        ↓
Consumers
```

The instructor makes a tentative statement about which entity controls certain infrastructure in India.

Because the transcript itself says:

> "I believe... I could be wrong"

that specific ownership claim should be treated as **unverified lecture commentary**, not as a fact.

The important concept is that Internet connectivity involves multiple layers of organizations and infrastructure operators.

---

# 40. Are Internet Cables Really Under the Ocean?

Yes.

Submarine communication cables physically run across the seabed.

Conceptually:

```text
                 Ocean
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

        Ship
         |
         |
         |
------------------------------  ← Sea surface

          \
           \
            \
             =================
             Submarine Cable
             =================
                    |
                    |
                 Ocean Floor
```

These cables carry enormous amounts of international Internet traffic.

---

# 41. Why Don't Sharks/Fish Destroy the Cables?

The lecture addresses a common question:

> "Don't sharks or fish cut these cables?"

The lecture explains that submarine cables are protected and, in many places, buried beneath the seabed.

The exact protection varies by cable location and design.

Near shore, cables are often buried or otherwise protected because human activities such as anchors and fishing can pose significant risks.

---

# 42. Other Physical Communication Media

The lecture mentions:

```text
Optical Fiber
Coaxial Cable
```

as examples of physical communication media.

---

## Optical Fiber

Uses light.

Advantages include:

- Very high capacity
- Long-distance transmission
- Low signal attenuation compared with many electrical media

---

## Coaxial Cable

Uses electrical signaling through a shielded cable structure.

It has historically been widely used for:

```text
Cable television
Internet access
Other communications
```

---

# Wireless Communication

# 43. Wireless Communication

Wireless communication does not require a physical cable directly connecting the communicating devices.

Instead, it commonly uses electromagnetic/radio signals.

Examples:

```text
Bluetooth
Wi-Fi
Cellular networks
```

---

# 44. Bluetooth

Bluetooth is designed primarily for relatively short-range wireless communication.

Examples:

```text
Phone ↔ Earbuds
Phone ↔ Laptop
Laptop ↔ Keyboard
Laptop ↔ Mouse
```

Conceptually:

```text
Phone
  ))) ))))
        Bluetooth
  (((( ((((
Earbuds
```

---

# 45. Wi-Fi

Wi-Fi provides wireless local-area networking.

Typical example:

```text
Laptop
   )))
   )))
Wi-Fi Router
   |
   |
Internet
```

The laptop communicates wirelessly with the router.

The router can then connect the local network to the wider Internet.

---

# 46. Cellular Networks — 3G, 4G, LTE and 5G

The lecture mentions:

```text
3G
4G
LTE
5G
```

These are cellular communication technologies/generations or standards.

They allow devices to communicate over cellular networks over much larger geographic areas than typical Bluetooth or Wi-Fi links.

Conceptually:

```text
Phone
  )))
  )))
Cell Tower
    |
    ↓
Mobile Network
    |
    ↓
Internet
```

---

# 47. Why Not Use Satellites for Everything?

The lecture asks:

> "Why can't we just use satellites?"

The key answer given is:

> "it's faster than satellite"

for many high-capacity terrestrial/submarine network paths.

---

## Why Fiber Can Be Preferable

For many fixed long-distance routes, submarine fiber provides:

- Very high capacity
- Low latency
- Efficient transmission
- Direct physical routes between network hubs

Satellites can be extremely useful for:

```text
Remote regions
Ships
Aircraft
Specialized communications
Areas without terrestrial infrastructure
```

But they are not a replacement for the global fiber infrastructure.

---

# Complete Mental Model

Let's combine everything learned so far.

Suppose you open:

```text
https://google.com
```

on your laptop.

---

## Step 1 — Your Device

Your laptop is connected to:

```text
Wi-Fi
```

Your router gives the laptop a local IP through DHCP.

Example:

```text
Laptop
192.168.1.10
```

---

## Step 2 — Domain Name

You enter:

```text
google.com
```

The domain is resolved to an appropriate IP address through DNS.

```text
google.com
     ↓
DNS
     ↓
IP address(es)
```

---

## Step 3 — Port

The communication uses an application/service endpoint.

For HTTPS, the well-known server port is commonly:

```text
443
```

---

## Step 4 — Data

The request consists of digital data.

The data is transmitted through network protocols and packetized for transmission.

```text
Request
   ↓
Packets
   ↓
Network
```

---

## Step 5 — Router

Your home router forwards the traffic toward the Internet.

NAT may translate the private/local connection to the public Internet-facing address.

```text
Laptop
192.168.1.10
      |
      ↓
Router
      |
      ↓
NAT
      |
      ↓
Public IP
```

---

## Step 6 — ISP

Your ISP provides connectivity from your local network toward the broader Internet.

```text
Home
 ↓
Router
 ↓
ISP
 ↓
Internet
```

---

## Step 7 — Physical Infrastructure

The traffic can travel across:

```text
Fiber
 ↓
Routers
 ↓
Submarine cables
 ↓
International networks
 ↓
Data centers
 ↓
Destination network
```

---

## Step 8 — Server

The request eventually reaches the appropriate server/service.

```text
Internet
   ↓
Google infrastructure
   ↓
Server
```

The server generates a response.

---

## Step 9 — Response

The response travels back:

```text
Server
   ↓
Internet
   ↓
ISP
   ↓
Router
   ↓
NAT
   ↓
Laptop
   ↓
Browser
```

---

# The Big Picture

The Internet is not simply:

```text
Laptop
   ↓
Cloud
   ↓
Google
```

A better mental model is:

```text
                    INTERNET

Laptop
  |
  ↓
Wi-Fi
  |
  ↓
Home Router
  |
  ↓
NAT
  |
  ↓
ISP
  |
  ↓
Regional Networks
  |
  ↓
Routers
  |
  ↓
Submarine Fiber
  |
  ↓
International Network
  |
  ↓
Data Center
  |
  ↓
Server
```

And the response follows the reverse/general return path.

---

# Hands-On Experience

The best way to understand these concepts is to verify them on your own Linux machine.

---

## Experiment 1 — Find Your IP Addresses

Run:

```bash
ip addr
```

Look for:

```text
inet 192.168.x.x
```

or another private address.

You can also run:

```bash
hostname -I
```

---

## Experiment 2 — Find Your Default Gateway

Run:

```bash
ip route
```

Look for:

```text
default via ...
```

For example:

```text
default via 192.168.1.1 dev wlan0
```

This usually represents your default gateway/router.

---

## Experiment 3 — Find Your Public IP

Run:

```bash
curl ifconfig.me
```

or:

```bash
curl https://api.ipify.org
```

Compare this with your local address.

You may observe:

```text
Local:
192.168.1.10

Public:
<public address>
```

This demonstrates the difference between local and public addressing.

---

# Experiment 4 — Check DNS

Run:

```bash
nslookup google.com
```

or:

```bash
dig google.com
```

You can observe the IP address(es) returned for the domain.

---

# Experiment 5 — Check Your Ports

Run:

```bash
ss -tuln
```

You may see services listening on ports such as:

```text
3000
5000
5432
27017
```

depending on what is installed/running on your system.

---

# Experiment 6 — Start a Server

Create a simple Python server:

```bash
python3 -m http.server 8000
```

Now your computer is serving files on:

```text
localhost:8000
```

Open:

```text
http://localhost:8000
```

in your browser.

You now have:

```text
Browser
   |
   | HTTP request
   ↓
localhost:8000
   |
   ↓
Python HTTP Server
   |
   | HTTP response
   ↓
Browser
```

---

# Experiment 7 — Observe Port 8000

While the Python server is running:

```bash
ss -tuln | grep 8000
```

You should see a listening socket associated with port `8000`.

This demonstrates that:

```text
localhost
```

identifies your machine while:

```text
8000
```

identifies the server endpoint.

---

# Experiment 8 — Use curl as the Client

With the server running:

```bash
curl http://localhost:8000
```

Here:

```text
curl
 ↓
Client
```

and:

```text
Python HTTP server
 ↓
Server
```

You are directly observing the client-server model on your own computer.

---

# Experiment 9 — Check Internet Connectivity

Run:

```bash
ping google.com
```

This can help you observe whether your machine can reach the destination using ICMP echo mechanisms.

You can also use:

```bash
curl -I https://google.com
```

to inspect HTTP response headers.

---

# Experiment 10 — Trace the Network Path

On Linux, you can use:

```bash
traceroute google.com
```

If it isn't installed:

```bash
sudo apt install traceroute
```

You can also try:

```bash
tracepath google.com
```

This helps visualize that communication can pass through multiple network hops.

Conceptually:

```text
Your Computer
     ↓
Router
     ↓
ISP
     ↓
Router
     ↓
Router
     ↓
Destination Network
```

---

# Experiment 11 — Observe Internet Speed

Use a speed-test website such as:

```text
Speedtest
```

or:

```text
Fast.com
```

Observe:

```text
Download
Upload
Latency
```

Then compare the values with your ISP's advertised plan.

---

# Experiment 12 — Understand Bits vs Bytes Yourself

Suppose your Internet speed is:

```text
100 Mbps
```

Convert it approximately to MB/s:

```text
100 / 8
=
12.5 MB/s
```

So:

```text
100 Mbps
≈
12.5 MB/s
```

before overhead and other practical limitations.

Try calculating:

```text
50 Mbps
100 Mbps
200 Mbps
500 Mbps
1 Gbps
```

using:

```text
MB/s ≈ Mbps / 8
```

---

# Deep Why Questions

## 1. Why do we need ports if we already have IP addresses?

Because IP addresses identify network endpoints/devices, while ports distinguish application/service endpoints.

```text
IP
 ↓
Which machine?

Port
 ↓
Which service?
```

---

## 2. Why are port numbers only 16 bits?

A 16-bit field provides:

```text
2^16 = 65,536
```

possible values.

This provides a standardized numerical namespace for transport-layer ports.

---

## 3. Why does HTTP have a standard port?

Standard ports allow clients and servers to use well-known conventions.

For example:

```text
HTTP  → 80
HTTPS → 443
```

---

## 4. Why does MongoDB use a different port?

Because MongoDB is a different service.

For example:

```text
Web application → 3000
MongoDB → 27017
```

The operating system can distinguish their network endpoints.

---

## 5. Why is `localhost:3000` different from `localhost:5000`?

Same host:

```text
localhost
```

Different port:

```text
3000
5000
```

Therefore they can represent different services.

---

## 6. Why is Internet speed measured in Mbps?

Because network transmission rates are conventionally expressed as bits per second.

```text
Mbps
=
Megabits per second
```

---

## 7. Why is 100 Mbps not 100 MB/s?

Because:

```text
1 Byte = 8 bits
```

Therefore:

```text
100 Mbps ÷ 8
=
12.5 MB/s
```

approximately.

---

## 8. Why do we need submarine cables?

Because high-capacity international Internet traffic needs physical communication infrastructure.

Submarine fiber provides high-capacity connections between continents and countries.

---

## 9. Why don't we use only Wi-Fi for international communication?

Wi-Fi is primarily a local wireless networking technology.

International communication requires large-scale backbone infrastructure.

A simplified path might be:

```text
Wi-Fi
 ↓
Home Router
 ↓
ISP
 ↓
Fiber Backbone
 ↓
Submarine Cable
 ↓
International Network
```

---

## 10. Why don't we use satellites for everything?

Satellites are useful in many scenarios, but fiber-optic networks are often preferred for high-capacity fixed routes because they can provide very high capacity and low latency.

---

## 11. Why are submarine cables buried?

Protection.

Potential hazards include:

```text
Anchors
Fishing activity
Underwater geological hazards
Other physical damage
```

Burial/protection is especially important in vulnerable areas.

---

## 12. Why does the Internet use both wired and wireless communication?

Because different environments require different technologies.

### Wired

Useful for:

```text
High capacity
Long-distance backbone
Stable connections
Data centers
Submarine links
```

### Wireless

Useful for:

```text
Mobility
Phones
Wi-Fi
Bluetooth
Remote access
```

---

# Interview Questions

## Basic

### Q1. What is a port?

A port is a logical network endpoint identifier used to distinguish services/applications on a device.

---

### Q2. How many port numbers are possible?

Port numbers use 16 bits:

```text
2^16 = 65,536
```

Possible numerical values:

```text
0–65535
```

---

### Q3. What is the difference between an IP address and a port?

```text
IP Address
→ Identifies the network endpoint/device.

Port
→ Identifies the service/application endpoint.
```

---

### Q4. What is the default HTTP port?

```text
80
```

---

### Q5. What is the default HTTPS port?

```text
443
```

---

### Q6. What is the commonly used MongoDB port?

```text
27017
```

---

### Q7. What is the common SQL Server port?

```text
1433
```

---

### Q8. What is an ISP?

ISP stands for:

```text
Internet Service Provider
```

It provides Internet connectivity to customers.

---

### Q9. What does Mbps mean?

```text
Megabits per second
```

---

### Q10. What is 1 Mbps?

Using decimal units:

```text
1 Mbps
=
1,000,000 bits/second
```

---

### Q11. What is 1 Gbps?

```text
1 Gbps
=
1,000,000,000 bits/second
```

---

### Q12. What is uploading?

Sending data from your device toward another system.

```text
Your Computer
     ↓
   Server
```

---

### Q13. What is downloading?

Receiving data from another system.

```text
Server
  ↓
Your Computer
```

---

### Q14. What is guided communication?

Communication through a physical medium that guides the signal.

Examples:

```text
Fiber
Coaxial cable
```

---

### Q15. What is unguided communication?

Wireless communication without a physical cable directly guiding the signal between endpoints.

Examples:

```text
Wi-Fi
Bluetooth
Cellular
```

---

### Q16. What is a submarine cable?

A communication cable laid underwater, typically along the seabed, used to connect distant geographic regions and countries.

---

### Q17. What technology is commonly used in modern submarine cables?

Fiber-optic technology.

---

### Q18. Why are submarine cables important?

They provide high-capacity international connectivity between countries and continents.

---

### Q19. What is the OSI model?

A layered conceptual model used to organize and understand network communication functions.

The lecture will cover its layers in detail later.

---

# Quick Revision Sheet

## Port

```text
Logical network endpoint
```

## Port Size

```text
16 bits
```

## Total Port Values

```text
2^16 = 65,536
```

## Port Range

```text
0–65535
```

## HTTP

```text
Port 80
```

## HTTPS

```text
Port 443
```

## MongoDB

```text
Common default port: 27017
```

## SQL Server

```text
Common default port: 1433
```

## IP

```text
Identifies a network endpoint
```

## Port

```text
Identifies a service/application endpoint
```

## ISP

```text
Internet Service Provider
```

## Mbps

```text
Megabits per second
```

## Gbps

```text
Gigabits per second
```

## Kbps

```text
Kilobits per second
```

## Bit

```text
0 or 1
```

## Byte

```text
8 bits
```

## Upload

```text
Your device → Network/Server
```

## Download

```text
Network/Server → Your device
```

## Guided

```text
Physical medium
```

Examples:

```text
Fiber
Coaxial cable
```

## Unguided

```text
Wireless medium
```

Examples:

```text
Bluetooth
Wi-Fi
3G
4G
LTE
5G
```

## Submarine Cable

```text
Underwater fiber-optic communication infrastructure
```

---

# Final Mental Model

Keep this entire chapter in your head as one connected story:

```text
                         INTERNET
                            |
                            |
                         ISP
                            |
                            |
                    ┌───────┴───────┐
                    │               │
               Wired Network    Wireless Network
                    │               │
                 Fiber            Wi-Fi
                    │               │
                    └───────┬───────┘
                            |
                        Router
                            |
                           NAT
                            |
                     Public IP
                            |
                     Global Network
                            |
                 ┌──────────┴──────────┐
                 │                     │
        Terrestrial Fiber       Submarine Fiber
                 │                     │
                 └──────────┬──────────┘
                            |
                       Destination
                            |
                         Server
```

At the device level:

```text
IP Address
    ↓
Which network endpoint?
    ↓
Port Number
    ↓
Which service?
    ↓
Protocol
    ↓
How should communication happen?
    ↓
Packets
    ↓
How is the data transported?
```

At the physical level:

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
    ↓
Fiber / Cable / Radio
```

This leads directly into the next major topic:

# OSI Model

The OSI model will explain how all these seemingly separate concepts fit together into a layered networking system.

---

# One-Minute Revision

If you remember only this, remember:

```text
PORT
16 bits
0–65535

IP
→ Which network endpoint?

PORT
→ Which service?

HTTP
→ Web communication

ISP
→ Provides Internet connectivity

Mbps
→ Megabits per second

UPLOAD
→ Send data

DOWNLOAD
→ Receive data

GUIDED
→ Physical medium

UNGUIDED
→ Wireless medium

SUBMARINE CABLE
→ Physical fiber infrastructure connecting distant regions

OSI MODEL
→ Explains networking through layers
```

The most important mental transition is:

```text
"The Internet is in the cloud"
              ❌

"The Internet is a huge physical + logical
network made of cables, fiber, radio,
routers, ISPs, data centers and protocols."
              ✅
```
