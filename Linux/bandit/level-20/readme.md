# Bandit Level 20 → Level 21


Objective

Use the suconnect program to open a listening port, send the Bandit20 password to it, and receive the password for the next level.

What I Learned  

\- How to open a listening port using nc  

\- How suconnect validates passwords over a TCP connection  

\- How to pass data between two terminals  

\- How to extract the next level’s password from listener output  


Commands Used  

pwd  

ls  

cat /etc/bandit\_pass/bandit20  

nc -l -p 4444  

./suconnect 4444  


Explanation  

I opened a listening port using `nc -l -p 4444` and attempted to connect to it using `./suconnect 4444`.  
When the correct Bandit20 password was sent to the listener, suconnect returned the password for the next level.  






