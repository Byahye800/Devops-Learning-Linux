File Permissions

Linux uses a clear permission model to control who can read, write, or execute files and directories. Understanding these basics gives you better control over your system and helps you use commands like chmod, chown, and chgrp effectively.



1: ls -l

Shows permissions, ownership, and timestamps in long listing format.



Example Output:

$ ls -l

-rw-r--r-- 1 user user 120 Feb 4 10:21 config.yaml

drwxr-xr-x 2 user user 4096 Feb 4 10:22 scripts



DevOps Usage:

Used to inspect file permissions, ownership, and directory structures before deployments, troubleshooting, or automation tasks.



2: chmod

Changes permission settings using numeric or symbolic notation.



Example Output:

$ chmod 644 config.yaml

(No output on success — this is normal and expected)

$ ls -l config.yaml

-rw-r--r-- 1 user user 120 Feb 4 10:21 config.yaml



DevOps Usage:

Used to fix permission issues on config files, scripts, SSH keys, or deployment artifacts.



3: chmod u+x

Adds execute permission for the file owner.



Example Output:

$ chmod u+x deploy.sh

(No output on success — this is normal and expected)

$ ls -l deploy.sh

-rwxr--r-- 1 user user 89 Feb 4 10:25 deploy.sh



DevOps Usage:

Used to make scripts executable before running automation tasks, CI/CD jobs, or deployment scripts.



4: chown <user>:<group> <file>

Changes the user and group that own a file.



Example Output:

$ sudo chown ubuntu:ubuntu app.log

(No output on success — this is normal and expected)

$ ls -l app.log

-rw-r--r-- 1 ubuntu ubuntu 5321 Feb 4 10:30 app.log



DevOps Usage:

Used when services (Nginx, Docker, Jenkins, etc.) require files to be owned by specific system users.



5: chgrp <group> <file>

Updates the group ownership of a file.



Example Output:

$ sudo chgrp developers script.sh

(No output on success — this is normal and expected)

$ ls -l script.sh

-rwxr--r-- 1 user developers 120 Feb 4 10:32 script.sh



DevOps Usage:

Used to give a team or service group access to shared scripts, logs, or configuration directories.



6: stat <file>

Displays detailed file information, including permission bits.



Example Output:

$ stat config.yaml

&nbsp; File: config.yaml

&nbsp; Size: 120         Blocks: 8          IO Block: 4096 regular file

Device: 802h/2050d  Inode: 1234567     Links: 1

Access: (0644/-rw-r--r--)  Uid: (1000/user)   Gid: (1000/user)

Access: 2025-02-04 10:21:00.000000000

Modify: 2025-02-04 10:21:00.000000000

Change: 2025-02-04 10:21:00.000000000



DevOps Usage:

Used when diagnosing permission issues, checking inode details, or verifying timestamps during debugging.



7: chmod -R

Applies permission changes to a directory and all items inside it.



Example Output:

$ chmod -R 755 scripts/

(No output on success — this is normal and expected)

$ ls -l scripts/

-rwxr-xr-x 1 user user 120 Feb 4 10:40 build.sh

-rwxr-xr-x 1 user user 98  Feb 4 10:40 deploy.sh



DevOps Usage:

Used to apply permissions across entire directories — common when preparing web server folders, deployment directories, or shared project structures.



Permission Basics



Permission Types

\- r = read

\- w = write

\- x = execute

Permission Scopes

\- u = user (owner)

\- g = group

\- o = others

Numeric (Octal) Permissions

\- 7 = rwx

\- 6 = rw-

\- 5 = r-x

\- 4 = r--

Task 3: Permissions & Ownership // Challenge

Explanation 

In this task, I demonstrated how to create a shell script, execute it, modify its ownership, and adjust file permissions using standard Linux commands. Below is a detailed explanation of each step and what it accomplished.

1. Creating a Shell Script (hello.sh)
I began by creating a new script file using output redirection:
echo "#!/bin/bash echo 'Hello Devops'" > hello.sh 
This command writes two lines into hello.sh:
•	#!/bin/bash specifies that the script should run using the Bash shell.
•	echo 'Hello Devops' prints a message when the script is executed.
Using > ensures the file is created (or overwritten if it already exists).
I verified the file was created with:
ls -l hello.sh 
This showed the file existed with default permissions (rw-r--r--) and was owned by my user account.

2. Making the Script Executable
By default, the script did not have execute permissions. I added them using:
chmod +x hello.sh 
This allowed me to run the script directly from the terminal.

3. Running the Script
I executed the script using:
./hello.sh 
The output confirmed the script worked correctly:
Hello Devops 

4. Changing File Ownership to Root
Next, I practiced modifying file ownership using chown. Only the root user can change ownership, so I used sudo:
sudo chown root:root hello.sh 
After this, the file was owned by the root user and root group. I confirmed this with:
ls -l hello.sh 
The permissions stayed the same, but the owner changed to root.

5. Restoring Ownership Back to Myself
To regain control of the file, I changed the ownership back:
sudo chown byahy:byahy hello.sh 
This returned the file to my user account, which I verified again with ls -l.

6. Creating an Empty File (myfile.txt)
I created a new empty file using:
touch myfile.txt 
This produced a zero byte file with default permissions (rw-r--r--).

7. Modifying Permissions on myfile.txt
Finally, I practiced adjusting permissions using symbolic notation:
chmod g-r myfile.txt 
This removed the read permission from the group. The updated permissions became:
rw----r-- 

Meaning:
•	User: read + write
•	Group: no permissions
•	Others: read
This could have also been achieved by applying the Octal method with the command (chmod 604 myfile.txt)
This demonstrated how to selectively remove access for specific permission classes.
Conclusion
Through this sequence of commands, I successfully demonstrated:
•	Creating and editing files
•	Making scripts executable
•	Running shell scripts
•	Changing file ownership using chown
•	Adjusting permissions using chmod
•	Understanding how Linux represents file permissions and ownership
Each step shows practical knowledge of Linux file management essential skills for system administration and DevOps workflows.




