Bandit Level 4 → Level 5



Objective

Learn how to identify a human-readable file among many binary files and how to read a file whose name begins with a dash.



What I Learned

\- How to list files in a directory

\- How to move into another directory using cd

\- How to use the file command to check file types

\- How to handle filenames that start with a dash

\- How to read the correct file using cat



Commands Used

ls

cd inhere

ls

file ./\*

cat ./-file07



Explanation

After logging into Bandit Level 4, I listed the files in the home directory and saw a directory named "inhere". Inside it were multiple files with names starting with a dash. I used the file command on all files at once (file ./\*) to check their types. Most were binary data, but one file, "-file07", was identified as ASCII text. Because the filename starts with a dash, cat would treat it as an option. To fix this, I used the path prefix "./" and ran cat ./-file07, which allowed me to read the file and retrieve the password for the next level.





