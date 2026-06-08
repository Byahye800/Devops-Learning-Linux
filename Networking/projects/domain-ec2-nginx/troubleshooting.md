# Troubleshooting

This file documents troubleshooting checks for the Domain + EC2 + NGINX project.

The purpose is to show a structured investigation process rather than guessing when something does not work. In a real environment, a website might fail to load for several different reasons, so the goal is to test each part of the path carefully.

## Troubleshooting Approach

For this project, the main question is:

```text
Can a user reach the NGINX web page through the domain name?
```

If the answer is no, the issue could be in several places:

```text
Browser
DNS
Domain record
EC2 public IP
Security group
Server firewall
NGINX service
Web root
```

The best approach is to move through the flow step by step instead of changing random settings.

## Basic Flow

```text
1. Confirm the domain name is correct.
2. Check DNS resolution.
3. Confirm DNS returns the EC2 public IPv4 address.
4. Confirm the EC2 instance is running.
5. Confirm the security group allows HTTP on port 80.
6. Connect to the server using SSH.
7. Confirm NGINX is installed and running.
8. Confirm NGINX is listening on port 80.
9. Test locally with curl.
10. Test externally with curl.
11. Test in the browser.
```

This process helps narrow the issue down logically. If DNS is wrong, there is no point restarting NGINX. If NGINX is not running, there is no point changing the domain record. Each check should prove or rule out one part of the path.

## Issue: Domain Does Not Resolve

Possible causes:

- DNS record has not been created.
- DNS record was created under the wrong zone.
- Name servers are not configured correctly.
- DNS propagation is still in progress.
- The domain name was typed incorrectly.

Checks:

```bash
dig example.com
```

```bash
dig +short example.com
```

```bash
nslookup example.com
```

Expected result:

```text
The domain should return the EC2 public IPv4 address.
```

If the domain does not return an IP address, the problem is likely with DNS configuration, name servers, or propagation.

## Issue: Domain Resolves to the Wrong IP

Possible causes:

- The A record points to an old EC2 public IP.
- The EC2 instance was stopped and restarted, changing the public IP.
- The wrong DNS record was edited.
- Browser or DNS cache still has the old value.

Checks:

```bash
dig +short example.com
```

Compare the result with the EC2 public IPv4 address shown in AWS.

Fix:

```text
Update the DNS A record so it points to the correct EC2 public IPv4 address.
```

This is a common issue because EC2 public IP addresses can change if an instance is stopped and started again, unless an Elastic IP is used.

## Issue: Browser Times Out

Possible causes:

- The EC2 security group does not allow HTTP on port 80.
- NGINX is not running.
- The EC2 instance is stopped.
- A network ACL or routing rule is blocking traffic.
- DNS points to the wrong public IP.

Checks:

```bash
curl -I http://example.com
```

```bash
systemctl status nginx
```

```bash
ss -tuln | grep ':80'
```

Fix areas:

- Start or restart NGINX.
- Allow port 80 in the EC2 security group.
- Confirm the EC2 instance is running.
- Confirm DNS points to the right public IP.

If the browser times out, it usually means the request is not successfully reaching a working web service.

## Issue: SSH Does Not Work

Possible causes:

- Wrong SSH key.
- Wrong username.
- Security group does not allow port 22.
- Instance is stopped.
- Connecting to the wrong public IP.

Common usernames:

```text
Amazon Linux: ec2-user
Ubuntu: ubuntu
```

Example SSH command:

```bash
ssh -i path/to/key.pem ec2-user@EC2_PUBLIC_IP
```

If SSH fails, check the key, username, public IP address, and inbound security group rule for port 22.

## Issue: NGINX Is Not Running

Check service status:

```bash
systemctl status nginx
```

Start NGINX:

```bash
sudo systemctl start nginx
```

Enable NGINX on boot:

```bash
sudo systemctl enable nginx
```

Restart NGINX:

```bash
sudo systemctl restart nginx
```

A domain and DNS record can be configured correctly, but the website still will not load if the web server process is not running.

## Issue: NGINX Running but Page Not Loading

Possible causes:

- Port 80 is blocked.
- Wrong web root is being edited.
- DNS points to the wrong server.
- NGINX configuration has an error.
- Browser cache is showing an old result.

Checks:

```bash
curl localhost
```

```bash
curl -I localhost
```

```bash
sudo tail -n 50 /var/log/nginx/error.log
```

If `curl localhost` works on the server, NGINX is responding locally. If the site still does not load publicly, the issue is likely outside the NGINX service itself.

## Issue: Works by IP but Not Domain

If the site works using the EC2 public IP but not the domain, the problem is likely DNS-related.

Checks:

```bash
dig +short example.com
```

```bash
nslookup example.com
```

Possible fixes:

- Correct the A record.
- Wait for DNS propagation.
- Confirm the domain uses the correct name servers.
- Clear local DNS or browser cache.

This is a useful test because it separates the web server from the domain configuration.

## Issue: Works Locally but Not Publicly

If `curl localhost` works on the server but the site does not load from your browser, the web server is probably running but external access is blocked.

Likely causes:

- Security group does not allow port 80.
- Server firewall blocks HTTP.
- Wrong public IP.
- DNS record points somewhere else.

Checks:

```bash
curl localhost
```

```bash
curl -I http://example.com
```

```bash
dig +short example.com
```

This helps confirm whether the issue is local to the server, external network access, or DNS.

## Issue: Custom Page Does Not Show

Possible causes:

- The wrong web root was edited.
- NGINX is serving a different default file.
- The browser cached the old page.
- NGINX was not restarted or reloaded after changes.

Checks:

```bash
curl localhost
```

```bash
sudo nginx -t
```

```bash
sudo systemctl reload nginx
```

If the default NGINX page still appears after editing, confirm the correct file path for the active NGINX site.

## Notes During Real Build

When the project is completed, this file should be updated with any real issues encountered and how they were solved.

Do not invent problems. If the build works smoothly, this file should remain as a structured troubleshooting guide and clearly separate planned troubleshooting checks from actual issues encountered.

## Key Takeaway

Troubleshooting should follow the path that traffic takes. For this project, that means checking the domain, DNS record, EC2 public IP, security group, HTTP port, NGINX service, and browser response.

A clear troubleshooting process makes the project easier to debug, easier to explain, and more professional to present.

## Networking in DevOps

Troubleshooting is a major part of DevOps work. When a service is unreachable, the cause could be DNS, routing, firewall rules, blocked ports, certificates, server configuration, or the service itself.

This project creates a simple but realistic troubleshooting path. A DevOps engineer should be able to follow the request from domain name to DNS record, from DNS record to public IP, from public IP to security group, and from the security group to the NGINX service running on the server.
