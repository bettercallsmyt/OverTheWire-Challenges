
# Bandit 08 - 09

[Challenge](https://overthewire.org/wargames/bandit/bandit9.html)

---

## What I Had to Do
Need to find password in ``data.txt`` and the password is the only line that occurs only once in the file.

---

## How I Did It

First i use ``ls`` to list the content of directory, where i find ``data.txt`` in home directory and if you run ``cat`` command you get so many lines of passwords.

So we need to find the line that occurs only once and for that i use ``uniq`` command and run this command: 
```bash
cat data.txt | uniq -u
```
I don't know that ``uniq -u`` only works if the file have repeated lines adjacent to each other, i come to know about this after reading the ``man`` page for ``uniq``, so we need to first sort the file then run the ``uniq`` command on that.

So i used this command with ``|`` operator: 
```bash
sort data.txt | uniq -u
```
It does two things, first it sorts the data of file *data.txt* making repeated lines adjacent to each other and then ``uniq`` command with ``-u`` option print the line that occur only once.

But you can use this command too:
```bash
cat data.txt | sort | uniq -u
```
It performs the same function.

Now you have the password log in to the bandit9 using this command: 
```bash 
ssh bandit9@bandit.labs.overthewire.org -p 2220
```

Then enter the password and the level is successfully completed.

Learn and Enjoy!

---

## What I Learned
- ``sort`` - used to sort the file according your needs.
- ``uniq`` - to print repeated lines can be use with options

---

## Password
`[REDACTED]`
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

---

## Helpful Reading Material
- `man sort` - to learn more about sort command
- `man uniq` - to learn more options of uniq
- [Piping and Redirection](https://ryanstutorials.net/linuxtutorial/piping.php) - to learn about piping and redirection of input, output and error.