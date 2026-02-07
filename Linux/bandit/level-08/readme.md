Bandit Level 8 → Level 9



Objective

Learn how to find a unique line in a file using sort and uniq.



What I Learned

\- How to list files in a directory

\- How to use sort to order lines in a file

\- How to use uniq -u to find lines that occur only once

\- How to combine commands using a pipe



Commands Used

pwd

ls

sort data.txt | uniq -u



Explanation

After logging into Bandit Level 8, I listed the files in the home directory and found a file named "data.txt". The password for the next level was stored on the only line that appears exactly once in this file. I used sort data.txt | uniq -u to first sort the lines and then filter out all lines that appear more than once. The remaining single line was the password for the next level.





