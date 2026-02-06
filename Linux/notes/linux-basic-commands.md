Navigation Commands
Linux navigation commands help you move around the filesystem, understand where you are, and access the directories you need. These commands form the foundation of working in the terminal and are used constantly in DevOps, scripting, troubleshooting, and system administration.

1: pwd
Shows the full path of the directory you are currently in.

Example Output:
$ pwd
/home/ubuntu/projects


DevOps Usage:
Used when verifying your working directory before running scripts, applying configs, or executing destructive commands like rm or mv.

2: ls
Lists files and directories in the current location.

Example Output:
$ ls
app.py logs config.yaml scripts


DevOps Usage:
Used constantly to inspect directories, check deployments, verify config files, and confirm whether automation scripts exist.

3: ls -lah
Lists files with details, including hidden files, in human‑readable format.

Example Output:
$ ls -lah
total 20K
drwxr-xr-x 3 user user 4.0K Feb 4 10:21 .
drwxr-xr-x 5 user user 4.0K Feb 4 10:20 ..
-rw-r--r-- 1 user user 1.2K Feb 4 10:21 config.yaml


DevOps Usage:
Used to check file permissions, ownership, and sizes — especially before deployments or troubleshooting permission issues.

4: cd <directory>
Changes the current directory.

Example Output:
$ cd /var/log
(No output on success — this is normal and expected)

DevOps Usage:
Used to navigate into log directories, project folders, or system paths during debugging or configuration work.

5: cd ..
Moves up one directory level.

Example Output:
$ cd ..
(No output on success — this is normal and expected)

DevOps Usage:
Used to quickly move up the directory tree when navigating infrastructure folders or repo structures.

6: cd ~
Returns to your home directory.

Example Output:
$ cd ~
$ pwd
/home/ubuntu
(cd itself produces no output — pwd confirms the change)

DevOps Usage:
Used to return to your home directory when resetting your working environment or accessing SSH keys.

File and Directory Operations

1: touch <file>
Creates an empty file.

Example Output:
$ touch notes.txt
(No output on success — this is normal and expected)
$ ls
notes.txt

DevOps Usage:
Used to create placeholder files, logs, or config files during automation or testing.

2: mkdir <folder>
Creates a new directory.

Example Output:
$ mkdir backups
(No output on success — this is normal and expected)

DevOps Usage:
Used to create directory structures for deployments, logs, backups, or scripts.

3: mkdir -p <path>
Creates nested directories without errors if they already exist.

Example Output:
$ mkdir -p /opt/app/releases/v1
(No output on success — this is normal and expected)

DevOps Usage:
Used when building nested folder structures in CI/CD pipelines or provisioning servers.

4: cp <source> <destination>
Copies a file.

Example Output:
$ cp config.yaml config.yaml.bak
(No output on success — this is normal and expected)

DevOps Usage:
Used to back up configs before editing, duplicate scripts, or copy deployment files.

5: mv <source> <destination>
Moves or renames a file.

Example Output:
$ mv app.log old-app.log
(No output on success — this is normal and expected)

DevOps Usage:
Used to rename logs, move build artifacts, or reorganise project files.

6: rm <file>
Deletes a file permanently.

Example Output:
$ rm old-app.log
(No output on success — this is normal and expected)

DevOps Usage:
Used to remove old logs, temporary files, or outdated build artifacts.
(Used carefully — DevOps engineers avoid accidental deletions.)

Viewing Files

1: cat <file>
Displays the entire contents of a file.

Example Output:
$ cat config.yaml
port: 8080
environment: production


DevOps Usage:
Used to quickly view config files, environment variables, or logs.

2: less <file>
Opens a scrollable viewer for large files.

Example Output:
$ less /var/log/syslog

DevOps Usage:
Used to inspect large log files without loading everything at once.

3: head -n 20 <file>
Shows the first 20 lines of a file.

Example Output:
$ head -n 20 app.log
[INFO] Starting service...
[INFO] Loading config...

DevOps Usage:
Used to check the beginning of logs, config files, or scripts.

4: tail -n 20 <file>
Shows the last 20 lines of a file.

Example Output:
$ tail -n 20 app.log
[INFO] Service started successfully

DevOps Usage:
Used constantly to check the latest log entries during deployments or debugging.

5: nl <file>
Displays a file with line numbers added automatically.

Example Output:
$ nl script.sh
1  #!/bin/bash
2  echo "Deploying..."

DevOps Usage:
Used when debugging scripts and referencing specific line numbers.

6: more <file>
Shows a file one page at a time, similar to less but more basic.

Example Output:
$ more README.md

DevOps Usage:
Used to view long files on systems with minimal tools installed.


