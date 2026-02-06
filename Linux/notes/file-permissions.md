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



