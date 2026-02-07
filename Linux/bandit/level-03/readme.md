Bandit Level 3 → Level 4



Objective

Learn how to find and read hidden files inside a directory.



What I Learned

\- How to list files in a directory

\- How to move into another directory using cd

\- How to list hidden files using ls -a

\- How Linux filenames are case-sensitive

\- How to read a hidden file using cat



Commands Used

ls

cd inhere

ls -a

cat ...Hiding-From-You



Explanation

After logging into Bandit Level 3, I listed the files in the home directory and saw a directory named "inhere". I moved into this directory using cd inhere. A normal ls did not show anything useful, so I used ls -a to display hidden files. This revealed a file named "...Hiding-From-You". My first attempts failed because I typed the filename in lowercase, but Linux filenames are case-sensitive. After using the correct name with capital letters, I ran cat ...Hiding-From-You and retrieved the password for the next level.





