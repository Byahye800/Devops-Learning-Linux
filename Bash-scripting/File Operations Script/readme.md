Bash File Operations Script

A simple Bash script that automates creating a directory, generating a file, writing text with the current date, and displaying the file contents. This script demonstrates Bash essentials such as directory management, file creation, command substitution, and output redirection.



Features

\- Creates a directory named bash\_demo

\- Navigates into the directory

\- Generates a file called demo.txt

\- Writes a message containing the current date

\- Displays the file contents in a clean, readable format



How It Works

\- The script creates a directory using mkdir -p to avoid errors if it already exists.

\- It moves into the directory with cd.

\- A line of text is written to demo.txt using echo and command substitution:

\- $(date +%Y-%m-%d) inserts the current date.

\- The file contents are displayed using cat, with a label printed beforehand for clarity.



Example Output

Directory 'bash\_demo' created.

File 'demo.txt' created.

File contents: This file was created by a Bash script on 2026-03-04





