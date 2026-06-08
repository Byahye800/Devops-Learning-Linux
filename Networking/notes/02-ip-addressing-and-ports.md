# IP Addressing and Ports

IP addressing and ports are two of the most important ideas in networking because they explain how traffic reaches the correct device and then the correct service on that device.

An IP address helps identify where traffic should go. A port helps identify which application or service should handle that traffic once it arrives.

A simple way to think about it:

```text
IP address = the building address
Port = the specific door or room inside the building
```

If a server is running multiple services, the IP address gets traffic to the server, but the port decides whether the traffic is meant for SSH, HTTP, HTTPS, DNS, or another service.

## IP Addresses

An IP address is a logical address used to identify a device on a network. Devices use IP addresses so they can send and receive data across local networks and the internet.

In practical terms, if one machine wants to communicate with another, it needs an address to send traffic to. That is the role of an IP address.

There are two main versions of IP addresses:

* IPv4
* IPv6

## IPv4

IPv4 is the older and still very common version of IP addressing. It uses a 32-bit address format and is usually written as four decimal numbers separated by dots.

Example:

```text
192.168.0.5
```

Each section is called an octet, and each octet can range from 0 to 255.

IPv4 is easy to read and is still heavily used in home networks, business networks, cloud platforms, and public internet infrastructure.

The main limitation of IPv4 is address space. Because it uses 32 bits, there are only around 4.3 billion possible IPv4 addresses. That sounds like a lot, but it became a limitation as the internet grew.

## IPv6

IPv6 was created to provide a much larger address space. It uses a 128-bit address format and is written using hexadecimal values separated by colons.

Example:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

IPv6 can support a much larger number of addresses than IPv4. This is important because the number of internet-connected devices has grown massively, including phones, laptops, servers, cloud resources, IoT devices, and containers.

## IPv4 vs IPv6

| Feature          | IPv4                                   | IPv6                                     |
| ---------------- | -------------------------------------- | ---------------------------------------- |
| Address size     | 32-bit                                 | 128-bit                                  |
| Format           | Four decimal numbers separated by dots | Hexadecimal groups separated by colons   |
| Example          | `192.168.0.5`                          | `2001:0db8:85a3::7334`                   |
| Address capacity | Limited compared to IPv6               | Very large address space                 |
| Common use       | Still widely used                      | Increasingly used across modern networks |

IPv4 is still very common, but IPv6 is important because it supports the long-term growth of the internet.

## Public and Private IP Addresses

Not every IP address is used directly on the public internet.

A public IP address is reachable over the internet. For example, an AWS EC2 instance can have a public IPv4 address so users can access a website hosted on it.

A private IP address is used inside private networks, such as a home network, office network, or cloud VPC. Private IPs are not directly reachable from the public internet.

Common private IPv4 ranges include:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

This distinction matters because cloud infrastructure often uses both. A server may have a private IP for internal communication and a public IP for internet access.

## MAC Addresses

A MAC address is a unique hardware identifier assigned to a network interface. It operates at the data link layer and is mainly used for communication inside a local network.

Example:

```text
00:1A:2B:3C:4D:5E
```

A MAC address is different from an IP address. An IP address is logical and can change depending on the network. A MAC address is tied to the network interface itself.

## IP Address vs MAC Address

| Address Type | Layer           | Purpose                                          |
| ------------ | --------------- | ------------------------------------------------ |
| IP address   | Network layer   | Helps route traffic between devices and networks |
| MAC address  | Data link layer | Helps identify devices within a local network    |

A useful way to separate them is:

```text
MAC address = local network identity
IP address = network routing identity
```

Switches mainly use MAC addresses to move traffic inside a LAN. Routers use IP addresses to move traffic between networks.

## Ports

A port is a logical endpoint used by applications and services. When traffic reaches a device, the port number helps decide which service should receive it.

For example, a server may accept:

* SSH traffic on port 22
* HTTP traffic on port 80
* HTTPS traffic on port 443

The same server can run multiple services because each service listens on a different port.

## Common Ports

