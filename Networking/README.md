# Networking Module

This module documents my networking fundamentals learning as part of my DevOps portfolio.

The purpose of this section is to build a practical understanding of how devices, servers, applications, domains, and cloud services communicate across networks. The notes explain the core concepts clearly, while the project work shows how those concepts are applied in a real infrastructure setup.

## Module Scope

This module covers:

* Networking fundamentals
* LANs and WANs
* Routers, switches, and firewalls
* IP addressing and MAC addresses
* Ports, protocols, TCP, and UDP
* The OSI model and TCP/IP model
* DNS and DNS records
* Routing, subnetting, CIDR, and NAT
* Network troubleshooting
* Cloud networking concepts

Each notes file ends with a short section connecting the topic to real DevOps environments, such as deployments, DNS configuration, cloud infrastructure, service access, firewall rules, troubleshooting, and application availability.

## Notes

| File                                                                       | Topic                                                                             |
| -------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [01-networking-overview.md](notes/01-networking-overview.md)               | Networking fundamentals, network types, key components, OSI, and TCP/IP models    |
| [02-ip-addressing-and-ports.md](notes/02-ip-addressing-and-ports.md)       | IP addresses, MAC addresses, ports, protocols, TCP, UDP, and common service ports |
| [03-dns.md](notes/03-dns.md)                                               | DNS, name servers, zone files, DNS records, resolution flow, and DNS tools        |
| [04-routing-subnetting-and-nat.md](notes/04-routing-subnetting-and-nat.md) | Routing, subnetting, CIDR, public/private IPs, and NAT                            |
| [05-network-troubleshooting.md](notes/05-network-troubleshooting.md)       | Practical troubleshooting tools and a structured approach to network debugging    |

## Practical Project

The main hands-on project for this module is:

[Domain + EC2 + NGINX Project](projects/domain-ec2-nginx/README.md)

This project brings the module together by deploying a web server on AWS EC2, installing NGINX, configuring DNS, and pointing a domain name to the EC2 public IPv4 address.

## Skills Demonstrated

This module is designed to demonstrate:

* Clear understanding of networking fundamentals
* Ability to explain how traffic moves across a network
* Understanding of DNS, records, and domain resolution
* Awareness of ports, protocols, and service access
* Basic cloud networking knowledge using AWS EC2
* Troubleshooting mindset for connectivity issues
* Professional documentation of theory, commands, project work, and evidence

## Project Structure

```text
Networking/
├── README.md
├── notes/
└── projects/
    └── domain-ec2-nginx/
        ├── README.md
        ├── commands.md
        ├── troubleshooting.md
        └── evidence/
            ├── screenshots/
            └── terminal-outputs/
```
