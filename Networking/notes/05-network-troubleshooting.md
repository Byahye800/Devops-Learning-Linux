# Network Troubleshooting

Network troubleshooting is the process of identifying, narrowing down, and fixing problems that stop systems from communicating correctly.

In real environments, a connectivity issue can come from many places: DNS, routing, firewall rules, service configuration, ports, cloud security groups, or the application itself. Troubleshooting gives a structured way to investigate instead of guessing.

## Why Troubleshooting Matters

Troubleshooting matters because network problems can cause downtime, failed deployments, unreachable websites, broken APIs, and failed service-to-service communication.

A good troubleshooting process helps answer questions like:

- Is the destination reachable?
- Does DNS resolve correctly?
- Is traffic going to the right IP address?
- Is the correct port open?
- Is a firewall or security group blocking access?
- Is the service actually running?
- Is the issue local, network-level, or application-level?

## Troubleshooting Mindset

The best approach is to move step by step.

Start with the simplest checks, then move deeper:

```text
1. Check the address
2. Check DNS
3. Check basic connectivity
4. Check the route
5. Check the port
6. Check firewall/security rules
7. Check the service
8. Check logs
```

This keeps the investigation controlled and avoids random guessing.

## `ping`

`ping` tests basic reachability between your machine and another host.

Example:

```bash
ping google.com
```

If ping works, it usually means the host is reachable at a basic network level.

If ping fails, it does not always mean the service is down. Some systems block ICMP traffic, so ping should be treated as one signal, not the full answer.

## `traceroute`

`traceroute` shows the path traffic takes to reach a destination.

Example:

```bash
traceroute google.com
```

It shows the network hops between your machine and the destination.

This is useful when trying to understand where traffic may be slowing down or failing.

On some systems, the command may be:

```bash
tracepath google.com
```

or on Windows:

```powershell
tracert google.com
```

## `nslookup`

`nslookup` checks DNS resolution.

Example:

```bash
nslookup google.com
```

This helps confirm whether a domain name resolves to an IP address.

For a domain project, this is useful for checking whether your custom domain points to the correct public IP.

## `dig`

`dig` is a more detailed DNS lookup tool.

Examples:

```bash
dig google.com
```

```bash
dig +short google.com
```

```bash
dig NS google.com
```

`dig` is useful because it gives more DNS detail than a basic browser check.

## `curl`

`curl` tests HTTP or HTTPS responses from the command line.

Example:

```bash
curl http://example.com
```

To show only headers:

```bash
curl -I http://example.com
```

This is useful because it helps confirm whether a web server responds even before checking in a browser.

## Checking Listening Ports

If a service is running, it should usually listen on a port.

Useful commands include:

```bash
ss -tuln
```

or:

```bash
sudo lsof -i -P -n
```

These commands help check whether services are listening on ports such as 22, 80, or 443.

## Checking a Service

For a Linux service like NGINX, check status with:

```bash
systemctl status nginx
```

If the service is stopped, the website may not load even if DNS and firewall rules are correct.

Useful commands:

```bash
sudo systemctl start nginx
```

```bash
sudo systemctl enable nginx
```

```bash
sudo systemctl restart nginx
```

## Checking Firewall and Security Rules

A service can be running correctly and still be unreachable if traffic is blocked.

In AWS, security groups control inbound and outbound access.

For a basic NGINX web server, HTTP traffic requires:

```text
Port 80 open for HTTP
```

For SSH access, the server usually needs:

```text
Port 22 open for SSH
```

For HTTPS, the server needs:

```text
Port 443 open for HTTPS
```

Security groups should be kept as tight as possible. For example, SSH should not be left open to the whole internet unless there is a specific reason and proper controls.

## Browser vs Terminal Testing

A browser test is useful, but terminal testing gives more detail.

For example:

```bash
curl -I http://your-domain.com
```

can show whether the web server is responding.

```bash
dig +short your-domain.com
```

can show whether DNS is pointing to the expected IP address.

Together, these checks are stronger than only refreshing the browser.

## Example Troubleshooting Flow: Website Not Loading

If a website does not load, a structured flow could look like this:

1. Confirm the domain name is correct.
2. Run `dig +short domain.com`.
3. Confirm DNS returns the expected public IP.
4. Check the EC2 instance is running.
5. Confirm the security group allows port 80.
6. SSH into the server.
7. Check `systemctl status nginx`.
8. Check whether NGINX is listening on port 80.
9. Test with `curl localhost`.
10. Test the public domain again from your local machine.

This breaks the issue into smaller checks.

## Common Problems and Causes

| Problem | Possible Cause |
|---|---|
| Domain does not resolve | DNS record missing, wrong name server, propagation delay |
| Domain resolves to wrong IP | A record points to old or incorrect public IP |
| Server unreachable | EC2 instance stopped, wrong IP, routing issue |
| Browser times out | Port 80 blocked by security group or firewall |
| SSH fails | Port 22 blocked, wrong key, wrong username, instance issue |
| NGINX page not loading | NGINX stopped, wrong web root, port not listening |
| Works by IP but not domain | DNS issue |
| Works locally but not publicly | Firewall, security group, routing, or public IP issue |

## Key Takeaway

Network troubleshooting is about working logically through the path traffic takes. A good engineer does not jump straight to conclusions. They check DNS, reachability, routing, ports, security rules, services, and logs until the cause becomes clear.

## Networking in DevOps

In DevOps, troubleshooting is one of the most valuable networking skills. Production issues often appear as application failures, but the real cause may be DNS, blocked ports, routing, cloud security groups, expired certificates, or a service not listening.

A DevOps engineer needs to prove each part of the path. For a domain pointing to EC2 running NGINX, that means checking the domain, DNS record, EC2 public IP, security group, HTTP port, NGINX status, and browser response. This structured approach reduces downtime and makes fixes more reliable.
