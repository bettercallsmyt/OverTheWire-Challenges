
# Bandit 04 - 05

[Challenge](https://overthewire.org/wargames/bandit/bandit5.html)

---

## What I Had to Do
I have to find the password in **inhere directory** in a *human-readable file* between many files in this directory.

---

## How I Did It

So first is listed content of home directory using ls:
```bash
bandit4@bandit:~$ ls
inhere
```
Then i change my current directory to inhere using cd command:
```bash
cd inhere/
```

Then i list the content of inhere :
```bash
ls 
```

And there are 10 files all named like *-file00*.

Now i have to find the **Human-Readable file** which is in the format of **ASCII Text** or **UTF-8** the most common ones.

So i run this command one by one for every file to see what type of file it is:
```bash
file ./-file00
```

This command is fair, if you don't have large number of files, but if you have to list all the file types in directory then you have to learn about **wildcards** :
```bash
file ./*
```
 **Asterisk( * )** - it means match everything

**Wildcards Examples** :
```bash
# * = match anything 
ls *.txt # all .txt files 
ls file* # anything starting with "file" 
ls *log* # anything with "log" anywhere in the name
```
So Now we have the *-file07* which is in **ASCII text** format which is human readable format so cat command will show you the password to login onto bandit5:
```bash
cat ./-file07
```

Now run this command to login to the bandit5:
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
```


Now just enter the password and you have successfully finished the challenge.

Learn and enjoy!

---

## What I Learned
- ``Human Readable File`` - File that are in plain text commonly used ASCII text or UTF-8 encoding.
- ``file command`` - used to know the type of file such as data,ASCII text, TXT files etc.
- ``Wildcards`` - special characters such as * , ?, [ ] used to specify searches.

---

## Password
`[REDACTED]`


---

## Helpful Reading Material
- ``man file`` - to know more about file command.
- [wildcards](https://www.warp.dev/terminus/linux-wildcards)- to know more about the wildcards and how to use them.
