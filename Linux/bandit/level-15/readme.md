\# Bandit Level 15 → Level 16



Level Goal  

Submit the current level’s password to port 30001 on localhost using SSL/TLS encryption.



What I Learned  

\- How to read the current level’s password  

\- How to make an SSL/TLS connection with openssl  

\- How to send data securely to a service  



Commands Used  

pwd

ls

cat /etc/bandit\_pass/bandit15  

openssl s\_client -connect localhost:30001  



Explanation  

I retrieved the password for bandit15, then used openssl s\_client to connect securely to port 30001 on localhost. After sending the password through the encrypted connection, the service returned the password for the next level.



