Networking Commands



Linux provides several simple tools to check connectivity, view network details, and troubleshoot basic network issues. Learning these commands helps you understand how your system communicates on the network and makes it easier to diagnose connection problems.





1: ip a = Shows network interfaces, assigned IP addresses, and link status.



Example Output:

$ ip a 2: eth0: mtu 1500 inet 192.168.1.45/24 brd 192.168.1.255 scope global eth0 



DevOps Usage:

Used to check IP addresses, interface status, and connectivity issues when debugging servers, containers, or cloud instances.



2: ifconfig = Displays interface information on older systems (legacy alternative to ip).



Example Output:

$ ifconfig eth0: flags=4163 inet 192.168.1.45 netmask 255.255.255.0 



DevOps Usage:

Used on older systems or minimal Linux images to quickly view interface information when ip is not available.



3: ping = Tests network connectivity and measures response time.



Example Output:

$ ping google.com 64 bytes from 142.250.187.78: icmp\_seq=1 ttl=115 time=12.3 ms 



DevOps Usage:

Used to test connectivity between servers, check DNS resolution, or verify if a service is reachable.



4: curl = Retrieves data from a web address; useful for testing APIs or endpoints.



Example Output:

$ curl https://api.example.com/health {"status":"ok","uptime":"1023s"} 



DevOps Usage:

Used to test APIs, check service health endpoints, download files, or debug HTTP issues.



5: wget = Downloads files from the internet using HTTP, HTTPS, or FTP.



Example Output:

$ wget https://example.com/file.zip Saving to: ‘file.zip’ 



DevOps Usage:

Used to download packages, scripts, or configuration files during provisioning or automation.



6: nslookup = Looks up DNS information to help diagnose name resolution issues.



Example Output:

$ nslookup google.com Server: 8.8.8.8 Address: 8.8.8.8#53 Name: google.com Address: 142.250.187.78 



DevOps Usage:

Used to diagnose DNS issues, verify domain resolution, or check if internal services resolve correctly.



7: ss -tulnp = Shows active network connections, listening ports, and associated processes.



Example Output:

$ ss -tulnp Netid State Local Address:Port PID/Program name tcp LISTEN 0.0.0.0:22 1023/sshd tcp LISTEN 127.0.0.1:5432 1500/postgres 



DevOps Usage:

Used to check which services are listening on which ports — essential for debugging firewalls, containers, and microservices.



8: traceroute = Displays the path packets take to reach a destination.



Example Output:

$ traceroute google.com 1 192.168.1.1 1.123 ms 2 10.10.0.1 5.234 ms 3 142.250.187.78 12.345 ms 



DevOps Usage:

Used to diagnose routing issues, latency problems, or network hops between servers and external services.





