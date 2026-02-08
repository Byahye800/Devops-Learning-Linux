\# Bandit Level 19 → Level 20



Level Goal  

Use the setuid binary bandit20-do to execute a command as bandit20 and read the password for the next level.



What I Learned  

\- How setuid binaries work  

\- How to run commands as another user  

\- How to use a helper binary to access protected files  



Commands Used  

pwd  

ls  

file bandit20-do  

./bandit20-do  

./bandit20-do cat /etc/bandit\_pass/bandit20  

ssh bandit20@bandit.labs.overthewire.org -p 2220  



Explanation  

The bandit20-do binary runs commands as bandit20. By executing `./bandit20-do cat /etc/bandit\_pass/bandit20`, I retrieved the password for bandit20 and used it to log into the next level.

