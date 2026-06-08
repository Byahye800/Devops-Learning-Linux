# Commands

This file records the key commands used for the Domain + EC2 + NGINX project.

The exact commands may vary slightly depending on the Linux distribution used on the EC2 instance. The project can be completed with Amazon Linux or Ubuntu, but the final commands should match the real build when the project is completed.

## Connect to EC2

Example SSH command:

```bash
ssh -i path/to/key.pem ec2-user@EC2_PUBLIC_IP
```

For Amazon Linux, the default username is usually:

```text
ec2-user
```

For Ubuntu, the default username is usually:

```text
ubuntu
```

## Update Packages

Amazon Linux:

```bash
sudo yum update -y
```

Ubuntu:

```bash
sudo apt update
sudo apt upgrade -y
```

## Install NGINX

Amazon Linux:

```bash
sudo yum install -y nginx
```

Ubuntu:

```bash
sudo apt install -y nginx
```

## Start NGINX

```bash
sudo systemctl start nginx
```

## Enable NGINX on Boot

```bash
sudo systemctl enable nginx
```

## Check NGINX Status

```bash
systemctl status nginx
```

or:

```bash
sudo systemctl status nginx
```

## Test NGINX Locally on the Server

```bash
curl localhost
```

Check only the response headers:

```bash
curl -I localhost
```

## Check Listening Ports

```bash
ss -tuln
```

Check specifically for HTTP on port 80:

```bash
ss -tuln | grep ':80'
```

## Check Public IP from the Server

```bash
curl ifconfig.me
```

## DNS Verification

Check whether the domain resolves:

```bash
nslookup example.com
```

Run a detailed DNS lookup:

```bash
dig example.com
```

Return only the resolved IP address:

```bash
dig +short example.com
```

Check the domain name servers:

```bash
dig NS example.com
```

## HTTP Verification

Test the domain from the terminal:

```bash
curl http://example.com
```

Check only the HTTP headers:

```bash
curl -I http://example.com
```

## NGINX Web Root

Common NGINX web root on Amazon Linux:

```text
/usr/share/nginx/html
```

Common NGINX web root on Ubuntu:

```text
/var/www/html
```

The exact path should be confirmed during the build because it can vary depending on the operating system and NGINX configuration.

## Edit the Default Page

Amazon Linux example:

```bash
sudo vim /usr/share/nginx/html/index.html
```

Ubuntu example:

```bash
sudo vim /var/www/html/index.html
```

## Test NGINX Configuration

```bash
sudo nginx -t
```

## Reload NGINX After Configuration Changes

```bash
sudo systemctl reload nginx
```

## Restart NGINX

```bash
sudo systemctl restart nginx
```

## View NGINX Logs

Access log:

```bash
sudo tail -n 50 /var/log/nginx/access.log
```

Error log:

```bash
sudo tail -n 50 /var/log/nginx/error.log
```

## Useful Project Verification Flow

A simple verification flow for this project is:

```text
1. Confirm EC2 is running.
2. Confirm NGINX is installed.
3. Confirm NGINX is active.
4. Confirm NGINX is listening on port 80.
5. Confirm the security group allows HTTP.
6. Confirm DNS points to the EC2 public IPv4 address.
7. Confirm the domain responds with curl.
8. Confirm the page loads in a browser.
```

## Notes During Real Build

This file should be updated with the exact commands used during the real project build.

Do not leave placeholder values such as `example.com` or `EC2_PUBLIC_IP` in the final project evidence. Replace them with the real project domain and verified public IP where it is safe and appropriate to show them.

## Key Takeaway

Commands are not just setup instructions. They are also verification tools. In this project, commands like `systemctl`, `ss`, `dig`, `nslookup`, and `curl` help prove whether the server, service, DNS record, and HTTP path are working correctly.

Recording commands clearly makes the project easier to repeat, audit, troubleshoot, and explain.

## Networking in DevOps

In DevOps, command-line verification is part of working safely. A web server might look correct in the cloud console, but commands prove whether the service is actually running, listening on the expected port, resolving through DNS, and responding over HTTP.

These commands help connect the practical build to real operational work: deploying services, checking connectivity, validating DNS, inspecting ports, and troubleshooting infrastructure without guessing.
