# DNS

DNS stands for Domain Name System. It is the system that translates human-readable domain names into IP addresses that computers can use to find servers and services.

Without DNS, users would need to remember IP addresses instead of names like `google.com`, `github.com`, or a custom project domain. DNS makes the internet easier to use by allowing people to access services through names while the network still works with IP addresses underneath.

## Why DNS Matters

DNS is important because it connects names to infrastructure. When a user types a domain into a browser, DNS helps locate the IP address behind that domain so the request can be sent to the correct server.

In practical infrastructure, DNS is often the connection point between a public domain and a cloud resource. For example, a domain can be pointed to an AWS EC2 public IPv4 address using an A record.

## DNS Components

DNS is made up of several important components.

| Component | Purpose |
|---|---|
| Domain name | The readable name users type into a browser. |
| Name server | Stores or helps find DNS information for a domain. |
| Zone file | Stores DNS records for a domain in an organised format. |
| DNS record | A specific entry that tells DNS how to handle a domain or subdomain. |
| Resolver | The system that performs DNS lookups on behalf of the client. |

## Authoritative and Recursive DNS

A recursive DNS resolver performs the lookup process for the client. It asks other DNS servers where to find the correct answer.

An authoritative DNS server holds the final DNS records for a domain. If a domain has an A record pointing to a specific IP address, the authoritative server is where that record is stored.

Simple version:

| Type | What It Does |
|---|---|
| Recursive resolver | Searches for the answer. |
| Authoritative server | Holds the official answer. |

## DNS Records

DNS records are entries inside a domain’s DNS zone. Each record has a specific purpose.

| Record | Purpose |
|---|---|
| A | Maps a domain name to an IPv4 address. |
| AAAA | Maps a domain name to an IPv6 address. |
| CNAME | Creates an alias from one domain name to another. |
| MX | Defines mail servers for the domain. |
| NS | Defines the name servers for the domain. |
| TXT | Stores text values often used for verification, SPF, or security settings. |
| PTR | Used for reverse DNS lookups. |
| SOA | Holds authority information about the DNS zone. |
| SRV | Defines service location information. |

## A Records

An A record maps a domain or subdomain to an IPv4 address.

Example:

```text
example.com → 203.0.113.10
```

This is one of the most important record types for the practical project because the domain needs to point to the EC2 public IPv4 address.

## AAAA Records

An AAAA record maps a domain to an IPv6 address.

Example:

```text
example.com → 2001:0db8:85a3::7334
```

AAAA records are used where IPv6 is supported.

## CNAME Records

A CNAME record creates an alias from one name to another.

Example:

```text
www.example.com → example.com
```

This is useful when you want multiple names to point towards the same destination without managing separate IP mappings for each one.

## MX Records

MX records are used for email routing. They tell the internet which mail servers should receive email for a domain.

Example use case:

```text
Email for example.com should be handled by the domain’s mail provider.
```

## TXT Records

TXT records store text information inside DNS. They are commonly used for domain verification, email security, SPF records, and other metadata.

Examples include:

- Proving ownership of a domain
- Email sender verification
- Security-related configuration

## DNS Resolution Process

When a user visits a website, DNS resolution usually follows a process like this:

1. The user enters a domain name into the browser.
2. The computer checks local DNS cache and `/etc/hosts`.
3. If there is no local answer, the request goes to a recursive resolver.
4. The resolver queries root DNS servers.
5. The root servers point to the correct top-level domain servers.
6. The top-level domain servers point to the authoritative name servers.
7. The authoritative name server returns the DNS record.
8. The resolver returns the IP address to the client.
9. The browser connects to the returned IP address.

This happens quickly, but it is a critical part of how websites and services are reached.

## DNS Tools

DNS can be tested from the command line.

| Tool | Purpose |
|---|---|
| `nslookup` | Performs basic DNS lookups. |
| `dig` | Provides detailed DNS query information. |
| `dig +short` | Returns a shorter DNS answer. |
| `/etc/hosts` | Allows local name-to-IP mappings before DNS is used. |

## Example Commands

```bash
nslookup google.com
```

```bash
dig google.com
```

```bash
dig +short google.com
```

```bash
dig NS google.com
```

These commands are useful for checking whether a domain resolves correctly and which DNS records are being returned.

## `/etc/hosts`

The `/etc/hosts` file allows a local machine to map a hostname to an IP address before using DNS.

Example:

```text
127.0.0.1 example.local
```

This can be useful for local testing, but it should be handled carefully because incorrect entries can override real DNS lookups on the local machine.

## DNS in the Practical Project

In the domain, EC2, and NGINX project, DNS will connect the custom domain to the EC2 public IPv4 address.

The flow will look like this:

```text
Domain Name
    ↓
DNS A Record
    ↓
EC2 Public IPv4 Address
    ↓
NGINX Web Server
```

This proves that DNS is not just a theory topic. It directly affects whether users can reach a deployed service.

## Key Takeaway

DNS translates domain names into IP addresses so users can access services using readable names. It is one of the most important parts of modern infrastructure because websites, APIs, cloud services, and applications all depend on correct DNS configuration.

## Networking in DevOps

In DevOps, DNS is a core part of deployment and service availability. A working server is not enough if users cannot reach it through the correct domain name.

When deploying applications, a DevOps engineer may need to configure A records, CNAME records, Route 53 hosted zones, Cloudflare DNS settings, or internal service discovery. If a website fails to load, DNS is one of the first areas to check: does the domain resolve, does it return the correct IP address, and has the record propagated correctly?

Understanding DNS helps connect infrastructure to users in a controlled and reliable way.
