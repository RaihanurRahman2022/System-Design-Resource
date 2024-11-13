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
