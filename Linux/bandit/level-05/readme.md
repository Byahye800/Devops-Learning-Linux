Bandit Level 5 → Level 6



Objective

Learn how to locate a file based on specific properties such as size, ownership, and permissions.



What I Learned

\- How to list directory contents

\- How to use the find command with filters

\- How to search by size, user, group, and file type

\- How to read the correct file using cat



Commands Used

ls

cd inhere

find . -type f -size 1033c

cat ./maybehere07/.file2



Explanation

After logging into Bandit Level 5, I listed the files in the home directory and saw a directory named "inhere". Inside it were many files with random names. I used the find command with multiple conditions to locate the correct file: it had to be a regular file, exactly 1033 bytes in size and owned by bandit6. The command find . -type f -size 1033c returned the correct filename. I then used cat on that file to retrieve the password for the next level.

