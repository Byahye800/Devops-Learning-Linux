Bandit Level 10 → Level 11



Objective

Decode a base64-encoded password stored in data.txt.



What I Learned

\- How to identify base64-encoded text

\- How to decode base64 using the base64 -d command

\- How to combine commands using pipes



Commands Used

pwd

ls

cat data.txt

cat data.txt | base64 -d



Explanation

After logging into Bandit Level 10, I found a file named data.txt. The contents were base64-encoded. I used cat data.txt | base64 -d to decode the text. The decoded output contained the password for the next level.





