Bandit Level 6 → Level 7



Objective

Learn how to locate a file owned by a specific user and group, even when many files are present.



What I Learned

\- How to use the find command with ownership filters

\- How to search by user and group

\- How to ignore permission errors using 2>/dev/null

\- How to read the correct file using cat



Commands Used

find / -type f -user bandit7 -group bandit6 2>/dev/null

cat /var/lib/dpkg/info/bandit7.password



Explanation

After logging into Bandit Level 6, I needed to find a file somewhere on the system that was owned by user bandit7 and group bandit6. I used the find command with ownership filters and redirected error messages using 2>/dev/null to avoid permission-denied spam. The command returned the path to the correct file. I then used cat on that file to retrieve the password for the next level.





