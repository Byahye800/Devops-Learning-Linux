\# Bandit Level 18 → Level 19



Level Goal  

The .bashrc for bandit18 logs you out immediately. You must bypass it by running a command directly during SSH login.



What I Learned  

\- How to bypass .bashrc using a non-interactive SSH command  

\- How SSH executes commands before loading the user’s shell  

\- How to retrieve a file without starting an interactive session  



Commands Used  

ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme  

ssh bandit19@bandit.labs.overthewire.org -p 2220  



Explanation  

Logging in normally triggers .bashrc, which forces an immediate logout. By running `cat readme` directly in the SSH command, I bypassed the interactive shell and printed the password for bandit19. I then used that password to log into the next level.



