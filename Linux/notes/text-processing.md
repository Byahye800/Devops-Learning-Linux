Text processing 



Linux provides powerful tools for searching, filtering, transforming, and analysing text. These commands are essential when working with logs, configuration files, automation scripts, and large datasets. Mastering text processing makes it easier to extract information, troubleshoot issues, and build efficient DevOps workflows





1: grep = Searches for lines matching a pattern inside a file.



Example Output:

$ grep "ERROR" app.log

\[ERROR] Failed to connect to database

\[ERROR] Timeout while waiting for response



DevOps Usage:

Used to filter logs, find errors quickly, extract specific values, and debug failing services or deployments.



2: awk = Extracts and processes specific fields or columns from text.



Example Output:

$ awk '{print $1, $3}' access.log

192.168.1.10 200

192.168.1.11 404



DevOps Usage:

Used to parse logs, extract metrics, analyse API responses, and format data for automation or monitoring scripts.



3: sed = Performs find/replace operations or edits text in files.



Example Output:

$ sed 's/production/staging/' config.yaml

environment: staging



DevOps Usage:

Used to update config files automatically, replace environment variables in templates, or clean log output in CI/CD pipelines.



4: sort = Sorts lines alphabetically or numerically.



Example Output:

$ sort users.txt

alice

bakar

john

zara



DevOps Usage:

Used to organise log output, sort IP lists, prepare data for reporting, or clean automation results.



5: uniq = Removes duplicate lines (usually after sorting).



Example Output:

$ sort errors.log | uniq

DatabaseError

TimeoutError

ValidationError



DevOps Usage:

Used to identify unique errors, count repeated log entries, or clean datasets before processing.



6: tr = Translates, replaces, or deletes characters.



Example Output:

$ echo "hello world" | tr a-z A-Z

HELLO WORLD



DevOps Usage:

Used to clean text, convert case, remove unwanted characters, or format data for scripts and pipelines.



7: join = Combines lines from two files based on a matching field.



Example Output:

$ join users.txt roles.txt

alice admin

matt devops

john tester



DevOps Usage:

Used to merge datasets, correlate logs from different sources, or combine configuration values during automation.







