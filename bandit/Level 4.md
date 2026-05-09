
# Bandit 03 - 04

[Challenge](https://overthewire.org/wargames/bandit/bandit4.html)

---

## What I Had to Do
I have to find the password in a **hidden file** in *inhere* directory to login onto bandit4.

---

## How I Did It

First i list all the directories and files present in current home directory with ls:
```bash
bandit3@bandit:~$ ls
inhere
```

Then i have to change my working directory to inhere directory, for this i am using **cd** command:

**cd** - change directory 
```bash
cd inhere/
```
Here i am using **Relative Path** inhere/ cause inhere is already in the home directory.

Now i need to list all the files and directories in inhere command using ls:
```bash
ls
```
It doesn't show anything because the file is hidden.

So You have to use *-la* option with it in which l stands for **long listing** and a stands for **all (including hidden files)**:
```bash
ls -la
...Hiding-From-You
```
Now you have the file just use cat to view the password:
```bash
cat ...Hiding-From-You
```

Now you have the password just enter this command and then enter the password and you have successfully completed this challenge:
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

Learn and Enjoy!

---

## What I Learned
- ``cd command`` - use to change working directory
- ``Relative Path`` - Path that is relative to the current directory not starting from root directory.
- ``ls command`` - using -a option shows you all the file


---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man ls`` - to know more options of ls for sorting etc.
- ``man cd`` - to know about changing directory
