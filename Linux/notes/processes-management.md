Process Management

Linux provides simple tools to view running processes, check system activity, and manage tasks. These commands help you understand what your system is doing and give you basic control over starting, stopping, and monitoring processes.

1: ps aux
Shows all running processes with details like CPU and memory usage.

Example Output:
$ ps aux
root        1  0.0  0.1 169260  1100 ?        Ss   10:00   0:02 /sbin/init
user     1324  1.2  3.5 812344 28900 ?        Sl   10:05   0:10 python3 app.py

DevOps Usage:
Used to inspect running processes, identify stuck applications, check resource usage, or find the PID of a service you need to stop or debug.

2: top
Displays real‑time system activity, including active processes and resource usage.

Example Output:
$ top
PID   USER  PR NI   VIRT   RES  SHR S %CPU %MEM TIME+      COMMAND
1324  user  20  0 812344 28900 1200 S 12.3  3.5  0:10.23   python3

DevOps Usage:
Used to monitor real‑time CPU, memory, and process activity — especially useful when diagnosing performance issues on servers.

3: htop
Interactive version of top with easier navigation and colour‑coded output (if installed).

Example Output:
$ htop
(Interactive colourful dashboard appears)

DevOps Usage:
Used for easier, more visual process monitoring — helpful during troubleshooting sessions or when analysing system load.

4: kill <PID>
Sends a signal to stop a process using its process ID.

Example Output:
$ kill 1324
(No output on success — this is normal and expected)

DevOps Usage:
Used to gracefully stop a process, such as a stuck script, runaway job, or misbehaving application.

5: kill -9 <PID>
Force‑kills a process immediately using the SIGKILL signal.

Example Output:
$ kill -9 1324
(No output on success — this is normal and expected)

DevOps Usage:
Used to force‑terminate a process that refuses to stop — common when dealing with frozen deployments, zombie processes, or hung services.

6: pkill <name>
Stops processes by matching their name instead of using a PID.

Example Output:
$ pkill python
(No output on success — this is normal and expected)

DevOps Usage:
Used to stop multiple processes by name — useful when restarting apps, clearing stuck jobs, or killing all instances of a service.

7: systemctl status <service>
Shows the current status of a system service.

Example Output:
$ systemctl status nginx
● nginx.service - A high performance web server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled)
     Active: active (running)

DevOps Usage:
Used to check whether a service is running, failed, or restarting — essential for debugging web servers, databases, and background services.

8: systemctl restart <service>
Restarts a system service to apply changes or recover from issues.

Example Output:
$ sudo systemctl restart nginx
(No output on success — this is normal and expected)

DevOps Usage:
Used to restart services after configuration changes, deployments, or when recovering from errors.








Exercise: Start → Find → Kill a Process // Challenge

Step 1 — Start a long‑running process
$ sleep 200 &
[1] 3001


Explanation:
Starts a 200‑second sleep process in the background.
Job number = 1
PID = 3001

Step 2 — Find its PID
$ ps aux | grep sleep
user   3001  0.0  0.0   5000   600 pts/0  S  10:20   0:00 sleep 200

Explanation:
Searches for the running sleep process and shows its PID.

Step 3 — Kill the process
$ kill 3001
(No output on success — this is normal and expected)

Explanation:
Sends a SIGTERM signal to stop the process.

Step 4 — Verify it stopped
$ ps aux | grep sleep


Example Output:
(no matching processes)


Explanation:
And that’s the full workflow for starting a process, finding it, and safely terminating it. These are core skills for managing Linux systems, and mastering them gives you real control over what’s running on your machine.


