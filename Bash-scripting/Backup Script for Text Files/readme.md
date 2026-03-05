Text File Backup Script



A simple Bash script that backs up all `.txt` files from a user‑specified directory into a timestamped backup folder. This script demonstrates Bash fundamentals such as directory handling, user input, functions, file searching, timestamps, and counting operations.



Features



\- Prompts the user for a \*\*source directory\*\*  

\- Automatically creates a \*\*timestamped backup folder\*\*  

\- Copies all `.txt` files into the backup directory  

\- Displays the \*\*number of files backed up\*\*  

\- Wrapped inside a function for clean structure and reusability  



How It Works



1\. The script defines a function called `backup\_text\_files()`.  

2\. It prompts the user for a source directory using `read -p`.  

3\. A timestamp is generated using:  

&nbsp;  

&nbsp;  $(date +"%Y-%m-%d\_%H-%M")

&nbsp; 

4\. A backup directory is created using the timestamp.  

5\. All `.txt` files are copied using `find` + `cp`.  

6\. The script counts how many files were backed up and displays the result.



Example Output



Enter source directory: /home/user/documents

Backup directory created: backup\_2024-11-29\_14-30

Copying .txt files...

Backup complete! Files backed up: 3 (Example)



