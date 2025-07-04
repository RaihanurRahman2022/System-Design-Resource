# System-Design-Resource
Collect System Design Resources

# Table of contents

- **Getting Started**
  - [What is system design?](#what-is-system-design)
 
- **Chapter I**
  - [IP](https://github.com/RaihanurRahman2022/system-design/tree/main?tab=readme-ov-file#ip)
    - [Public IP Address](#public-ip-address)
    - [Private IP Address](#private-ip-address)
    - [Dynamic IP Address](#dynamic-ip-address)
    - [Static IP Address](#static-ip-address)
  - [OSI Model](#osi-model)
  - [TCP and UDP](#tcp-and-udp)
  - [HTTP and HTTPS](#http-and-https)
  - [Scalability](#scalability)
    - [Vertical scaling](#vertical-scaling)
    - [Horizontal scaling](#horizontal-scaling)
    - [Vertical scaling vs Horizontal scaling](#vertical-scaling-vs-horizontal-scaling)
  - [Performance vs scalability](#performance-vs-scalability)
  - [Latency vs throughput](#latency-vs-throughput)
  - [Availability vs consistency](#availability-vs-consistency)
    - [CAP Theorem](#cap-theorem)
      - [CP - consistency and partition tolerance](#cp---consistency-and-partition-tolerance)
      - [AP - availability and partition tolerance](#ap---availability-and-partition-tolerance)
  - [Consistency patterns](#consistency-patterns)
    - [Strong Consistency](#strong-consistency)
    - [Weak Consistency](#weak-consistency)
    - [Eventual Consistency](#eventual-consistency)
  - [Availability patterns](#availability-patterns)
    - [Fail-Over](#fail-over)
      - [Active-passive](#active-passive)
      - [Active-active](#active-active)
    - [Replication](#replication)
      - [Master-Master replication](#master-master-replication)
      - [Master-Slave replication](#master-slave-replication)
    - [Availability in Numbers](#availability-in-numbers)
    - [Availability vs Reliability](#availability-vs-reliability)
  - [Domain name system](#domain-name-system)
    - [How DNS Works](#how-dns-work)
    - [Server types](#server-types)
      - [DNS Resolver](#dns-resolver)
      - [DNS root server](#dns-root-server)
      - [TLD nameserver](#tld-nameserver)
      - [Authoritative DNS server](#authoritative-dns-server)
    - [Query Types](#query-types)
      - [Recursive](#recursive)
      - [Iterative](#iterative)
      - [Non-recursive](#non-recursive)
    - [Record Types](#record-types)
    - [Subdomains](#subdomains)
    - [DNS Zones](#dns-zones)
    - [DNS Caching](#dns-caching)
    - [Reverse DNS](#reverse-dns)
    - [Distributed DNS](#distributed-dns)
- [Load Balancing](#load-balancing)
 - [Workload distribution](#workload-distribution)
 - [Layers](#layers)
 - [Types](#types)
 - [Routing Algorithms](#routing-algorithms)
 - [Advantages](#advantages)   


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

# Vertical scaling
  Vertical scaling (also known as scaling up) refers to the process of adding more resources to a single server or machine in order to handle increased demand. This approach focuses on upgrading the 
  hardware of an existing server rather than adding more servers to a system.

  - Adding Resources: Involves increasing the capacity of a single server by adding more CPU power, RAM, storage, or network bandwidth to handle more traffic or computational load.
  - Simpler Architecture: Unlike horizontal scaling, vertical scaling keeps the architecture relatively simple, as it only involves one machine with upgraded resources.
  - No Need for Distributed Systems: Because you're working with a single server, vertical scaling does not require complex distributed systems or load balancing mechanisms.

### Example
  - A web application may start with a server that has 4 GB of RAM and a 2-core processor. As traffic grows, the server is upgraded to 16 GB of RAM and an 8-core processor to handle the increased number of   
  requests.
  - In the case of a database system, if a database server is struggling to keep up with the growing volume of queries, you can scale vertically by upgrading the hardware to provide more processing power and 
  memory for better query handling.

### Advantages

- Simple to implement
- Easier to manage
- Data consistent

### Disadvantages

- Risk of high downtime
- Harder to upgrade
- Can be a single point of failure


# Horizontal scaling
  Horizontal scaling (also known as scaling out) refers to adding more individual machines or servers to a system to distribute the workload across multiple resources, rather than upgrading a single machine (as    in vertical scaling). This approach is often used to handle larger volumes of traffic or data while maintaining system reliability and performance.

  - Adding More Servers: In horizontal scaling, you scale by increasing the number of computing nodes (servers, virtual machines, containers, etc.) in your infrastructure.
  - Distributed Workload: The workload is distributed across multiple servers, which can improve performance and reduce the risk of any single server becoming overwhelmed.
  - Increased Redundancy: Horizontal scaling increases the fault tolerance of the system because the failure of one server does not result in a complete failure of the system.

### Advantages

- Increased redundancy
- Better fault tolerance
- Flexible and efficient
- Easier to upgrade

### Disadvantages

- Increased complexity
- Data inconsistency
- Increased load on downstream services

# Vertical scaling vs Horizontal scaling
  Vertical scaling and horizontal scaling are two primary approaches to scaling systems in order to handle increased demand. Both strategies aim to improve the performance and capacity of a system, but they 
  differ in how they achieve that goal.

  | **Aspect**                 | **Vertical Scaling**                          | **Horizontal Scaling**                                    |
  |--------------------------- |---------------------------------------------- |---------------------------------------------------------- |
  | **Definition**             | Add more resources to a single server         | Add more servers to distribute the load                   |
  | **Scalability**            | Limited (single machine)                      | Virtually unlimited (add more servers)                    |
  | **Cost**                   | Can become expensive with high-end hardware   | Generally more cost-effective with cloud services         |
  | **Complexity**             | Simple to implement                           | Complex to manage and maintain                            |
  | **Fault Tolerance**        | Single point of failure                       | Higher availability and redundancy                        |
  | **Limits**                 | Limited by hardware                           | No hard limits, as long as infrastructure can accommodate |
  | **Performance**            | Improved performance for small to medium loads| Great for handling large-scale traffic and data           |
  | **Example Use Cases**      | Small-to-medium-sized applications, databases | Large-scale web apps, cloud-based services, big data      |
  
### Resources on Vertical scaling vs Horizontal scaling
  - [Vertical vs. horizontal scaling explained - Aerospike](https://aerospike.com/blog/vertical-vs-horizontal-scaling/#vertical_vs_horizontal_scaling)
  - [Horizontal Vs. Vertical Scaling: Which One Should You Choose?](https://www.finout.io/blog/horizontal-vs-vertical-scaling)

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
    
# Consistency patterns
  Consistency patterns refer to the ways in which data is stored and managed in a distributed system, and how that data is made available to users and applications. With multiple copies of the same data, we are 
  faced with options on how to synchronize them so clients have a consistent view of the data. Recall the definition of consistency from the CAP theorem - Every read receives the most recent write or an error. 
  There are three main types of consistency patterns:

  - Strong consistency
  - Weak consistency
  - Eventual Consistency
    
  Each of these patterns has its own advantages and disadvantages, and the choice of which pattern to use will depend on the specific requirements of the application or system.

## Strong Consistency
  After an update is made to the data, it will be immediately visible to any subsequent read operations. The data is replicated in a synchronous manner, ensuring that all copies of the data are updated at the 
  same time.

  - After a write, reads will see it. Data is replicated synchronously.
  - This approach is seen in file systems and RDBMSes. Strong consistency works well in systems that need transactions.
    
## Weak consistency
  After an update is made to the data, it is not guaranteed that any subsequent read operation will immediately reflect the changes made. The read may or may not see the recent write. 
  
  - After a write, reads may or may not see it. A best effort approach is taken.
  - This approach is seen in systems such as memcached. Weak consistency works well in real time use cases such as VoIP, video chat, and realtime multiplayer games. For example, if you are on a phone call and 
    lose reception for a few seconds, when you regain connection you do not hear what was spoken during connection loss.

## Eventual Consistency
  Eventual consistency is a form of Weak Consistency. After an update is made to the data, it will be eventually visible to any subsequent read operations. The data is replicated in an asynchronous manner, 
  ensuring that all copies of the data are eventually updated.

  - After a write, reads will eventually see it (typically within milliseconds). Data is replicated asynchronously.
  - This approach is seen in systems such as DNS and email. Eventual consistency works well in highly available systems.

### Resources on Consistency patterns
  - [Consistency Patterns in Distributed Systems](https://cs.fyi/guide/consistency-patterns-week-strong-eventual)
  - [Transactions across data centers](https://snarfed.org/s/transactions_across_datacenters_io.html)

# Availability patterns
  Availability is measured as a percentage of uptime, and defines the proportion of time that a system is functional and working. Availability is affected by system errors, infrastructure problems, malicious 
  attacks, and system load. Cloud applications typically provide users with a service level agreement (SLA), which means that applications must be designed and implemented to maximize availability.

## Fail-Over

  Failover is an availability pattern that is used to ensure that a system can continue to function in the event of a failure. It involves having a backup component or system that can take over in the event of a 
  failure.

  In a failover system, there is a primary component that is responsible for handling requests, and a secondary (or backup) component that is on standby. The primary component is monitored for failures, and if     it fails, the secondary component is activated to take over its duties. This allows the system to continue functioning with minimal disruption.
  
  Failover can be implemented in various ways, such as active-passive, active-active, and hot-standby.
   
### Active-passive
  With active-passive fail-over, heartbeats are sent between the active and the passive server on standby. If the heartbeat is interrupted, the passive server takes over the active’s IP address and resumes 
  service.

  The length of downtime is determined by whether the passive server is already running in ‘hot’ standby or whether it needs to start up from ‘cold’ standby. Only the active server handles traffic.

   Active-passive failover can also be referred to as master-slave failover.

### Example Model

  An active-passive architectural pattern consists of at least two nodes. The passive server (failover) acts as a backup that remains on standby and takes over in the event the active server gets disconnected 
  for whatever reason. The primary active server hosts production, test and development applications.
  
  The secondary passive server essentially remains dormant during normal operation. A major disadvantage of this model is that there is no guarantee that the production application will function as expected on 
  the passive server. The model is also considered a relatively wasteful approach because expensive hardware is left unused. 

   ![Alt text](https://cdnblog.filecloud.com/blog/wp-content/uploads/2015/12/active_passive_high_availability_cluster1.png)

### Active-active
  In active-active, both servers are managing traffic, spreading the load between them.

  If the servers are public-facing, the DNS would need to know about the public IPs of both servers. If the servers are internal-facing, application logic would need to know about both servers.

  Active-active failover can also be referred to as master-master failover.

### Example Model

  The active-active model also contains at least two nodes; however, in this architectural pattern, multiple nodes are actively running the same services simultaneously. In order to fully utilize all the active 
  nodes, an active-active cluster uses load balancing to distribute workloads across the nodes in order to prevent any single node from being overloaded. The distributed workload subsequently leads to a marked 
  improvement in response times and throughput.
  
  The load balancers uses a set of complex algorithms to assign clients to the nodes, the connections are typically based on performance metrics and health checks. In order to guarantee seamless operability, all 
  the nodes in the cluster must be configured for redundancy. A potential drawback for an active-active redundancy is that in case one of the nodes fails, client sessions might be dropped, forcing them to re- 
  login into the system. However, this can easily be mitigated by ensuring that the individual configuration settings of each node are virtually identical.

  ![Alt text](https://cdnblog.filecloud.com/blog/wp-content/uploads/2015/12/active_active_high_availability_cluster_load_balancer1.png)
  
### Disadvantages of Failover
  - Fail-over adds more hardware and additional complexity.
  - There is a potential for loss of data if the active system fails before any newly written data can be replicated to the passive.

### Resources on Fail Over
  - [Fail Over Pattern - High Availability](https://www.filecloud.com/blog/2015/12/architectural-patterns-for-high-availability/)

# Replication
  Replication refers to the process of copying data from one server (the primary or master) to one or more other servers (the replicas or slaves) to ensure that the data is available across multiple locations. 
  In the context of availability patterns, replication plays a key role in improving system availability, fault tolerance, and reliability.

  Replication allows a system to handle failures and continue serving requests even when certain parts of the system are down. This is particularly relevant for distributed systems and databases where high 
  availability and disaster recovery are critical. In the event of a failure, the data can be retrieved from a different location. There are two main types of replication: 
  
  - Master-Master replication.
  - Master-Slave replication.

# Master-Master replication
  In this type of replication, multiple servers are configured as “masters,” and each one can accept read and write operations. This allows for high availability and allows any of the servers to take over if one 
  of them fails. However, this type of replication can lead to conflicts if multiple servers update the same data at the same time, so some conflict resolution mechanism is needed to handle this.


  <p align="center">
    <img src="images/krAHLGg.png">
    <br/>
    <i><a href=http://www.slideshare.net/jboner/scalability-availability-stability-patterns/>Source: Scalability, availability, stability, patterns</a></i>
  </p>

# Master-Slave replication
  In this type of replication, one server is designated as the “master” and handles all write operations, while multiple “slave” servers handle read operations. If the master fails, one of the slaves can be 
  promoted to take its place. This type of replication is simpler to set up and maintain compared to Master-Master replication.

  <p align="center">
    <img src="images/C9ioGtn.png">
    <br/>
    <i><a href=http://www.slideshare.net/jboner/scalability-availability-stability-patterns/>Source: Scalability, availability, stability, patterns</a></i>
  </p>

### Resources on Replication
  - [Database Replication](https://github.com/RaihanurRahman2022/system-design/blob/main/README.md#database-replication)
  - [Replication: Availability Pattern](https://github.com/donnemartin/system-design-primer#replication)
  
# Availability in Numbers
  Availability is often quantified by uptime (or downtime) as a percentage of time the service is available. Availability is generally measured in number of 9s—a service with 99.99% availability is described as 
  having four 9s.

## The Nine's of availability
  Availability is often quantified by uptime (or downtime) as a percentage of time the service is available. It is generally measured in the number of 9s.

  $$
  Availability = \frac{Uptime}{(Uptime + Downtime)}
  $$
  
  If availability is 99.00% available, it is said to have "2 nines" of availability, and if it is 99.9%, it is called "3 nines", and so on.

  | Availability (Percent)   | Downtime (Year)    | Downtime (Month)  | Downtime (Week)    |
  | ------------------------ | ------------------ | ----------------- | ------------------ |
  | 90% (one nine)           | 36.53 days         | 72 hours          | 16.8 hours         |
  | 99% (two nines)          | 3.65 days          | 7.20 hours        | 1.68 hours         |
  | 99.9% (three nines)      | 8.77 hours         | 43.8 minutes      | 10.1 minutes       |
  | 99.99% (four nines)      | 52.6 minutes       | 4.32 minutes      | 1.01 minutes       |
  | 99.999% (five nines)     | 5.25 minutes       | 25.9 seconds      | 6.05 seconds       |
  | 99.9999% (six nines)     | 31.56 seconds      | 2.59 seconds      | 604.8 milliseconds |
  | 99.99999% (seven nines)  | 3.15 seconds       | 263 milliseconds  | 60.5 milliseconds  |
  | 99.999999% (eight nines) | 315.6 milliseconds | 26.3 milliseconds | 6 milliseconds     |
  | 99.9999999% (nine nines) | 31.6 milliseconds  | 2.6 milliseconds  | 0.6 milliseconds   |

## Availability in parallel vs in sequence
  If a service consists of multiple components prone to failure, the service’s overall availability depends on whether the components are in sequence or in parallel.

### In sequence
  Overall availability decreases when two components with availability < 100% are in sequence:

  ```
  Availability (Total) = Availability (Foo) * Availability (Bar)
  ```
  
  If both Foo and Bar each had 99.9% availability, their total availability in sequence would be 99.8%.
  
### In parallel
  Overall availability increases when two components with availability < 100% are in parallel:
  ```
  Availability (Total) = 1 - (1 - Availability (Foo)) * (1 - Availability (Bar))
  ```
  If both Foo and Bar each had 99.9% availability, their total availability in parallel would be 99.9999%.
  
# Availability vs Reliability
  If a system is reliable, it is available. However, if it is available, it is not necessarily reliable. In other words, high reliability contributes to high availability, but it is possible to achieve high  
  availability even with an unreliable system.

## Domain name system

<p align="center">
  <img src="images/IOyLj4i.jpg">
  <br/>
  <i><a href=http://www.slideshare.net/srikrupa5/dns-security-presentation-issa>Source: DNS security presentation</a></i>
</p>

The Domain Name System (DNS) is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network.- Wikipedia.

Earlier, we learned about IP addresses that enable every machine to connect with other machines. But as we know humans are more comfortable with names than numbers. It's easier to remember a name like `google.com` than something like `122.250.192.232`.

This brings us to Domain Name System (DNS) which is a hierarchical and decentralized naming system used for translating human-readable domain names to IP addresses.

## How DNS works

![how-dns-works](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/domain-name-system/how-dns-works.png)

DNS lookup involves the following eight steps:

1. A client types [example.com](http://example.com) into a web browser, the query travels to the internet and is received by a DNS resolver.
2. The resolver then recursively queries a DNS root nameserver.
3. The root server responds to the resolver with the address of a Top-Level Domain (TLD).
4. The resolver then makes a request to the `.com` TLD.
5. The TLD server then responds with the IP address of the domain's nameserver, [example.com](http://example.com).
6. Lastly, the recursive resolver sends a query to the domain's nameserver.
7. The IP address for [example.com](http://example.com) is then returned to the resolver from the nameserver.
8. The DNS resolver then responds to the web browser with the IP address of the domain requested initially.

Once the IP address has been resolved, the client should be able to request content from the resolved IP address. For example, the resolved IP may return a webpage to be rendered in the browser.

## Server types

Now, let's look at the four key groups of servers that make up the DNS infrastructure.

### DNS Resolver

A DNS resolver (also known as a DNS recursive resolver) is the first stop in a DNS query. The recursive resolver acts as a middleman between a client and a DNS nameserver. After receiving a DNS query from a web client, a recursive resolver will either respond with cached data, or send a request to a root nameserver, followed by another request to a TLD nameserver, and then one last request to an authoritative nameserver. After receiving a response from the authoritative nameserver containing the requested IP address, the recursive resolver then sends a response to the client.

### DNS root server

A root server accepts a recursive resolver's query which includes a domain name, and the root nameserver responds by directing the recursive resolver to a TLD nameserver, based on the extension of that domain (`.com`, `.net`, `.org`, etc.). The root nameservers are overseen by a nonprofit called the [Internet Corporation for Assigned Names and Numbers (ICANN)](https://www.icann.org).

There are 13 DNS root nameservers known to every recursive resolver. Note that while there are 13 root nameservers, that doesn't mean that there are only 13 machines in the root nameserver system. There are 13 types of root nameservers, but there are multiple copies of each one all over the world, which use [Anycast routing](https://en.wikipedia.org/wiki/Anycast) to provide speedy responses.

### TLD nameserver

A TLD nameserver maintains information for all the domain names that share a common domain extension, such as `.com`, `.net`, or whatever comes after the last dot in a URL.

Management of TLD nameservers is handled by the [Internet Assigned Numbers Authority (IANA)](https://www.iana.org), which is a branch of [ICANN](https://www.icann.org). The IANA breaks up the TLD servers into two main groups:

- **Generic top-level domains**: These are domains like `.com`, `.org`, `.net`, `.edu`, and `.gov`.
- **Country code top-level domains**: These include any domains that are specific to a country or state. Examples include `.uk`, `.us`, `.ru`, and `.jp`.

### Authoritative DNS server

The authoritative nameserver is usually the resolver's last step in the journey for an IP address. The authoritative nameserver contains information specific to the domain name it serves (e.g. [google.com](http://google.com)) and it can provide a recursive resolver with the IP address of that server found in the DNS A record, or if the domain has a CNAME record (alias) it will provide the recursive resolver with an alias domain, at which point the recursive resolver will have to perform a whole new DNS lookup to procure a record from an authoritative nameserver (often an A record containing an IP address). If it cannot find the domain, returns the NXDOMAIN message.

## Query Types

There are three types of queries in a DNS system:

### Recursive

In a recursive query, a DNS client requires that a DNS server (typically a DNS recursive resolver) will respond to the client with either the requested resource record or an error message if the resolver can't find the record.

### Iterative

In an iterative query, a DNS client provides a hostname, and the DNS Resolver returns the best answer it can. If the DNS resolver has the relevant DNS records in its cache, it returns them. If not, it refers the DNS client to the Root Server or another Authoritative Name Server that is nearest to the required DNS zone. The DNS client must then repeat the query directly against the DNS server it was referred.

### Non-recursive

A non-recursive query is a query in which the DNS Resolver already knows the answer. It either immediately returns a DNS record because it already stores it in a local cache, or queries a DNS Name Server which is authoritative for the record, meaning it definitely holds the correct IP for that hostname. In both cases, there is no need for additional rounds of queries (like in recursive or iterative queries). Rather, a response is immediately returned to the client.

## Record Types

DNS records (aka zone files) are instructions that live in authoritative DNS servers and provide information about a domain including what IP address is associated with that domain and how to handle requests for that domain.

These records consist of a series of text files written in what is known as _DNS syntax_. DNS syntax is just a string of characters used as commands that tell the DNS server what to do. All DNS records also have a _"TTL"_, which stands for time-to-live, and indicates how often a DNS server will refresh that record.

There are more record types but for now, let's look at some of the most commonly used ones:

- **A (Address record)**: This is the record that holds the IP address of a domain.
- **AAAA (IP Version 6 Address record)**: The record that contains the IPv6 address for a domain (as opposed to A records, which stores the IPv4 address).
- **CNAME (Canonical Name record)**: Forwards one domain or subdomain to another domain, does NOT provide an IP address.
- **MX (Mail exchanger record)**: Directs mail to an email server.
- **TXT (Text Record)**: This record lets an admin store text notes in the record. These records are often used for email security.
- **NS (Name Server records)**: Stores the name server for a DNS entry.
- **SOA (Start of Authority)**: Stores admin information about a domain.
- **SRV (Service Location record)**: Specifies a port for specific services.
- **PTR (Reverse-lookup Pointer record)**: Provides a domain name in reverse lookups.
- **CERT (Certificate record)**: Stores public key certificates.

## Subdomains

A subdomain is an additional part of our main domain name. It is commonly used to logically separate a website into sections. We can create multiple subdomains or child domains on the main domain.

For example, `blog.example.com` where `blog` is the subdomain, `example` is the primary domain and `.com` is the top-level domain (TLD). Similar examples can be `support.example.com` or `careers.example.com`.

## DNS Zones

A DNS zone is a distinct part of the domain namespace which is delegated to a legal entity like a person, organization, or company, who is responsible for maintaining the DNS zone. A DNS zone is also an administrative function, allowing for granular control of DNS components, such as authoritative name servers.

## DNS Caching

A DNS cache (sometimes called a DNS resolver cache) is a temporary database, maintained by a computer's operating system, that contains records of all the recent visits and attempted visits to websites and other internet domains. In other words, a DNS cache is just a memory of recent DNS lookups that our computer can quickly refer to when it's trying to figure out how to load a website.

The Domain Name System implements a time-to-live (TTL) on every DNS record. TTL specifies the number of seconds the record can be cached by a DNS client or server. When the record is stored in a cache, whatever TTL value came with it gets stored as well. The server continues to update the TTL of the record stored in the cache, counting down every second. When it hits zero, the record is deleted or purged from the cache. At that point, if a query for that record is received, the DNS server has to start the resolution process.

## Reverse DNS

A reverse DNS lookup is a DNS query for the domain name associated with a given IP address. This accomplishes the opposite of the more commonly used forward DNS lookup, in which the DNS system is queried to return an IP address. The process of reverse resolving an IP address uses PTR records. If the server does not have a PTR record, it cannot resolve a reverse lookup.

Reverse lookups are commonly used by email servers. Email servers check and see if an email message came from a valid server before bringing it onto their network. Many email servers will reject messages from any server that does not support reverse lookups or from a server that is highly unlikely to be legitimate.

_Note: Reverse DNS lookups are not universally adopted as they are not critical to the normal function of the internet._

## Examples

These are some widely used managed DNS solutions:

- [Route53](https://aws.amazon.com/route53)
- [Cloudflare DNS](https://www.cloudflare.com/dns)
- [Google Cloud DNS](https://cloud.google.com/dns)
- [Azure DNS](https://azure.microsoft.com/en-in/services/dns)
- [NS1](https://ns1.com/products/managed-dns)

## Resource to learn more
- [DNS-A-Distributed-System](https://notes.kodekloud.com/docs/Demystifying-DNS/DNS-as-a-System/DNS-A-Distributed-System)
- [How DNS works](https://newsletter.systemdesign.one/p/what-is-a-dns-server-and-how-does-it-work)

## Distributed DNS
Distributed DNS (Domain Name System) refers to the decentralized architecture of the DNS system, which is used to translate human-readable domain names (like openai.com) into IP addresses (like `104.22.1.46` ) that computers use to communicate.

### Why is DNS Distributed?
If DNS were centralized, it would become:

- A single point of failure
- Slow for global users
- Difficult to scale with the growth of the internet

So instead, it's distributed across many servers and levels of hierarchy to ensure speed, reliability, and scalability.

## Detail Explaination
- [Distributed DNS](https://medium.com/@lazygeek78/system-design-of-dns-6a7532bdf0a0)
- [Alternet option if link is not available](https://github.com/RaihanurRahman2022/System-Design-Resource/blob/main/design-resource-pdf/distributed-dns.pdf)
  
# Load Balancing
Load balancing lets us distribute incoming network traffic across multiple resources ensuring high availability and reliability by sending requests only to resources that are online. This provides the flexibility to add or subtract resources as demand dictates.

![load-balancing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/load-balancer.png)

For additional scalability and redundancy, we can try to load balance at each layer of our system:

![load-balancing-layers](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/load-balancer-layers.png)

## But why?

Modern high-traffic websites must serve hundreds of thousands, if not millions, of concurrent requests from users or clients. To cost-effectively scale to meet these high volumes, modern computing best practice generally requires adding more servers.

A load balancer can sit in front of the servers and route client requests across all servers capable of fulfilling those requests in a manner that maximizes speed and capacity utilization. This ensures that no single server is overworked, which could degrade performance. If a single server goes down, the load balancer redirects traffic to the remaining online servers. When a new server is added to the server group, the load balancer automatically starts sending requests to it.

## Workload distribution

This is the core functionality provided by a load balancer and has several common variations:

- **Host-based**: Distributes requests based on the requested hostname.
- **Path-based**: Using the entire URL to distribute requests as opposed to just the hostname.
- **Content-based**: Inspects the message content of a request. This allows distribution based on content such as the value of a parameter.
## Layers

Generally speaking, load balancers operate at one of the two levels:

### Network layer

This is the load balancer that works at the network's transport layer, also known as layer 4. This performs routing based on networking information such as IP addresses and is not able to perform content-based routing. These are often dedicated hardware devices that can operate at high speed.

### Application layer

This is the load balancer that operates at the application layer, also known as layer 7. Load balancers can read requests in their entirety and perform content-based routing. This allows the management of load based on a full understanding of traffic.

## Types

Let's look at different types of load balancers:

### Software

Software load balancers usually are easier to deploy than hardware versions. They also tend to be more cost-effective and flexible, and they are used in conjunction with software development environments. The software approach gives us the flexibility of configuring the load balancer to our environment's specific needs. The boost in flexibility may come at the cost of having to do more work to set up the load balancer. Compared to hardware versions, which offer more of a closed-box approach, software balancers give us more freedom to make changes and upgrades.

Software load balancers are widely used and are available either as installable solutions that require configuration and management or as a managed cloud service.

### Hardware

As the name implies, a hardware load balancer relies on physical, on-premises hardware to distribute application and network traffic. These devices can handle a large volume of traffic but often carry a hefty price tag and are fairly limited in terms of flexibility.

Hardware load balancers include proprietary firmware that requires maintenance and updates as new versions, and security patches are released.

### DNS

DNS load balancing is the practice of configuring a domain in the Domain Name System (DNS) such that client requests to the domain are distributed across a group of server machines.

Unfortunately, DNS load balancing has inherent problems limiting its reliability and efficiency. Most significantly, DNS does not check for server and network outages, or errors. It always returns the same set of IP addresses for a domain even if servers are down or inaccessible.

## Routing Algorithms

Now, let's discuss commonly used routing algorithms:

- **Round-robin**: Requests are distributed to application servers in rotation.
- **Weighted Round-robin**: Builds on the simple Round-robin technique to account for differing server characteristics such as compute and traffic handling capacity using weights that can be assigned via DNS records by the administrator.
- **Least Connections**: A new request is sent to the server with the fewest current connections to clients. The relative computing capacity of each server is factored into determining which one has the least connections.
- **Least Response Time**: Sends requests to the server selected by a formula that combines the fastest response time and fewest active connections.
- **Least Bandwidth**: This method measures traffic in megabits per second (Mbps), sending client requests to the server with the least Mbps of traffic.
- **Hashing**: Distributes requests based on a key we define, such as the client IP address or the request URL.

## Advantages

Load balancing also plays a key role in preventing downtime, other advantages of load balancing include the following:

- Scalability
- Redundancy
- Flexibility
- Efficiency

## Redundant load balancers

As you must've already guessed, the load balancer itself can be a single point of failure. To overcome this, a second or `N` number of load balancers can be used in a cluster mode.

And, if there's a failure detection and the _active_ load balancer fails, another _passive_ load balancer can take over which will make our system more fault-tolerant.

![redundant-load-balancing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/redundant-load-balancer.png)

## Features

Here are some commonly desired features of load balancers:

- **Autoscaling**: Starting up and shutting down resources in response to demand conditions.
- **Sticky sessions**: The ability to assign the same user or device to the same resource in order to maintain the session state on the resource.
- **Healthchecks**: The ability to determine if a resource is down or performing poorly in order to remove the resource from the load balancing pool.
- **Persistence connections**: Allowing a server to open a persistent connection with a client such as a WebSocket.
- **Encryption**: Handling encrypted connections such as TLS and SSL.
- **Certificates**: Presenting certificates to a client and authentication of client certificates.
- **Compression**: Compression of responses.
- **Caching**: An application-layer load balancer may offer the ability to cache responses.
- **Logging**: Logging of request and response metadata can serve as an important audit trail or source for analytics data.
- **Request tracing**: Assigning each request a unique id for the purposes of logging, monitoring, and troubleshooting.
- **Redirects**: The ability to redirect an incoming request based on factors such as the requested path.
- **Fixed response**: Returning a static response for a request such as an error message.

## Examples

Following are some of the load balancing solutions commonly used in the industry:

- [Amazon Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing)
- [Azure Load Balancing](https://azure.microsoft.com/en-in/services/load-balancer)
- [GCP Load Balancing](https://cloud.google.com/load-balancing)
- [DigitalOcean Load Balancer](https://www.digitalocean.com/products/load-balancer)
- [Nginx](https://www.nginx.com)
- [HAProxy](http://www.haproxy.org)
