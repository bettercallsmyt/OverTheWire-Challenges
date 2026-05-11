
# Bandit 05 -06

[Challenge](https://overthewire.org/wargames/bandit/bandit6.html)

---

## What I Had to Do
I have to find password stored in inhere directory in which there are so many directories and in those directory one file which is *human-readable* and *1033 bytes in size* and *not executable*  contains the password to login onto bandit6.

---

## How I Did It

First i listed all directory in home directory using ls command where i find inhere directory.

In inhere directory i also use ls command to list what is inside there, there are so many directories named like **maybehere00** to **maybehere19** and all of this directories also contain so many files.

So i need to use the command **find** in order to search for the desired file using some option, for that i read the man page and find out about *-type* (to determine the file type) and *-size*(searching according the size c indicates bytes) option and run this command;
```bash
find -type f -size 1033c
```

It gives me only one file in **maybehere07** directory named **.file2** . indicates that it's a hidden file.

The more advanced command which filter more:
```bash
find . -type f -size 1033c -not -executable
```
In this command . represent that find in current directory which is inhere and -type for the type which is file and -size for the size of file and c used for bytes and -not -executable option cause the file is not executable.

So i run cat command to view the content of file from home directory:
```bash
cat maybehere07/.file2
```
Now i have the password to login onto bandit6 so just run this command and enter the password and you have successfully completed the challenge:
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

Learn and enjoy!

---

## What I Learned
- ``find command`` - use to search for files in the directory using multiple options.

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man find`` - to learn more about the find command
- ``man cat`` - to learn about cat command
