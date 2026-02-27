\# Bash Arithmetic Calculator



A simple, interactive Bash script that performs basic arithmetic operations on two user‑provided numbers. This script displays Bash fundamentals such as variables, user input, functions, arithmetic expansion, and conditional logic.



---



Features



\- Prompts the user for two numbers  

\- Performs: - Addition - Subtraction - Multiplication - Division 
  (with safe handling for division by zero)

\- Displays all results in a clean, readable format

\- Wrapped inside a function for better structure and reusability



---



How It Works



1\. The script defines a function called calculate().

2\. It asks the user to enter two numbers using read -p.

3\. Arithmetic is performed using Bash’s built‑in arithmetic expansion:  

&nbsp;  $(( expression ))

