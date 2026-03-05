File Permission Checker



A simple, interactive Bash script that checks whether a file exists and displays its read, write, and execute permissions. This script demonstrates Bash fundamentals such as user input, functions, file test operators, and conditional logic.



Features



\- Prompts the user for a filename  

\- Checks whether the file exists  

\- Displays:  

&nbsp; - Read permission  

&nbsp; - Write permission  

&nbsp; - Execute permission  

\- Clean output for readability  

\- Wrapped inside a function for better structure and reusability  



How It Works



1\. The script defines a function called `check\_file\_permissions()`.  

2\. It asks the user to enter a filename using `read -p`.  

3\. File tests are performed using Bash’s built‑in operators:  

&nbsp;  - `-e` → file exists  

&nbsp;  - `-r` → readable  

&nbsp;  - `-w` → writable  

&nbsp;  - `-x` → executable  

4\. The script prints clear messages showing which permissions the file has.



Example Output



Enter filename to check: /etc/passwd

File '/etc/passwd' exists.

File is readable

File is not writable

File is not executable

