# Networking Overview

Networking is the foundation that allows devices, servers, applications, and cloud services to communicate with each other. Without networking, systems would exist in isolation and would not be able to exchange data, share resources, or support internet-based services.

At a basic level, a computer network connects devices so they can send and receive information. In real infrastructure, this could mean a user accessing a website, an application connecting to a database, a CI/CD pipeline reaching a deployment server, or cloud services communicating across private and public networks.

## Why Networking Matters

Networking is important because almost every modern system depends on communication between different components. Websites, APIs, databases, monitoring tools, cloud platforms, and deployment pipelines all rely on reliable network connectivity.

A good understanding of networking helps explain how traffic moves from one place to another, why certain services are reachable, why others are blocked, and how to investigate problems when communication fails.

In DevOps, this matters because deployments are not only about running code. The application also needs to be reachable, secure, correctly routed, and able to communicate with the services around it.

## LAN and WAN

Networks are often described by the area they cover.

| Type | Meaning            | Explanation                                                                                 | Example                                                   |
| ---- | ------------------ | ------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| LAN  | Local Area Network | A network that connects devices within a small area such as a home, office, or data centre. | Home Wi-Fi or an office network                           |
| WAN  | Wide Area Network  | A network that connects multiple smaller networks across large distances.                   | The internet or a company network across different cities |

A LAN is usually smaller, faster, and privately managed. A WAN covers a much larger area and connects separate networks together.

The internet is the largest example of a WAN because it connects networks across the world.

## Key Networking Components

Networking depends on several core components that control how devices connect, communicate, and stay protected.

| Component | Purpose                                                       | Simple Explanation                                                                           |
| --------- | ------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Switch    | Connects devices within the same local network.               | Helps devices inside a LAN communicate with each other.                                      |
| Router    | Connects different networks and directs traffic between them. | Helps traffic move from one network to another, such as from a home network to the internet. |
| Firewall  | Monitors and controls incoming and outgoing traffic.          | Acts like a security checkpoint for network traffic.                                         |

These components work together. A switch helps local devices communicate, a router moves traffic between networks, and a firewall controls what traffic is allowed or blocked.

## IP Addresses and MAC Addresses

Devices need addresses so network traffic knows where to go.

An IP address is a logical address used to identify a device on a network. It helps route traffic between devices and networks.

A MAC address is a hardware identifier assigned to a network interface. It is mainly used within a local network to identify devices at the data link level.

Simple way to think about it:

| Address Type | What It Does                                           |
| ------------ | ------------------------------------------------------ |
| IP address   | Helps traffic find the correct device across networks. |
| MAC address  | Helps identify a device within a local network.        |

The detailed differences between IPv4, IPv6, MAC addresses, ports, TCP, and UDP are covered in the next note.

## Ports and Protocols

A port is a logical endpoint used by applications and services. It helps a device know which application should receive the traffic.

For example:

| Port | Common Use |
| ---- | ---------- |
| 22   | SSH        |
| 53   | DNS        |
| 80   | HTTP       |
| 443  | HTTPS      |

Protocols define the rules for communication. Two important transport protocols are TCP and UDP.

TCP is reliable and connection-oriented. UDP is faster and connectionless, but it does not guarantee delivery or order.

This matters because different applications need different types of communication. Web browsing and SSH usually need reliability, while streaming and gaming often prioritise speed.

## The OSI Model

The OSI model is a seven-layer model used to understand how data moves through a network. It separates networking into layers so each part of the communication process is easier to understand and troubleshoot.

| Layer | Name         | Purpose                                                                                |
| ----- | ------------ | -------------------------------------------------------------------------------------- |
| 7     | Application  | Network services used by applications, such as HTTP, DNS, SSH, and FTP.                |
| 6     | Presentation | Formats, encrypts, or translates data so it can be understood by the receiving system. |
| 5     | Session      | Manages sessions and connections between applications.                                 |
| 4     | Transport    | Handles end-to-end communication using TCP or UDP.                                     |
| 3     | Network      | Handles IP addressing and routing between networks.                                    |
| 2     | Data Link    | Handles local network communication using frames and MAC addresses.                    |
| 1     | Physical     | Moves raw bits across physical media such as cables, fibre, or wireless signals.       |

The OSI model is useful because it gives a structured way to think about network problems. Instead of guessing, you can ask which layer the issue belongs to.

For example:

* If a cable or Wi-Fi connection is broken, the issue may be at the physical layer.
* If DNS is failing, the issue may be at the application layer.
* If a port is blocked, the issue may involve the transport layer or firewall rules.
* If traffic cannot reach another network, the issue may involve routing at the network layer.

## The TCP/IP Model

The TCP/IP model is a simpler networking model commonly used to describe real-world internet communication.

| TCP/IP Layer   | Related Concepts                         |
| -------------- | ---------------------------------------- |
| Application    | HTTP, DNS, TLS, SSH                      |
| Transport      | TCP, UDP                                 |
| Internet       | IP addressing and routing                |
| Network Access | Ethernet, Wi-Fi, physical network access |

The TCP/IP model is practical because it closely matches how the internet works. It helps explain how applications communicate over networks using protocols like HTTP, DNS, TCP, UDP, and IP.

## OSI Model vs TCP/IP Model

The OSI model is more detailed and useful for learning and troubleshooting. The TCP/IP model is more practical and reflects how modern networks are commonly implemented.

Both models are useful because they help break networking down into smaller parts. This makes it easier to understand how a request moves from a user’s device to a server and back again.

## Example: Loading a Website

When a user visits a website, several networking concepts work together:

1. The browser uses DNS to find the website’s IP address.
2. The device sends traffic towards that IP address.
3. Routers help move the traffic across networks.
4. TCP establishes a reliable connection if the site uses HTTP or HTTPS.
5. The request reaches the web server.
6. The server responds with the website content.
7. The browser displays the page.

This simple action depends on DNS, IP addressing, routing, ports, protocols, and application-layer services working correctly together.

## Key Takeaway

Networking is not just about cables, routers, or technical definitions. It is the system that allows modern infrastructure to communicate. Understanding the basics of LANs, WANs, network devices, addressing, protocols, and network models gives a strong foundation for cloud, DevOps, cybersecurity, and troubleshooting work.

## Networking in DevOps

In DevOps, networking knowledge helps engineers deploy, secure, and troubleshoot real systems. A working application still needs DNS to point users to the correct infrastructure, open ports to accept traffic, firewall or security group rules to control access, and routing to move traffic between networks.

This is why networking connects directly to cloud projects. When deploying a web server on AWS EC2, the server must have a reachable public IP, the security group must allow the correct port, DNS must point to the right address, and the web service must be running. If the website does not load, a DevOps engineer needs to check each part logically instead of guessing.
