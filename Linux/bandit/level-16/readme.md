\# Bandit Level 16 → Level 17



Level Goal  

Find the SSL-enabled service running on a port between 31000 and 32000, submit the bandit16 password, and use the returned RSA key to log into bandit17.



What I Learned  

\- How to scan ports with version detection using nmap -sV  

\- How to identify which service uses SSL/TLS  

\- How to connect to SSL services using openssl s\_client  

\- How to handle RSA private keys and set correct permissions  

\- How to authenticate with SSH using a private key  



Commands Used  

pwd  

ls  

cat /etc/bandit\_pass/bandit16  

nmap -sV -p 31000-32000 localhost  

openssl s\_client -connect localhost:31790 -ign\_eof  

mkdir ~/myspace  

nano sshkey17.private  

chmod 600 sshkey17.private  

ssh -i sshkey17.private bandit17@bandit.labs.overthewire.org -p 2220  



Explanation  

I scanned ports 31000–32000 using nmap -sV to detect which one was running an SSL service. After finding the SSL-enabled port (31790), I connected using openssl s\_client and submitted the bandit16 password. The server returned an RSA private key, which I saved locally with correct permissions and used to SSH into bandit17.

