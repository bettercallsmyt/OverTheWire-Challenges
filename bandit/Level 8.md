
# Bandit 07 - 08

[Challenge](https://overthewire.org/wargames/bandit/bandit8.html)

---

## What I Had to Do
I have to find the password stored in a file ``data.txt`` which is a very large text file, password is next to the word millionth in the file.

---

## How I Did It

So first i listed all the content in home directory using ``ls`` finding ``data.txt`` file there and try to use cat command but terminal just blowing with lots of text so i have to stop the command via ``Ctrl+C``.

Then i run a command to search for the word *millionth* in the file using grep and | piping (pipe operator)
```bash
cat data.txt | grep millionth
```
 **|** - pipe operator it takes the output from one command and make it as input for the next command.

**grep** - this command is used to search for patterns in the file.

Now you have the password just run this command and enter the password and you have successfully logged in to bandit8.
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
```

Learn and Enjoy!

---

## What I Learned
- ``|`` - pipe operator and how to use it 
- ``grep`` - use to find patterns in the file

---

## Password
`[REDACTED]`
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

---

## Helpful Reading Material
- ``man grep`` - to learn more about grep command you can also watch a YouTube video on this one too.
- ``|`` - Learn how pipe operator works.
