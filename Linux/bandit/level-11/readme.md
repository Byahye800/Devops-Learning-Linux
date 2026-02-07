Bandit Level 11 → Level 12



Objective

Decode a ROT13-encoded password stored in data.txt.



What I Learned

\- How to identify ROT13-encoded text

\- How to decode ROT13 using the tr command

\- How to extract readable text from encoded data



Commands Used

pwd

ls

cat data.txt

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'



Explanation

After logging into Bandit Level 11, I found a file named data.txt. The contents were encoded using ROT13. I decoded the file using cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'. The decoded output contained the password for the next level.





