
# Bandit 09 - 10

[Challenge](https://overthewire.org/wargames/bandit/bandit10.html)

---

## What I Had to Do
The password is stored in file `data.txt` in which one of the few human readable strings that starts with several `=` have the password.

---

## How I Did It

First i listed `data.txt` in the current directory using `ls` command then i run:
```bash
strings data.txt
```
It prints all human readable string in the file, but we need that one which starts with several `=` , so we need to search in file using ``grep`` command with `Regular Expressions` :
```bash
strings data.txt | grep "^="
```
It list all the strings that begins with `=` sign and there you find your password to log in onto bandit10, just enter this command and enter the password and you've completed this challenge:
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

Learn and Enjoy!

---

## What I Learned
- ``strings command`` - prints human readable string from the file.
- ``regex`` - regular expressions such as ^,$, etc.
- `wildcards` - used in commands like find,sed etc. such as * , ?, [ ], 

---

## Password
`[REDACTED]`


---

## Helpful Reading Material
- `man strings` - to learn more about strings command
- [regex](https://data-flair.training/blogs/regular-expression-in-linux/) - to learn about regular expressions used in grep 
- [wildcards](https://medium.com/@saikiransarvepalli/mastering-wildcards-in-linux-89206f2d595e) - to learn about wildcards and how they are different from regex
