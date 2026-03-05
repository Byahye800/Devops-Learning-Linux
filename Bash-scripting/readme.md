Bash Scripting Challenges 



This folder is a small but meaningful snapshot of my Bash scripting journey — the point where the command line stopped feeling intimidating and started feeling like a tool I could actually control.

Each script represents a practical skill I picked up along the way: taking user input, working with files and directories, checking permissions, and automating simple tasks that would normally take several manual steps.

What makes this collection important to me is that it isn’t just theory.

These scripts reflect the real habits you need in DevOps: thinking clearly, breaking problems down, writing safe commands, and understanding how Linux behaves under the hood.

It’s a foundation I’m building, one script at a time and it’s already shaping the way I approach automation and system tasks.



Script Summaries



1\. Basic Arithmetic Calculator (`calculator.sh`)\*\*

A simple interactive calculator that:

\- Prompts the user for two numbers  

\- Performs addition, subtraction, multiplication, and division  

\- Handles division‑by‑zero safely  

\- Displays all results in a clean, readable format  



\*\*Key concept:\*\* user input, arithmetic expansion, conditional checks.



2\. File Operations Script (`file\_ops.sh`)\*\*

Automates basic filesystem tasks:

\- Creates a directory named `bash\_demo`  

\- Navigates into it  

\- Creates a file `demo.txt`  

\- Writes text including the current date  

\- Displays the file contents  



\*\*Key concept:\*\* directory management, file creation, command chaining.



3\. File Checker with Permissions (`file\_checker.sh`)\*\*

A script that:

\- Prompts the user for a filename  

\- Checks if the file exists  

\- Verifies read, write, and execute permissions   



\*\*Key concept:\*\* file testing (`-r`, `-w`, `-x`), conditional branching.



4\. Text File Backup Script (`backup.sh`)\*\*

A lightweight backup utility that:

\- Prompts for a source directory  

\- Creates a timestamped backup folder  

\- Copies all `.txt` files into it  

\- Displays the number of files backed up  



\*\*Key concept:\*\* automation, wildcard matching, timestamps, safe copying.



Key Learnings



\- Mastery of user input handling\*\* using `read`, validation, and conditional logic.  

\- Understanding filesystem operations\*\* such as creating directories, writing files, and navigating paths.  

\- Working with permissions\*\* and learning how Linux enforces read/write/execute rules.  

\- Automation mindset\*\* — using Bash to eliminate repetitive manual tasks.  

\- Safe scripting practices\*\*, including error handling and checking for edge cases (e.g., division by zero, missing files).



One Challenge I Overcome



1\. Learning to Handle User Input the Right Way

At first, I underestimated how unpredictable user input can be.

Someone might enter letters instead of numbers or accidentally try to divide by zero.

Figuring out how to validate input properly taught me to think ahead and write scripts that protect themselves — a mindset that’s essential in DevOps.



2\. Making Sense of Linux Permissions

Understanding file permissions wasn’t just about using , , and .

It was about realising why Linux enforces access the way it does.

Once it clicked, checking permissions felt less like a chore and more like understanding the rules of the system I’m working with.



3\. Writing Scripts That Work Anywhere, Not Just on My Machine

Early on, I hard‑coded paths without thinking about portability.

Fixing that meant learning to accept user input, validate directories, and build scripts that adapt to different environments.

It was a small shift, but it made my scripts feel more “real world.”



4\. Building a Backup Script That Doesn’t Break Under Pressure

The backup script taught me a lot about edge cases.

What if the directory doesn’t exist?

What if there are no  files?

What if the backup folder already exists?

Handling all of that made the script more reliable — and gave me a better appreciation for automation that’s safe, predictable, and calm under pressure.



Why Bash Matters in DevOps



Bash is one of those skills that quietly transforms the way you work.

Once you start using it, you realise how much smoother everything becomes — from simple tasks to full automation.

For anyone stepping into DevOps, Bash isn’t just another tool; it’s the language of the systems you’re trying to understand and control.

This folder represents the early steps of learning that language.

Every script here — whether it’s checking permissions, creating backups, or handling user input — reflects the kind of real tasks you’ll automate on Linux servers, cloud environments, and CI/CD pipelines.

Bash matters in DevOps because it helps you:

\- Automate everyday tasks so you spend less time repeating commands and more time solving real problems.

\- Interact directly with servers in a way that’s fast, reliable, and easy to reproduce.

\- Glue tools together in pipelines, where Bash often acts as the “bridge” between different stages.

\- Work confidently across AWS, Docker, Kubernetes, and Linux, all of which rely heavily on shell scripting behind the scenes.

Learning Bash early gives you a huge advantage — it builds confidence, sharpens your thinking, and makes every other DevOps tool feel more approachable.

It’s a small skill with a big impact, and this folder is where that journey begins.





