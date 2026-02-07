Bandit Level 12 → Level 13



Objective

Extract the password from a file that has been repeatedly compressed and encoded inside data.txt.



What I Learned

\- How to reverse a hexdump using xxd

\- How to identify file types using the file command

\- How to decompress gzip, bzip2, and tar files

\- How to work through multiple layers of compressed data



Commands Used

pwd

ls

cat data.txt

xxd -r data.txt > data

file data

mv data data.gz

gzip -d data.gz

file data

mv data data.bz2

bzip2 -d data.bz2

file data

mv data data.tar

tar -xf data.tar

file <extracted file>

cat <final file>



Explanation

After logging into Bandit Level 12, I found that data.txt contained a hexdump. I reversed it using xxd -r and saved the output as data. Using the file command showed that the file changed formats after each extraction. I renamed the file to match its format and decompressed it step by step using gzip, bzip2, and tar. After several rounds of extraction, the final file revealed the password for the next level.

