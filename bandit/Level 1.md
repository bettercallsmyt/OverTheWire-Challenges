
# Bandit 00 - 01

[Challenge](https://overthewire.org/wargames/bandit/bandit1.html)


## What I Had to Do
In this level, firstly you are already logged in bandit0 or say Level 0 and there's a password for the next level in a file called **readme** in the home directory.
You need to find that password and login to the bandit1 using SSH.

---

## How I Did It

First i need to find what is in the home directory (which is generally represented by this ~ sign in terminal), So i used the command:

**ls** - *which is short for listing, it list all the directories and files present in the current working directory* 
```bash
bandit0@bandit:~$ ls
readme
```

Then you need to see what is in the file, for this i am using the following command:

**cat** - *which is short for concatenate, and it's main task is to show/view the content of any file*

**Note** - *You can also use some other commands such as more or less, if file size is much bigger.*

```bash
cat readme
```

And in the file readme, you will see the password at the end to login in to the bandit1 using SSH on port 2220 and the same host as it is bandit.labs.overthewire.org

```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

Now you jsut need to enter the password you found in the readme file in bandit0 and then you are successfully login to bandit1.

Learn and Enjoy!

---

## What I Learned
- ``Listing Directory Contents`` - ls command let you see what is in the directory.
- ``Viewing File Contents`` - cat command let you see the content of files.


---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man ls`` - to see what are some options you can use for specific listing such as -l and many more.
- ``man cat`` - to know more about cat command, you can also create a file with cat using output redirector.
- ``man pwd`` - to know in what directory you're currently in, short for print working directory.
- ``man more or less`` - if you wanna learn some other commands to view the file.
