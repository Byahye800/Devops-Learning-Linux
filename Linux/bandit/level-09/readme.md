Bandit Level 9 → Level 10



Objective

Find the password hidden inside a mostly binary file by extracting human‑readable strings.



What I Learned

\- How to extract readable text from a binary file using strings

\- How to filter output using grep

\- How to identify patterns inside noisy data



Commands Used

pwd

ls

strings data.txt

strings data.txt | grep "="



Explanation

After logging into Bandit Level 9, I found a file named data.txt. The file contained mostly binary data, so I used the strings command to extract only human‑readable text. Then I filtered the output using grep "=" to locate the line that contains several '=' characters. That line contained the password for the next level.





