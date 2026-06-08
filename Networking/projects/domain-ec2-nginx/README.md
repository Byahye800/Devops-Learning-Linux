# Domain + EC2 + NGINX Project

This project brings together the main networking concepts from the module by deploying a web server on AWS EC2, installing NGINX, configuring DNS, and pointing a domain name to the EC2 public IPv4 address.

The goal is to prove that I understand how DNS, IP addressing, ports, cloud firewall rules, and web services work together in a real infrastructure flow.

## Project Objective

Deploy a simple web page that can be reached through a custom domain.

The final flow should look like this:

```text
User Browser
    ↓
Domain Name
    ↓
DNS A Record
    ↓
EC2 Public IPv4 Address
    ↓
Security Group Allows HTTP
    ↓
NGINX Web Server
    ↓
Web Page
```

## Tools and Services

| Tool/Service | Purpose |
|---|---|
| AWS EC2 | Hosts the Linux server running NGINX. |
| NGINX | Serves the web page over HTTP. |
| DNS provider | Stores the domain DNS records. |
| A record | Points the domain to the EC2 public IPv4 address. |
| Security Group | Controls inbound access to the EC2 instance. |
| SSH | Used to connect to and configure the server. |
| `dig` / `nslookup` | Used to verify DNS resolution. |
| `curl` | Used to test HTTP responses from the command line. |

## What This Project Demonstrates

This project demonstrates:

- Launching a cloud server
- Connecting to a server using SSH
- Installing and managing NGINX
- Understanding HTTP access on port 80
- Configuring a security group to allow web traffic
- Creating a DNS A record
- Pointing a domain to cloud infrastructure
- Verifying DNS and web server behaviour
- Documenting commands, evidence, and troubleshooting steps

## Planned Build Steps

1. Register or use a domain.
2. Launch an AWS EC2 instance.
3. Configure the EC2 security group.
4. Allow SSH access for administration.
5. Allow HTTP access on port 80.
6. Connect to the instance using SSH.
7. Install NGINX.
8. Start and enable the NGINX service.
9. Replace or customise the default NGINX page.
10. Create an A record pointing the domain to the EC2 public IPv4 address.
11. Verify DNS resolution using `dig` and `nslookup`.
12. Confirm the site loads in a browser.
13. Capture focused evidence.
14. Document any issues and fixes.

## Security Group Plan

The EC2 security group should allow only what is needed.

| Port | Purpose | Notes |
|---|---|---|
| 22 | SSH | Used for server administration. Should be restricted where possible. |
| 80 | HTTP | Required for the browser to access the NGINX web page. |
| 443 | HTTPS | Future improvement after HTTP is working. |

The first version of the project focuses on HTTP because the assignment requires the domain to load the NGINX page. HTTPS can be added later as an improvement using TLS certificates.

## DNS Plan

The domain will use an A record to point to the EC2 public IPv4 address.

Example:

```text
example.com → EC2 Public IPv4
```

If a subdomain is used, the record may look like this:

```text
nginx.example.com → EC2 Public IPv4
```

The important part is that the DNS record returns the correct public IP address for the EC2 instance.

## Verification Plan

The project will be verified in several ways:

| Check | Purpose |
|---|---|
| EC2 instance running | Confirms the server exists and is active. |
| Security group allows port 80 | Confirms HTTP traffic can reach the instance. |
| NGINX status check | Confirms the web server is running. |
| `curl localhost` | Confirms NGINX works from inside the server. |
| `curl http://domain` | Confirms the web server responds externally. |
| `dig +short domain` | Confirms DNS returns the expected IP. |
| Browser test | Confirms the domain loads the web page for a user. |

## Evidence Plan

Evidence will be stored in:

```text
Networking/projects/domain-ec2-nginx/evidence/
├── screenshots/
└── terminal-outputs/
```

Evidence should be focused and meaningful.

Planned evidence includes:

- EC2 instance running
- Security group HTTP rule
- NGINX installed and active
- DNS A record configured
- DNS resolution output
- Domain loading the NGINX page
- Custom page loading if added

## Project Notes

This project is intentionally small but important. It connects several networking ideas in one practical build: DNS resolution, public IP addressing, HTTP traffic, port access, security group rules, Linux service management, and browser verification.

A simple website loading through a custom domain proves more than it first appears. It shows that the network path from user to domain to cloud server to web service is working.

## Future Improvements

Possible improvements after the base project works:

- Add HTTPS using TLS certificates.
- Use a custom NGINX landing page.
- Add a subdomain specifically for the project.
- Restrict SSH access more tightly.
- Add a basic architecture diagram.
- Move the server into a more complete VPC design.
- Add a load balancer in front of the instance.
- Automate setup with a script or infrastructure-as-code later.

## Networking in DevOps

This project reflects a common DevOps responsibility: making an application reachable and reliable.

A DevOps engineer needs to understand more than just how to install a web server. They need to know how users reach that server, how DNS points to infrastructure, how cloud firewall rules control access, how ports expose services, and how to verify each part of the path.

This project turns networking theory into an applied cloud deployment.
