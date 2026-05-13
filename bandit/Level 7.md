
# Bandit 06 - 07

[Challenge](https://overthewire.org/wargames/bandit/bandit7.html)

---

## What I Had to Do
To find a password stored somewhere in the server with the properties such as:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

---

## How I Did It

First i listed all the directories present in home directory, there are no directories in it so i go to root (/) directory cause then i can search for the file in the whole server.

I started my search with find command like this:
```bash
find / -user bandit7 -group bandit6 -size 33c
```
But it gives me so many errors of permission denied and then i remember the method of using **redirectors** to discard the error in /dev/null file so i take help from internet and then run the command:

```bash
find / -user bandit7 -group bandit6 -size 33c 2> /dev/null
```

**2>** - redirects error into the file and we use /dev/null cause it discards everything.

Now you have the file which looks something like this:
```bash
./var/lib/dpkg/info/bandit7.password
```

Now just use cat command with this file path and then you have the password then run this command in your terminal:
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```

Now just enter the password and you have successfully logged in to the bandit7.

Learn and Enjoy!

---

## What I Learned
- ``Root directory`` - / represents a root directory and use find there to find a file.
- ``Discarding error message`` - use of redirectors such as > output redirector used with 2 which is a standard error **STDERR** number.
- ``Redirectors`` - Input, Output, Error redirectors and how to use them

---

## Password
`[REDACTED]`

---

## Helpful Reading Material
- ``man find`` - to learn more about find command
- [redirectors](https://www.geeksforgeeks.org/linux-unix/input-output-redirection-in-linux/) - Redirection of Input, Output and Error
