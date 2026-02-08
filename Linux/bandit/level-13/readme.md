Bandit Level 13 → Level 14



Objective  

Extract the SSH private key for bandit14, recreate it locally with the correct permissions, and use it to authenticate into the next level.



What I Learned  

\- How to identify and extract SSH private keys from a remote system  

\- How to recreate files locally using vim  

\- How to verify my working directory with pwd  

\- How to inspect directory contents using ls  

\- How to read file contents using cat  

\- How SSH enforces strict private key permissions  

\- How to authenticate using ssh -i with a locally stored key  



Commands Used  

pwd  

ls  

cat <file>  

vim mykey  

chmod 600 mykey  

ssh -i mykey bandit14@bandit.labs.overthewire.org -p 2220  



Explanation  

The private key for bandit14 is readable from bandit13, but it can’t be used directly because SSH requires strict permissions that I couldn’t modify on the server. To bypass this, I recreated the key locally using vim, confirmed the file with pwd and ls, and inspected content with cat when needed. After applying the required permissions using chmod 600, the key met SSH’s security rules. With the file correctly secured, I authenticated into bandit14 using ssh -i on port 2220 and progressed to the next level.

