# Routing, Subnetting and NAT

Routing, subnetting, and NAT explain how traffic moves between networks, how networks are divided into smaller sections, and how private devices communicate with the public internet.

These concepts are important because modern infrastructure is rarely one flat network. Cloud environments, office networks, home networks, and production systems all use routing and subnetting to organise traffic and control communication.

## Routing

Routing is the process of deciding where network traffic should go next.

When a device sends traffic to a destination outside its own local network, routers help move that traffic across one or more networks until it reaches the correct destination.

A router uses routing information to decide the best path for traffic.

## Why Routing Matters

Routing matters because it allows separate networks to communicate with each other.

For example:

```text
Laptop
    ↓
Home Router
    ↓
Internet Service Provider
    ↓
Internet Routers
    ↓
Web Server
```

Without routing, devices would only be able to communicate inside their own local network.

## Routing Tables

A routing table is a set of rules that helps decide where traffic should be sent.

A routing table usually includes:

| Item | Meaning |
|---|---|
| Destination network | The network traffic is trying to reach. |
| Next hop | The next router or gateway traffic should be sent to. |
| Interface | The network interface used to send the traffic. |
| Metric | A value used to help choose between possible routes. |

In simple terms, a routing table tells the device:

```text
If traffic is going to this network, send it this way.
```

## Static Routing

Static routing is when routes are manually configured.

It is predictable and simple in small environments, but it can become difficult to manage as networks grow.

Example use case:

```text
A small lab network where the route never changes.
```

## Dynamic Routing

Dynamic routing allows routers to learn and update routes automatically using routing protocols.

This is useful in larger networks where routes may change due to failures, congestion, or design updates.

## Common Routing Protocols

| Protocol | Purpose |
|---|---|
| OSPF | Used inside organisations to dynamically route traffic within a network. |
| BGP | Used between large networks and internet providers to route traffic across the internet. |

OSPF is commonly associated with internal routing. BGP is one of the key protocols behind global internet routing.

## Subnetting

Subnetting is the process of dividing a larger network into smaller networks.

This makes networks easier to manage, improves organisation, and can help with security and performance.

Example:

```text
One large network:
192.168.1.0/24

Can be divided into smaller subnets:
192.168.1.0/26
192.168.1.64/26
192.168.1.128/26
192.168.1.192/26
```

## Why Subnetting Matters

Subnetting helps separate different parts of an environment.

For example, a cloud environment may have:

- Public subnets for load balancers or public web servers
- Private subnets for application servers
- Private subnets for databases
- Separate subnets across different availability zones

This separation helps with security, design, and traffic control.

## CIDR Notation

CIDR stands for Classless Inter-Domain Routing.

CIDR notation shows how much of an IP address belongs to the network portion.

Example:

```text
192.168.1.0/24
```

The `/24` means the first 24 bits represent the network portion.

A simple way to understand it:

| CIDR | Approximate Usable Size |
|---|---|
| `/24` | 256 total addresses |
| `/25` | 128 total addresses |
| `/26` | 64 total addresses |
| `/27` | 32 total addresses |
| `/28` | 16 total addresses |

As the prefix number gets larger, the subnet gets smaller.

## Subnet Masks

A subnet mask shows which part of an IP address belongs to the network and which part can be used for hosts.

Example:

```text
255.255.255.0
```

This commonly matches a `/24` network.

For example:

```text
192.168.1.0/24
```

This means devices from `192.168.1.1` to `192.168.1.254` can usually be used as host addresses, while the network and broadcast addresses are reserved.

## Public and Private IPs

Public IP addresses are reachable over the internet.

Private IP addresses are used inside internal networks and are not directly reachable from the public internet.

Common private IPv4 ranges include:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

Private IPs are heavily used in cloud networks, home networks, and company networks.

## NAT

NAT stands for Network Address Translation.

NAT allows devices using private IP addresses to communicate with external networks by translating their private address into a public address.

Simple example:

```text
Private device: 192.168.1.10
Router public IP: 98.117.53.254
Destination: google.com
```

The public website sees the router’s public IP, not the private IP of the internal device.

## Why NAT Matters

NAT is important because private IP addresses cannot communicate directly over the internet. NAT allows many private devices to share one or more public IP addresses.

This is common in:

- Home networks
- Office networks
- Cloud networks
- Private subnets that need outbound internet access

## Types of NAT

| NAT Type | Explanation |
|---|---|
| Static NAT | Maps one private IP to one public IP. |
| Dynamic NAT | Maps private IPs to a pool of public IPs. |
| PAT | Allows many private devices to share one public IP using different ports. |

PAT is also known as Port Address Translation. It is commonly used when many internal devices share one public IP.

## Routing, Subnetting and NAT Together

These concepts often work together.

Example cloud flow:

```text
Private EC2 Instance
    ↓
Route Table
    ↓
NAT Gateway
    ↓
Internet Gateway
    ↓
Internet
```

In that design, the EC2 instance may not have a public IP, but it can still reach the internet through NAT.

## Key Takeaway

Routing moves traffic between networks. Subnetting divides networks into smaller, organised sections. NAT allows private IP addresses to communicate with public networks.

Together, these concepts explain a major part of how modern networks and cloud infrastructure are designed.

## Networking in DevOps

In DevOps, routing, subnetting, and NAT are important when working with cloud environments such as AWS.

A DevOps engineer needs to understand why a public web server may sit in a public subnet, why a database should usually sit in a private subnet, how route tables control traffic, and how NAT allows private resources to download updates without exposing them directly to the internet.

If an application cannot reach another service, the issue may not be the application code. It could be a subnet, route table, NAT gateway, internet gateway, security group, or private/public IP design problem. Understanding these concepts makes troubleshooting much more structured.
