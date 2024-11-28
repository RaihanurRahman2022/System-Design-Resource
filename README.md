# System-Design-Resource
Collect System Design Resources

# Table of contents

- **Getting Started**
  - [What is system design?](#what-is-system-design)
 
- **Basic**
  - [IP](https://github.com/RaihanurRahman2022/system-design/tree/main?tab=readme-ov-file#ip)
      - [Public IP Address](#public-ip-address)
      - [Private IP Address](#private-ip-address)
      - [Dynamic IP Address](#dynamic-ip-address)
      - [Static IP Address](#static-ip-address)
  - [OSI Model](#osi-model)
  - [TCP and UDP](#tcp-and-udp)
  - [HTTP and HTTPS](#http-and-https)
  - [Scalability](#scalability)
  - [Performance vs scalability](#performance-vs-scalability)
  - [Latency vs throughput](#latency-vs-throughput)
  - [Availability vs consistency](#availability-vs-consistency)
      - [CAP Theorem](#cap-theorem)
          - [CP - consistency and partition tolerance](#cp---consistency-and-partition-tolerance)
          - [AP - availability and partition tolerance](#ap---availability-and-partition-tolerance)  






# What is system design?
System design is the process of defining the elements of a system, as well as their interactions and relationships, in order to satisfy a set of specified requirements.
  - It involves taking a problem statement, breaking it down into smaller components and designing each component to work together effectively to achieve the overall goal of the system.
  - This process typically includes analyzing the current system (if any) and determining any deficiencies, creating a detailed plan for the new system, and testing the design to ensure
    that it meets the requirements.
  - It is an iterative process that may involve multiple rounds of design, testing, and refinement.

# Public IP Address
  A Public IP Address is an IP address that is accessible over the internet. This is the address assigned to your router (or a public-facing server), and it’s how devices outside your local network can         
  communicate with your network.Public IP addresses are assigned by your Internet Service Provider (ISP). They are unique across the entire internet.
  
  Example:
  - A website like www.example.com has a public IP address like `93.184.216.34`, which is accessible to anyone across the world.
  
  Characteristics:
  - Public IPs are visible on the internet and can be reached from anywhere (unless blocked by firewalls or other security measures).
  - Every device connected to the internet has a public IP (often shared by many devices through a router using Network Address Translation or NAT).

# Private IP Address
  A Private IP Address is used inside private networks (like home, office, or school networks). These addresses are not accessible from the internet and are reserved for use within local networks. 
  
  Private IP Address Ranges:
  - Class A: `10.0.0.0` to `10.255.255.255`
  - Class B: `172.16.0.0` to `172.31.255.255`
  - Class C: `192.168.0.0` to `192.168.255.255`
    
  Example:
  - `192.168.1.1`: Commonly used as the default IP address for home routers.
  - `10.0.0.1`: Often used by larger networks (e.g., office networks).
    
  Characteristics:
  - Private IP addresses cannot be routed on the public internet.
  - Routers use Network Address Translation (NAT) to map private IP addresses to a public IP address when accessing the internet.
    
# Dynamic IP Address
  A Dynamic IP Address is an IP address that is assigned to a device for a limited time by a [Dynamic Host Configuration Protocol (DHCP)](https://www.geeksforgeeks.org/dynamic-host-configuration-protocol-dhcp/) 
  server, such as your router or ISP. These IP addresses can change over time.

  Example:
  - Your laptop or smartphone might get a dynamic IP like `192.168.1.100` when it connects to your home Wi-Fi, but the next time it connects, it may get `192.168.1.102`.
  
  Characteristics:
  - Dynamic IPs are temporary and can change each time the device connects to the network.
  - The DHCP server automatically assigns and manages dynamic IP addresses for devices.
    
# Static IP Address
  A Static IP Address is an IP address that is manually assigned to a device and does not change over time. These are typically used for devices that need a consistent, unchanging address (e.g., web servers, 
  email servers).

  Example:
  - If you're hosting a website, your server might have a static IP like `203.0.113.5`, which remains the same every time someone accesses it.
    
  Characteristics:
  - Static IPs are fixed and remain the same over time, making them suitable for services that require constant access.
  - They are more expensive and typically require manual configuration.
    
# OSI Model
  The Open System Interconnection (OSI) model has defined the common terminology used in networking discussions and documentation. This allows us to take a very complex communications process apart and evaluate     its components.

  While this model is not directly implemented in the TCP/IP networks that are most common today, it can still help us do so much more, such as:
  
  - Make troubleshooting easier and help identify threats across the entire stack.
  - Encourage hardware manufacturers to create networking products that can communicate with each other over the network.
  - Essential for developing a security-first mindset.
  - Separate a complex function into simpler components.
### Resources On OSI Model
  - [OSI MODEL: কেন এবং কীভাবে?](https://www.linkedin.com/pulse/osi-model-%E0%A6%95%E0%A6%A8-%E0%A6%8F%E0%A6%AC-%E0%A6%95%E0%A6%AD%E0%A6%AC-poridhiio/)
  - [OSI MODEL](https://github.com/RaihanurRahman2022/system-design/tree/main?tab=readme-ov-file#osi-model)

# TCP and UDP
  What is TCP?
  - TCP (Transmission Control Protocol) is a connection-oriented protocol.
  - It ensures reliable communication. Data is sent in the correct order, and if packets are lost, they are retransmitted.
  
  Example: Imagine you're sending a letter through the mail. TCP ensures that your letter will reach its destination without being lost, and if it’s delayed or damaged, it will be resent. It also ensures that 
  all the pages are in the right order.
  
  What is UDP?
  - UDP (User Datagram Protocol) is a connectionless protocol.
  - It's faster because it doesn't guarantee reliability or order. If some packets get lost, they aren't retransmitted.
  
  Example: Think of streaming a live video or playing an online game. If a few frames or packets are lost, it doesn't matter that much. You’re willing to accept some data loss for the sake of speed.
### How does whole communication work
 ```
  +-------------------------+          +----------------------+
  |  Web Browser (Client)    |         |   Web Server (Server)|
  |------------------------- |         |----------------------|
  | 1. Enter URL             |         |                      |
  |    (www.example.com)     |         |                      |
  | 2. Resolve DNS (to IP)   |         |                      |
  |    (e.g., 192.0.2.1)     |         |                      |
  | 3. Send HTTP Request     |         |                      |
  |    (GET /index.html HTTP)|         |                      |
  +-------------------------+          +----------------------+
                 |                                |
                 | Step 1: DNS Resolution         |
                 v                                |
     +------------------------+                   |
     |       DNS Server        |                  |
     | Resolves domain name to |                  |
     | IP address (e.g., 192.0.2.1)               |
     +------------------------+                   |
                 |                                |
     Step 2: TCP Connection Establishment         |
                 |                                |
                 v                                v
  +-------------------------+          +----------------------+
  |        Client (TCP)      |         |       Web Server     |
  |------------------------- |         |----------------------|
  | 4. Client opens a TCP    |         | 5. Server listens on |
  |    connection to server  |         |    TCP port 80       |
  |    (SYN, SYN-ACK, ACK)   |         |                      |
  |    to port 80 (HTTP)     |         |                      |
  +-------------------------+          +----------------------+
                 |                                |
                 | Step 3: Send HTTP Request      |
                 v                                v
  +-------------------------+          +----------------------+
  |        Client (TCP)     |          |     Web Server       |
  |-------------------------|          |----------------------|
  | 6. Client sends HTTP    |          | 7. Server receives   |
  |    Request over TCP     |          |    the HTTP request  |
  |    (GET /index.html)    |          |    over TCP          |
  +-------------------------+          +----------------------+
                 |                                |
                 | Step 4: Server Response      |
                 v                                v
  +-------------------------+          +----------------------+
  |        Client (TCP)     |          |     Web Server       |
  |-------------------------|          |----------------------|
  | 8. Client receives HTTP |          | 9. Server processes  |
  |    Response (HTML page) |          |    the HTTP request  |
  |    over TCP             |          |    and sends back a  |
  |                         |          |    response (200 OK) |
  +-------------------------+          +----------------------+
                 |                                |
                 | Step 5: Data Transfer         |
                 v                                v
  +-------------------------+          +----------------------+
  |        Client (TCP)     |          |     Web Server       |
  |-------------------------|          |----------------------|
  | 10. Client closes TCP   |          | 11. Server closes TCP|
  |     connection (FIN, ACK)|         |     connection (FIN) |
  +-------------------------+          +----------------------+
```
### Resources on TCP & UDP
  - [TCP & UDP](https://github.com/RaihanurRahman2022/system-design/tree/main?tab=readme-ov-file#tcp-and-udp)

# HTTP and HTTPS
  HTTP (HyperText Transfer Protocol) is the foundation of data communication on the World Wide Web. It's a protocol used by browsers (clients) to communicate with web servers. HTTPS (HyperText Transfer Protocol 
  Secure) is simply the secure version of HTTP, which means that the communication between the client and server is encrypted using SSL/TLS.
  
### HTTP (HyperText Transfer Protocol)
  - HTTP is an application-layer protocol in the OSI model.
  - It is a stateless protocol, meaning each request from a client to a server is treated as independent, with no memory of previous requests.
  - HTTP relies on TCP (Transmission Control Protocol) for data transfer, which ensures reliable communication.
    
### HTTPS (HyperText Transfer Protocol Secure)
  - HTTPS is essentially HTTP with an added layer of security.
  - HTTPS encrypts data using SSL/TLS (Secure Sockets Layer / Transport Layer Security), which ensures privacy and integrity by encrypting the data between the client and server.
  - It provides protection against man-in-the-middle attacks and ensures data integrity (i.e., the data sent has not been tampered with).

### HTTPS Connection Process (SSL/TLS Handshake)

![Ref-Image](https://media2.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fsl3p050n2cvojxzewqvr.jpg)
    
  - TLS Handshake: Before any data can be transferred securely over HTTPS, the client and server first perform a handshake to establish the encryption methods.

    Steps in the SSL/TLS Handshake:
    - Client Hello: The client sends a message to the server, initiating the handshake, listing the supported encryption algorithms, and other details.
    - Server Hello: The server responds with its own encryption method and sends its SSL certificate, which includes the server's public key.
    - Certificate Verification: The client verifies the server's certificate using trusted Certificate Authorities (CAs).
    - Session Key Generation: Both client and server generate a session key using a Diffie-Hellman key exchange or other methods.
    - Client Finished: The client sends a message encrypted with the session key to confirm that the handshake is complete.
    - Server Finished: The server responds with its own encrypted message, indicating the completion of the handshake.
      
  - Secure Data Transfer: After the handshake, the client and server can now securely send and receive data, all encrypted with the session key.
  
  - Session Termination: Once the session is finished, the connection is closed.

# Scalability
  
  Scalability refers to the ability of a system, application, or process to handle an increasing amount of work, or its potential to be enlarged to accommodate that growth. In computing and 
  software, scalability often refers to the system's ability to grow in capacity or performance when demand increases. A scalable system can efficiently manage an increase in workload or users without 
  significantly degrading performance.

  There are different techniques and strategies used to ensure that a system can efficiently handle increasing loads, users, or data volume without significant performance degradation.

### Resources on Scalability
  - [A word on scalability](https://www.allthingsdistributed.com/2006/03/a_word_on_scalability.html)
  - [Scalability for Dummies](https://web.archive.org/web/20221030091841/http://www.lecloud.net/tagged/scalability/chrono)

# Performance vs scalability
  A service is scalable if it results in increased performance in a manner proportional to resources added. Generally, increasing performance means serving more units of work, but it can also be to handle larger   units of work, such as when datasets grow.

  Another way to look at performance vs scalability:

  - If you have a performance problem, your system is slow for a single user.
  - If you have a scalability problem, your system is fast for a single user but slow under heavy load.

### Resources on Performance vs Scalability
  - [Performance vs Scalability](https://blog.professorbeekums.com/performance-vs-scalability/)
  - [Scalability, Availability & Stability Patterns](https://www.slideshare.net/slideshow/scalability-availability-stability-patterns/4062682)

# Latency vs throughput
  Latency and throughput are two important measures of a system’s performance. Latency refers to the amount of time it takes for a system to respond to a request. Throughput refers to the number of requests that   a system can handle at the same time.

  - Generally, you should aim for maximal throughput with acceptable latency.

### Resources on Latency vs throughput
  - [System Design: Latency vs Throughput](https://cs.fyi/guide/latency-vs-throughput)
  - [Understanding Latency versus Throughput](https://community.cadence.com/cadence_blogs_8/b/fv/posts/understanding-latency-vs-throughput)

# Availability vs consistency
  Availability refers to the ability of a system to provide its services to clients even in the presence of failures. This is often measured in terms of the percentage of time that the system is up and running,    also known as its uptime.

  Consistency, on the other hand, refers to the property that all clients see the same data at the same time. This is important for maintaining the integrity of the data stored in the system.

  In distributed systems, it is often a trade-off between availability and consistency. Systems that prioritize high availability may sacrifice consistency, while systems that prioritize consistency may 
  sacrifice availability. Different distributed systems use different approaches to balance the trade-off between availability and consistency, such as using replication or consensus algorithms.

## CAP Theorem
  The CAP Theorem, also known as Brewer's Theorem, is a concept from distributed systems that describes the trade-offs between three key properties in a distributed database or system. 

  According to CAP theorem, in a distributed system, you can only support two of the following guarantees:

  - Consistency - Every read receives the most recent write or an error
  - Availability - Every request receives a response, without guarantee that it contains the most recent version of the information
  - Partition Tolerance - The system continues to operate despite arbitrary partitioning due to network failures
  
  Networks aren’t reliable, so you’ll need to support partition tolerance. You’ll need to make a software tradeoff between consistency and availability.

### Resources on CAP Theorem
  - [CAP theorem revisited](https://robertgreiner.com/cap-theorem-revisited/)
  - [A plain english introduction to CAP theorem](http://ksat.me/a-plain-english-introduction-to-cap-theorem)
  - [CAP FAQ](https://github.com/henryr/cap-faq)
  - [The CAP theorem](https://www.youtube.com/watch?v=k-Yaq8AHlFA)
    
## CP - consistency and partition tolerance
  CP (Consistency + Partition Tolerance) system is one that prioritizes consistency and partition tolerance but sacrifices availability in certain situations. Waiting for a response from the partitioned node 
  might result in a timeout error. CP is a good choice if your business needs require atomic reads and writes.

### CP System:
  - Consistency (C): All nodes in the system have the same data at any given time, and any read operation will return the most recent write (i.e., the system ensures that the data is consistent across all nodes).
  
  - Partition Tolerance (P): The system can continue operating correctly even if a network partition occurs (i.e., if nodes can’t communicate with each other due to network failures or latency). Partition 
    tolerance is essential in distributed systems because network failures and partitions are inevitable in large-scale environments.

  - Availability (A) is sacrificed: If a partition occurs, the system may choose to not respond to some requests (either read or write) to maintain consistency. In other words, during network partitions, the 
    system may not be fully available to serve all requests.

## AP - availability and partition tolerance
   AP (Availability + Partition Tolerance) system prioritizes availability and partition tolerance, but sacrifices consistency in certain situations. Responses return the most readily available version of the 
   data available on any node, which might not be the latest. Writes might take some time to propagate when the partition is resolved.

   AP is a good choice if the business needs to allow for [eventual consistency](#eventual-consistency) or when the system needs to continue working despite external errors.

### AP System:
  - Availability (A): The system will always respond to requests, either with the requested data or an acknowledgment of the write operation. In an AP system, no request is left hanging, and the system is 
    designed to provide a response to all read and write requests, even if some of the data may be inconsistent across nodes.
  
  - Partition Tolerance (P): The system can continue to operate correctly even if a network partition occurs (i.e., if some nodes are unable to communicate with others due to network issues). The system can     
    handle network failures or delays without going down, maintaining functionality across all parts of the system.
  
  - Consistency (C) is sacrificed: In the event of a partition, different nodes might have inconsistent or outdated data. The system will respond to requests, but it may not guarantee that the data returned is 
    the most up-to-date version. This trade-off means that, during partitions, the system could return stale or conflicting data.
    
