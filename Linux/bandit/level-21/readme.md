# Bandit Level 21 → Level 22


A program is running automatically at regular intervals from cron. Look in /etc/cron.d/ for the configuration and see what command is being executed.



What I Learned  


\- How to inspect cron jobs in /etc/cron.d  

\- How to read and understand cron syntax  

\- How cron executes scripts as different users  

\- How to follow a script to find where it stores output  



Commands Used  


cd /etc/cron.d  

ls  

cat cronjob\_bandit22  

cat /usr/bin/cronjob\_bandit22.sh  

cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv  


Explanation  

Inside /etc/cron.d, I found a cron job that runs `/usr/bin/cronjob\_bandit22.sh` as user bandit22 every minute.  

Reading the script showed that it copies the Bandit22 password into a world‑readable file located at:

`/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`

By reading this file, I obtained the password for the next level.



