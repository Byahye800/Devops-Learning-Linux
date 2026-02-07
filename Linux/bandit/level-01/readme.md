Bandit Level 1 → Level 2



Objective

Learn how to find files with unusual names and read their contents.



What I Learned

\- How to list all files including hidden ones

\- How to handle files with special characters in their names

\- How to use quotes to access files with spaces or symbols



Commands Used

ls -a

cat ./-



Explanation

After logging into the Bandit Level 1 server, I listed all files including hidden ones. I found a file named "-" which is a special filename. To read it safely, I used cat with a path prefix (./-) so the shell treats it as a file instead of an option. The file contained the password for the next level.