| Port | Protocol/Service | Purpose                         |
| ---- | ---------------- | ------------------------------- |
| 22   | SSH              | Secure remote access to servers |
| 53   | DNS              | Domain name resolution          |
| 80   | HTTP             | Unencrypted web traffic         |
| 443  | HTTPS            | Encrypted web traffic           |
| 25   | SMTP             | Email sending                   |
| 3306 | MySQL            | MySQL database connections      |

These ports are important in DevOps because deployments often require checking whether the right service is listening on the right port and whether firewalls or security groups allow access.

## Protocols

A protocol is a set of rules that defines how data is transmitted between devices.

Protocols matter because different types of communication need different behaviour. Some applications need reliability and ordered delivery. Others need speed and can tolerate some packet loss.

Two important transport-layer protocols are:

* TCP
* UDP

## TCP

TCP stands for Transmission Control Protocol.

TCP is connection-oriented, which means it establishes a connection before data is transferred. It is designed for reliable communication.

TCP provides:

* Connection setup using a handshake
* Reliable delivery
* Data delivered in order
* Error checking
* Flow control

TCP is used when accuracy matters more than speed.

Common examples include:

* Web browsing
* SSH
* Email
* File transfer
* API communication

If a packet is lost, TCP can detect the issue and resend data. This makes it reliable, but it also creates more overhead compared to UDP.

## UDP

UDP stands for User Datagram Protocol.

UDP is connectionless, which means it sends data without first establishing a full connection. It is faster than TCP but does not guarantee delivery or order.

UDP is used when speed matters more than perfect reliability.

Common examples include:

* Video streaming
* Online gaming
* Voice calls
* DNS queries
* VPN traffic

UDP can be useful for real-time applications because waiting to resend missing data may be worse than simply continuing with the live stream or session.

## TCP vs UDP

| Feature        | TCP                                     | UDP                         |
| -------------- | --------------------------------------- | --------------------------- |
| Connection     | Connection-oriented                     | Connectionless              |
| Reliability    | Reliable delivery                       | No delivery guarantee       |
| Ordering       | Ensures data arrives in order           | No guaranteed order         |
| Speed          | Slower due to overhead                  | Faster due to less overhead |
| Error checking | Yes                                     | Limited compared to TCP     |
| Common uses    | Web browsing, SSH, email, file transfer | Streaming, gaming, DNS, VPN |

TCP and UDP are both useful. The right choice depends on what the application needs.

## How Ports and Protocols Work Together

Ports and protocols work together to make network communication useful.

For example:

```text
HTTP = TCP port 80
HTTPS = TCP port 443
DNS = usually UDP port 53
SSH = TCP port 22
```

When a browser loads a website using HTTPS, it usually connects to the server on TCP port 443. The IP address identifies the server, TCP provides reliable communication, and port 443 identifies the HTTPS service.

## Example: Connecting to a Website

When a user visits a website, this is roughly what happens:

1. The browser asks DNS for the website’s IP address.
2. DNS returns an IP address.
3. The browser connects to that IP address.
4. The connection uses the correct port, usually 80 for HTTP or 443 for HTTPS.
5. TCP establishes a reliable connection.
6. The web server responds with the website content.

This is why IP addresses, ports, and protocols are linked. They work together to move traffic to the correct destination and service.

## Key Takeaway

IP addresses identify devices and help route traffic across networks. MAC addresses identify devices inside local networks. Ports identify the specific service receiving traffic on a device. TCP and UDP define how transport communication behaves.

Understanding these basics makes it much easier to troubleshoot why a server, website, database, or cloud service is reachable or unreachable.

## Networking in DevOps

In DevOps, IP addresses and ports are part of everyday infrastructure work. When deploying an application, a DevOps engineer needs to know which server should receive traffic, which port the service listens on, and whether the firewall or security group allows that traffic.

For example, if an AWS EC2 instance is running NGINX, the instance needs a reachable IP address and the security group must allow HTTP traffic on port 80. If users cannot access the website, the issue could be the wrong IP address, a blocked port, DNS pointing to the wrong place, or NGINX not listening correctly.

This is why understanding IP addressing, ports, TCP, and UDP helps turn troubleshooting from guesswork into a logical process.
