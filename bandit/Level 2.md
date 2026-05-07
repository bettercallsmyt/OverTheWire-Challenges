
# Bandit 01 - 02

[Challenge](https://overthewire.org/wargames/bandit/bandit2.html)

---

## What I Had to Do
I need to login to the bandit2 after reading the password from a file which have name of dash - in the home directory.

---

## How I Did It
First i listed all the files and directories using the command ls :
```bash
bandit1@bandit:~$ ls
-
```

To view this file i tried some command such as: 
```bash
cat -
cat '-'
```

But it doesn't work, it stays in interactive mode for more input so i have to try something different.

So i use more command which i learnt from the book:
**more** - used to view the page of a file at a time and also lets you page down through it.

```bash
more -
```

And this works fine and i got the password, because `more` doesn't treat `-` as anything special. whereas ``cat`` treat this is as an option or say argument (special built in convention stdin).

The main fix i found on internet is:
```bash
cat ./-
```
To specify the relative path of the file, basically the path for the file so that cat command understand this as the path to go to and find the file in that directory.

And now you have the Password to login in to the bandit2, just run this command:
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

It then asks for the password, enter the password you find in the file called - and then you successfully login on to the bandit2.

Learn and Enjoy!

---

## What I Learned
- ``more`` - command used to view file in pages and scrolling via enter key.
- ``Using File Path`` - If name of file is something special such as - , then some commands can understand this as stdin or special built in convention.

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man more`` - to know more about the command more
- [File Paths in Linux](https://pressbooks.senecapolytechnic.ca/uli101/chapter/file-paths-in-linux/) - to understand *Relative* and *Absolute* Path.
