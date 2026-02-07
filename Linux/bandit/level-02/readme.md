Bandit Level 2 → Level 3



Objective

Learn how to read a file whose name contains spaces and starts with dashes.



What I Learned

\- How to list files in a directory

\- How Linux treats filenames that start with --

\- How to read files with spaces in their names using quotes

\- How to use ./ to force the shell to treat something as a file



Commands Used

ls

cat "./--spaces in this filename--"



Explanation

After logging into Bandit Level 2, I listed the files in the home directory and found a file named "--spaces in this filename--". Because the filename starts with two dashes, cat treated it as an option and returned an error. To fix this, I used the path prefix "./" which forces the shell to treat it as a file in the current directory. Using cat "./--spaces in this filename--" allowed me to read the file and retrieve the password for the next level.





