\# Bandit Level 17 → Level 18



Level Goal  

Find the password for bandit18 by identifying the only line that changed between passwords.old and passwords.new.



What I Learned  

\- How to compare two files using diff  

\- How to identify modified lines  

\- How to extract a changed value from file differences  



Commands Used  

pwd  

ls  

cat passwords.old  

cat passwords.new  

diff passwords.old passwords.new  



Explanation  

I compared passwords.old and passwords.new using diff. The output showed one changed line, and the line beginning with “>” contained the password for bandit18.



