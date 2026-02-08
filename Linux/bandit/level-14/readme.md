\# Bandit Level 14 → Level 15



Objective  

Submit the current level’s password to port 30000 on localhost to retrieve the next password.



What I Learned  

\- Where Bandit stores each level’s password  

\- How to read the current level’s password  

\- How to connect to a port on localhost  

\- How to send data to a service using nc  

\- Basic understanding of ports and localhost  



Commands Used  

pwd  

ls  

cat /etc/bandit\_pass/bandit14  

nc localhost 30000  



Explanation  

After logging into Bandit Level 14, I needed to retrieve the current level’s password. Bandit stores all passwords in /etc/bandit\_pass/, so I read the file for bandit14. The instructions said to submit this password to port 30000 on localhost. I used nc localhost 30000 to connect, then pasted the password. The service responded with the password for the next level.



